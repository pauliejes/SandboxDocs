<h1>Developer Guide</h1>

The VW Sandbox is based on a minimal Node.js server and a rich JavaScript client.

<h2>Contents</h2>
[TOC]

# Server Installation

The VW Sandbox server runs under [Node.js](https://nodejs.org/en/) ([v0.12.x](http://nodejs.org/dist/latest-v0.12.x/)), an open-source, cross-platform JavaScript runtime for developing server-side web applications.

1. Clone the VW Sandbox GitHub Repository

	```
	 git clone https://github.com/adlnet/Sandbox
	```

2. Assuming you've installed Node.js (v0.12.x), install the VW Sandbox in the app directory

	```
	npm install
	```

3. Run the server in the app directory

	```
	node app.js
	```

4. With the server running, point web browser to:

	```
	http://localhost:3000
	```

The server can be configured using either command line switches listed below and/or a json configuration file (see the [Configuration](#configuration) section).

## Command Line Switches

Switches and values should be seperated by spaces, and surrounded by quotes when the value contains a space.

* `-a <user>`   	- the username of the user who should be treated as the administrator. Default is 'admin'
* `-ap`				- set the default URL for the site
* `-cc`				- activates and specifies versioning??
* `-clean`    		- clean??
* `-config <file>	- point to a different JSON configuration file than the config.json in the app directory
* `-cluster`		- turns clustering on or off??
* `-compile` 		- the server will build the main RequireJS module. This takes a long time on startup, but reduces the number of requests the client will make by almost 50.
* `-d <directory>`  - the path to the data directory. The default is "./data"

!!! note:

	If the data directory, either specified or unspecified, doesn't exist, the Sandbox will attempt to create it.


* `-DB` 			- set the database driver??
* `-exit`			- quits the process after the build step
* `-l`				- the verbosity level of the console log
* `-ls`				- simulate a given number of milliseconds latency for each message to the reflector
* `-min`			- the server will minify using Uglyify.js. 
* `-nocache`		- the FileCache will not retain files in memory. Not much reason to disable this these days.
* `-p`				- the port to use. Default is 3000
* `-sp`				- the port to use when using SSL
* `-v`				- enable versioning. All requests will redirect to {host}/version/{url} with the version number in Version.js

!!! note:

	The -v option is helpful to ensure client caches are overridden when new versions are available.

So, possible production settings are as follows:

```
node app.js -p 80 -minify -compile -v
```

## JSON Config File

The server side application can also be configured by editing the `config.json` file in the root directory of the application. 

!!! note:

	Command line switches will override JSON configuration file values.  Also remember that you must restart the VW Sandbox server when making changes to the configuration file.

You should find a sample configuration file in the app directory that contains some useful information.  A copy of the sample configuration file is below.

!!! Warning:

	The comments below are not valid JSON and must be removed before using.

```
    "port": 3000, 								// the port to serve on
    "datapath": "c:/vwfData", 					// the database location
    "admin": "admin", 							// the username of the administrator
    "logLevel": 1, 								// the vebosity of the console output
    "build": false, 							// build the require js modules
    "minify": false, 							// minify javascript on serve
    "compile": false, 							// compile with the closure conpiler
    "version": 1,								// the version number to use for URL versioning. Must be an integer!
    "useVersioning": false,						// when true, the server will use a url prefix to identify the software version

    "hostAssets": true,							// when true, assets are hosted locally in the data directory
    "remoteAssetServerURL": null, 				// remote URL where the asset server is hosted if assets are not hosted locally
    "sessionSecret": null 						// enter a good random string here for security of sessions

    "_3DRAPI": null, 							// the endpoint to use to access the service. Null defaults to the public 3DR instance
    "_3DRAPIKey": null, 						// the api key to use for all requests. Null defaults to the public API key
    "_3DRUser": null, 							// username server identifies itself as. Null defaults to Anonymous
    "_3DRPassword": null, 						// password for the server user. Null defaults to Anonymous
    "_3DRUseAuth": false, 						// use anonymous access or not. Null defaults to anonymous.

    "sendEmails": false, 						// send emails to new users and on password reset (note, password reset is really not useful without this!) 
    "emailFrom": "", 							// the sender as it will appear in the emails to users
    "emailService": "", 						// the service provider for outgoing emails. See the nodemailer docs
    "emailPassword": "", 						// the service password for outgoing emails. See the nodemailer docs
    "emailUsername": "", 						// the service username for outgoing emails. See the nodemailer docs

    "lrsEndpoint": null,						// the xAPI Learning Record Store (LRS) endpoint
    "lrsUsername": "",							// the xAPI LRS username
    "lrsPassword": "",							// the xAPI LRS password

    "pfx": null, 								// the path and name of the PFX credential file. If not null, server will use HTTPS and WSS
    "pfxPassphrase": null, 						// the passphrase to open the pfx file
    "sslPort": 443, 							// the port to use for the secure server. Requests to the nonSSL port will redirect here

    "sslCA": ["./ca1.pem", "./ca2.pem"], 		// intermediate certificate authority

    "sessionKey": "virtual", 					// enter a good random string here for security of sessions
    "sessionSecret": "unsecure cookie secret", 	// enter a good random string here for security of sessions

    // use the the following settings to enable social media logins

    "facebook_app_id": null,
    "facebook_app_secret": null,
    "facebook_callback_url": "http://localhost:3000/adl/sandbox/auth/facebook/callback",
    "twitter_consumer_key": null,
    "twitter_consumer_secret": null,
    "twitter_callback_url": "http://localhost:3000/adl/sandbox/auth/twitter/callback",
    "google_client_id": null,
    "google_client_secret": null,
    "google_callback_url": "http://localhost:3000/adl/sandbox/auth/google/callback"
```


## Configure 3D Repository Integration

The VW Sandbox allows users to load 3D assets from an ADL 3D Repository instance. Out of the box (and on the hosted copy at [https://sandbox.adlnet.gov/](https://sandbox.adlnet.gov/), the server is configured to connect to a 3D Repository instance hosted by ADL at [http://3dr.adlnet.gov](http://3dr.adlnet.gov). However, as of version 0.4.11, this can be configured to use any 3DR installation. The VW Sandbox server now proxies traffic to and from the connected 3DR instance, so you don’t even necessarily need to make your 3DR publicly visible, so long as the VW Sandbox server can connect to it.  The 3DR integration features are implemented in `/support/server/3dr_proxy.js`.

The settings for connecting to the 3DR server are stored in the `config.json` file, located in the server application root directory.   See the [JSON Config File](#json-config-file) section.  Below are examples of some of the 3DR values:
 
1.  `_3DRAPI`
    *   Use this to configure the endpoint of the 3DR service
    *   Example: `"_3DRAPI":"https://3dr.adlnet.gov/api/rest/"`
2.  `_3DRAPIKey`
    *   Requests to the 3DR API must include a valid API key. You can create a new key under the Account page on your 3DR instance. The public key on the ADL 3DR site is the default, `00-00-00`
    *   Example: `"_3DRAPIKey":"00-00-00"`
3.  `_3DRUser`
    *   The user name to use when the VWS server connects to the 3DR. You can leave this blank, but in doing so, you will only be able to access publicly accessible models. When you input a 3DR username (usually an email address), the permissions of this user will control the access of anyone using the VWS server
    *   Example: `"_3DRUser":"robert.chadwick.ctr@adlnet.gov"`
4.  `_3DRPassword`
    *   The plain text password for the 3DR user. Because the server proxies the traffic, this password will not be visible to VWS users.
    *   Example: `"_3DRPassword":"Password1234_is_very_strong"`
5.  `_3DRUseAuth`
    *   When set to false, the system will ignore the `_3DRUser` and `_3DRPassword` settings. When true, these setting will be used.
    *   Example: `"_3DRUseAuth": true`

!!! note:
	
	The VW Sandbox Editor currently prevents users from loading models that do not have public access, even though, if requested, the server would actually be able to load them.


## Configure Asset Server Integration

The VW Sandbox includes the [Sandbox Asset Server](https://github.com/adlnet/SandboxAssetServer/), which provides a set of CRUD services to manage VW Sandbox assets.  The Sandbox Asset Server runs by default as a VW Sandbox node module where assets are hosted locally.  However, the Sandbox Asset Server can be run as a standalone server and where VW Sandbox assets are hosted remotely.  Remote hosting of assets is helpful when a team is working together on a collection of assets.

The settings for configuring the VW Sandbox asset server node module are stored in the JSON configuration file, located in the server application root directory.   See the [JSON Config File](#json-config-file) section.  Below are examples of some of the Sandbox Asset Server values:

    "hostAssets": true,				// when true, assets are hosted locally in the data directory
    "remoteAssetServerURL": null, 	// remote URL where the asset server is hosted if assets are not hosted locally
    "sessionSecret": null 			// enter a good random string here for security of sessions



# Architecture Overview

The VW Sandbox is composed of two major components: 1) the server side and 2) the client application.  The VW Sandbox can also be viewed by its [File Organization](#file-organization). 

## Server

The VW Sandbox server is a Node.js application that makes heavy use of Express. It's composed of several sub systems:

1. [Reflector](#reflector)
1. [File Server](#file-server)
1. [Services API](#services-api)
1. [Data Access Layer](#data-access-layer)
1. [Views](#views)

Session is currently handled with Express middleware, although this was not always the case. We are currently using Cookie-Session from [https://github.com/expressjs/cookie-session](https://github.com/expressjs/cookie-session).

### Reflector

The reflector is a portion of the system that synchronizes worlds. It's job is to accept messages from clients and send them to all participants in the world. This allows the simulation to only move forward when all clients receive the message. This system also keeps track of all the running worlds, and detects when all uses have left so a world can be shut down.  This the system is implemented in `reflector.js`. See [File Organization](#file-organization) for more info.

### File Server

The file server is a simple tool that responds to request for files by the client. Each file is GZipped and loaded into memory before being served. The File Server component is implemented in `filecache.js`. See [File Organization](#file-organization) for more info.

### Services API

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



## Client 
Most of the client-side application is implemented as either a view driver or a models driver, depending on whether or not it provides services that can be accessed by the runtime reasoning of the world.  Drivers are the part of the system that provide capabilities to nodes.  Model drivers participate in the simulation, and can actually change the state of the world synchronously. View drivers can only change the state of the world by sending messages to the reflector.

### Model Drivers
These modules actually affect the state of the running simulation. Together, they completely define the state of the world, and storing all their data represents a snapshot of the environment. 

#### AmmoJS
This is the physics driver. It is responsible for reading simulation state data and applying collision detection and Newtonian motion.

#### JavaScript
This driver does the actual execution of the code attached to VWF nodes through scripts. See [JavaScript Model Driver](drivers/Drivers/#javascript-model-driver).

#### JQueryUI
The actual driver does very little. Most GUI code is in the views.

#### Object
Last chance data storage for object property data.

#### Three.js Model Driver
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

#### Audio
This driver wraps up the [Buzz audio library (http://buzz.jaysalvat.com/)](http://buzz.jaysalvat.com/ "Buzz audio library"). It responds to method calls on nodes and creates sounds.

#### EditorView
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

