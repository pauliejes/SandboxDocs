<h1>Architecture</h1>

A guide to understand the VW Sandbox architecture.

[TOC]

This architecture guide will provide information on the server, editor, engine, and drivers.  However, one powerful way to extend the VW Sandbox without knowing too much about or changing the architecture is to write custom graphics.

# Writing Custom Graphics

Most simulation development involves manipulating existing Graphic types (e.g., 3D models, primitive shapes, particle systems).  Sometimes simulation developers will need to create custom Graphic types that directly interface with THREE.js (e.g., ocean, orthographic camera, advanced particle system, custom animation, custom shaders).  

At its core, writing a custom graphic type involves defining a node definition.  As an example of writing a custom graphic, consider making a custom sphere graphic type.

Node definition

```
extends: custom_sphere.vwf
source: custom_sphere.js

```

Where `extends: custom_sphere.vwf` is the engine's node interface (not implementation) defining its properties and methods.  `source: custom_sphere.js` is a JavaScript file that implements the interface.

Learn more by going through the [Custom Graphic Tutorial]().

# Architecture Overview

The VW Sandbox is a system composed of a node.js server-side JavaScript application and a client-side JavaScript application providing collaborative authoring of cloud-based multiplayer and singleplayer simulations.  The Server-Side JavaScript manages user and simulation data, exchanges messages between simulation clients, and provides a web server and a Web Service API.  The client-side JavaScript provides an editor and an engine for single and multiplayer simulations made up of drivers.  The engine provides drivers for Scripting, Transforms, Graphics, Physics, User Interfaces, and Audio.  The Scripting driver provides the Scripting API enabling simulation developers to use the engine's drivers. 

## Server-Side JavaScript

The Server-Side JavaScript manages user and simulation data, exchanges messages between simulation clients, provides a web server and a Web Service API, and delivers the client-side JavaScript.  The 

The VW Sandbox server is a Node.js application that makes heavy use of Express. It's composed of several sub systems:

1. [Reflector](#reflector)
1. [File Server](#file-server)
1. [Web Service API](#web-service-api)
1. [Data Access Layer](#data-access-layer)
1. [Views](#views)

Session is currently handled with Express middleware, although this was not always the case. We are currently using Cookie-Session from [https://github.com/expressjs/cookie-session](https://github.com/expressjs/cookie-session).

### Reflector

The reflector is a portion of the system that synchronizes worlds. It's job is to accept messages from clients and send them to all participants in the world. This allows the simulation to only move forward when all clients receive the message. This system also keeps track of all the running worlds, and detects when all uses have left so a world can be shut down.  This the system is implemented in `reflector.js`. See [File Organization](#file-organization) for more info.

### File Server

The file server is a simple tool that responds to request for files by the client. Each file is GZipped and loaded into memory before being served. The File Server component is implemented in `filecache.js`. See [File Organization](#file-organization) for more info.

### Web Service API

The web front end uses many services on the server to manipulate worlds and users. This system includes the endpoints for CRUD operations on worlds and users, as well as upload of files, thumbnails, and a few other odds and ends. The Express routes send any request that includes `/vwfdatamanager.svc/` to this system. It's implemented in `sandboxAPI.js`. See [File Organization](#file-organization) for more info.

### Data Access Layer

The DAL interacts with the database to perform CRUD operation as requested by the Services API. It does not do any validation or verification, as it assumes that the front end has handled this. It does wrap several asyncronous steps into simple calls. It handles all storage. Currently, we write blobs to the filesystem and store metadata about worlds, users, and inventory in [NeDB](https://github.com/louischatriot/nedb).  The actual database interaction is implemented in `DB_nedb.js`. You can replace this to access a different DB.  Below is the current layout of data written to the file system.

```
  /data
     /DataFiles
        /Models
        /Textures
        /Sounds
     /Logs
     /Profiles
     /States
     /Textures
     /Thumbnails
```

#### /data/Datafiles
All files and sub-folders from here are simply served by the file server as `vwfdatamanager.svc/datafile/...` where `...` is the path to the file. You can place anything here you need for your own servers scenes, like models or textures

#### /data/Logs
This folder will fill over time with log traces from the server and from each running world.

#### /data/Profiles
Each user will have a folder here, and inventory asset blobs will be saved in it. Actual user profiles are stored in the DB, not as filesystem blobs.

#### /data/States
Each world will have a folder here, named with the UUID of the world. The `state` file in this folder is the current JSON for the world. You can manually edit the world data in this file, if you choose. Each backup is stored here as well. Note that if you move the database or create or delete these files manually, you may have references in the DB to binary data that is not on the disk.

#### /data/Textures
This subdirectory will be served to the client as part of the 'Map Browser' component. All files and directories will be indexed and downloadable. Files in this directory are assumed to be images.

#### /data/Thumbnails
This directory should mirror the Textures directory, with the same files and the same folders. However, each file in this directory should be a thumbnail of its pair in the /textures/ directory.


### Views
We use Hogan and Mustache to template the view files. These render all the front end GUI like the login page, the home page, and all the create/delete world logic.



## Client-Side JavaScript

The client-side JavaScript application provides an editor and an engine for single and multiplayer simulations made up of drivers.  The engine provides drivers for Scripting, Transforms, Graphics, Physics, User Interfaces, and Audio.  The Scripting driver provides the Scripting API enabling simulation developers to use the engine's drivers. 

The Engine is the web application that the system sends to users web browsers.

Most of the client-side application is implemented as either a view driver or a models driver, depending on whether or not it provides services that can be accessed by the runtime reasoning of the world.  Drivers are the part of the system that provide capabilities to nodes.  Model drivers participate in the simulation, and can actually change the state of the world synchronously. View drivers can only change the state of the world by sending messages to the reflector.

## Synchronizing Properties

The engine tracks the changing values of object properties during the simulation.  These values are what gets saved when you save the environment.  The engine needs to be instructed about what values in your objects should be tracked.  When you define properties in the script editor, these values are automatically registered with the engine.  Additionally, all of the editor tools already properly register their values.  When you write a custom object, it is up to you to inform the engine what information needs to be tracked.  The engine contains methods to register your custom values.

### Engine

wire protocol.  The wire protocol is the JSON representation of commands to the engine.

When issue console commands into the engine, this is the API.

This is what the script engine compiles scripts into for engine execution.

engine.application() returns the identifier for the root node .  This.scene.id.

node ids for all methods.

Engine functions

callmethod
getproperty
setproperty
createproperty
createchild
deletechild
deletemethod
createmethod
createevent
deleteevent
fireevent
getstate
setstate
tick

### Model Drivers
These modules actually affect the state of the running simulation. Together, they completely define the state of the world, and storing all their data represents a snapshot of the environment. 

#### Physics Driver
This is the physics driver. It is responsible for reading simulation state data and applying collision detection and Newtonian motion.

#### Scripting Driver
This driver does the actual execution of the code attached to nodes through scripts. See [JavaScript Model Driver](drivers/Drivers/#javascript-model-driver).

#### GUI Driver
The actual driver does very little. Most GUI code is in the views.

#### Object
Last chance data storage for object property data.

#### Graphics Model Driver
The ThreeJS model driver loads all asset files, and is one of the more complex parts of the system. Its responsible for interpreting information from nodes and creating the graphic representation.  

##### SubDrivers

In order to make our code more modular, graphics engine functions are divided into sub-components we call subdrivers. Most of the real workload of the THREE.js driver is creating the sub drivers and sending messages into them. Subdrivers can inherit other subdrivers, and can also be specified by a user node definition. This last option allows a node to load custom graphics code into the simulation at runtime, even from another domain.  Below are a list of VW Sandbox SubDrivers:

###### Asset SubDriver
An entity in the simulation that loads a resource file, like a 3D model

###### MaterialDef SubDriver
Manages materials

1. Diffuse Color
1. Emission Color
1. Specular Reflections

###### Modifier SubDriver
Allow for transformation of parent geometry

1. Bend
1. Twist
1. Taper

###### ParticleSystem SubDriver
Implements particle systems

1. Smoke
1. Fire
1. Dust

###### Prim SubDriver
Master class for all primitive objects. Implements the modifier stack.

1. Sphere
1. Box
1. Cylinder

######  Spline SubDriver
Implements a 2D shape as a list of points

###### Terrain SubDriver
Implements the [Terrain](tutorials/working-with-terrain.md "Terrain") system

###### Transformable SubDriver
Manages setting and getting the position / orientation / scale of objects


**Other Subdrivers**

1. *Visible* - hides or shows objects
1. All modifiers and prims have their own, like `sphere.js` or `bend.js`
1. *Selectable* - enables/disables raycast functionality for an object. 
[comment]: <> (See [Scene Manager]())
1. *Static* - set objects as static or dynamic. 
[comment]: <> (See [Scene Manager]())

**Custom Subdrivers**

Nodes may request that they be associated with a subdriver via the `source` field of their node definition. 

```
    extends: "node3.vwf.yaml",
    type: "subDriver/threejs"
    source: "url to driver code"
```

A subdriver should implement the model driver API, and additionally expose a `getRoot` method that returns a three.js object. They may inherit the properties of other subdrivers by specifying an `inherit` property.

The format of a subdriver file should be a function that return a new function, which when called returns an object which implements the above described interface. The function returned by the `SubDriver` file is the `SubDriverFactory` for the given subdriver type. `SetProperty` and `callMethod` are examples of calls passed to this driver, and all the associated functions in the drivers it inherits. The inheritance is accomplished by merging together the JavaScript objects of the entire inheritance tree of subdriver. 

```
(function(){ //boilerplate
		function text(childID, childSource, childName)  //the actual driver code
		{
			this.text = "hi";
			this.inherits = ['vwf/model/threejs/prim.js']; // other subdrivers to be merged into this
			this.setProperty ...
                        this.calledMethod ...
			this.getRoot = function()
			{
				return this.rootnode;
			}
			this.rootnode = new THREE.Object3D(); //all subdrivers must have a GetRoot function
		}
		//default factory code
        return function(childID, childSource, childName) {  //the factory function
			//name of the node constructor
            return new text(childID, childSource, childName); //returns a new subdriver
        }
})();
```



### View Drivers
View drivers do all the work in the system that is not available to applications. These modules may only interact with the application state by sending messages to the reflector. The internal state of these modules is not considered part of the replicated application data.

#### Audio Driver
This driver wraps up the [Buzz audio library (http://buzz.jaysalvat.com/)](http://buzz.jaysalvat.com/ "Buzz audio library"). It responds to method calls on nodes and creates sounds.

#### Editor Driver
This is the main entrypoint for the entire suite of editing tools.

The entire editing interface is implemented as a single large [View driver](#view-drivers). This driver is located in `/support/client/lib/vwf/views/Editorview/`.  See [File Organization](#file-organization).

The EditorView is mostly a shell that loads up several modules as required. This depends on the metadata about the state which is retrieved from the Service API at world load. 

The modules loaded by the EditorView to provide functionality are either Managers or Editors (though there is currently little difference between these). Generally, Editors expose more of a UI, and Managers are used by other modules for services. Most editors and managers are loaded into global variables with the file name prefixed with an underscore. For instance, the Editor component is implemented in `Editor.js` and is available at runtime as `window._Editor`. 

**Major components**

1. UndoManager
1. MaterialEditor
1. PrimitiveEditor
1. ScriptEditor
1. SelectionEditor
1. InventoryManager
1. _3DRIntegration
1. Mapbrowser
1. Publisher
1. UserManager
1. DataManager
1. PhysicsEditor

<!--
## How To ...
1. [Add a new menu item](Add a new menu item)
1. [Add a new editor in the side panel](Add a new editor in the side panel)
1. [Add a new camera mode](Add a new camera mode)
1. [Show or hide GUI components](Show or hide GUI components)
-->

#### JQueryUI
This driver created JQueryUI objects to track the changing state of UI nodes, and hooks up all the UI functionality so the nodes properly represent the UI state.

#### ThreeJS
This is the graphics engine view component. It does the actual render, and is responsible for non-stateful UI bits like selection rectangles, highlights, and camera previews.

The THREE.js View Driver manages all the rendering of the scene. It also includes the code for dealing with user input events and sending them over the VWF socket. 

This component is also responsible for displaying the inset selected camera view, and for rendering the object selection lines.

This driver is responsible for manipulating the graphics engine objects. Much of the actual functionality has been moved into the subdrivers, but some remains for historical reasons. 

#### xAPI
This module creates the interaction with the [ExperienceAPI (http://www.adlnet.gov/tla/experience-api/)](http://www.adlnet.gov/capabilities/tla/experience-api.html "XAPI - Experience API") to provide performance tracking capabilities.

#### webRTC
Provides the hookups for the Video chat function.



## File Organization

This page details how files are organized in the repo.

```
  /Sandbox
     /data
     /support
        /client
           /lib
              /vwf
                 /views
                   /Editorview
                 /models
                   /threejs
        /server
        /proxy
          /vwf.example.com
     /public
        /ADL
          /Sandbox
            /views
            /examples
            /skys
            /textures
            /terrain
```      
### /Support/Server/
The server files for the NodeJS application

### /support/client/proxy/
The VWF uses this location to store object definition files for the common object types. Here you'll find many of the YAML files for root object types like node3.vwf.yaml and scene.vwf.yaml. A few of these have been extended in Sandbox.

### /public/adl/Sandbox
This is the root directory of the client side application. Here is the index.vwf.yaml that defines the scene, and object definitions that are specific to the Sandbox, like Prim.vwf.yaml and Asset.vwf.yaml. There are also some default textures and assets that are part of the system, like the texture for the home grid. Resources that are used in the examples live here as well. 

### /public/adl/Sandbox/examples
This directory holds all the example scenes you find when you access the /examples/ page. Each example directory must start with 'example_'. 

### /public/adl/Sandbox/skys
The skyboxes. Notice how each is names with the BK,UP,DN,FR,RT or FL suffix. 

### /public/adl/Sandbox/textures
Not to be confused with the textures that are available through the API and are stored with the data

### /public/adl/Sandbox/terrain
Just some example assets

### /data
This is where all the data that is specific to a given install lives (by default. Can be overridden by the config file) See [Data Organization](Data-Organization)

### /support/client/lib
This is where libraries required by the client side application live. Most of the system lives under /vwf/

### /support/client/lib/vwf/
The VWF system, and the associated boot files. The application is bootstrapped from here, and most of the client side app is in these subfolders

### /support/client/lib/vwf/views
This is where all the vwf view code lives. Many of the Sandbox features are implemented as vwf views. 

### /support/client/lib/vwf/views/EditorView
This is location of all the editor interface elements, as well as a few other bits of logic. The Editorview is responsible for creating all the widgets you normally see on the screen.

### /support/client/lib/vwf/models
The VWF model drivers. All the services that are provided to a running application are implemented as model drivers.

### /support/client/lib/vwf/models/threejs
The threejs model driver contains a lot of functionality, and is modularized into subdrivers. Files in this directory are loaded as required to provide threejs related services.



