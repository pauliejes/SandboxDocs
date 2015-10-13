<h1>Creating Simulations</h1>

A guide to create simulations using the VW Sandbox.

[TOC]

# Learning the Interface

## Using the Editor

### Editor Overview

The VW Sandbox Editor provides a collaborative authoring experience in a web browser.  

![](images/editor-interface.png)

At the bottom left of the screen is a play-pause-stop control panel that controls the state of the simulation.  By default, simulations load in the Editor in the stopped state.

Along the top of the interface is the toolbar and toolbar icons that enable a wide range of commands to be issued.

On the left side of the screen is a `Library` tab providing access to drag and drop re-usable content objects into the scene.

The scene itself is in the center of the screen.  A grid provides perspective within the scene.

On the right side of the screen is an `Editors` tab providing access to multiple editors that provide information about objects in the scene and commands to manipulate the objects and the scene itself.

When an object is selected, the Script Editor can be loaded at the bottom of the screen from the toolbar menu (Windows > Script Editor) or from the toolbar icons (![](images/script-editor-icon.png)) located three icons in from the right.

### Navigation, Selecting, and Moving Objects

By default, simulations are launched for editing in the Editor Camera.  The Editor Camera allows you to see and navigate the whole scene.  To navigate and manipulate objects using the Editor Camera, please review the keyboard and mouse commands below.

#### Navigation

* Hold the right mouse button and move your mouse to look around the scene.  
* Scroll the mouse wheel forward to zoom in and backward to zoom out.
* Hold the mouse wheel down to pan the view around.

!!! note

	To learn more about navigating using using different modes of the Editor Camera, take a look at [Camera Modes](camera-modes.md).

#### Selection

Click the left mouse button to select an object.  Go ahead and create an object to try it out.  Expand the `Library` tab on the left side of the screen.  Open the `Demo Entities` tab and drag the T90 Tank into the scene.  Select the tank by moving the cursor over the tank and clicking your left mouse button.  The tank should highlight in blue.

![Tank Selection](images/tank_selection.png)

Click the left mouse button again on a specific part of an already selected object to select that part.  To continue the example, with the tank already selected, click the mouse button over the turret of the tank.  The turret should highlight in green.

![Tank Selection](images/turret_selection.png)

To learn more about selecting objects in more advanced ways, check out the [Selecting Objects](../tutorials/Selecting-Objects.md) tutorial.

#### Moving Objects

[comment]: <> (embed a video demonstration follow by a try it now option.)



#### Toolbar and Hotkeys

![Logout Icon](images/toolbar_icons/leave_world.png) Logout (`File` > `Logout`)

Leave the current simulation.

![Move Icon](images/toolbar_icons/move.png) Move (`Edit` > `Transform` > `Move`)
Activate the move tool. This will place a 'gizmo' over the selected object. Click and drag on the colored lines to move the object in the direction of that line. Hold your mouse between lines to select the plane made from those two lines. Clicking and dragging while a plane handle is selected will move the object along the selected plane.

!!! note:

	The blue background highlight indicates the move tool is currently active.

![Rotate Icon](images/toolbar_icons/rotate.png) Rotate (`Edit` > `Transform` > `Rotate`) 
Activate the rotate tool. This will place a 'gizmo' over the selected object. Click the gizmo axis you want to rotate on and drag in a straight horizontal line in one direction to rotate one way and then in a straight horizontal line in the other direction to rotate away.

![rotate animation](videos/rotate.gif)

![Scale Icon](images/toolbar_icons/rotate.png) Scale (`Edit` > `Transform` > `Scale`)
Activate the Scale tool. This will place a 'gizmo' over the selected object. Click and drag the center box to scale uniformly on all axis. Click and drag on one of the colored boxes to scale only in the direction of the selected box. TIP: scaling always happens in local space - you cannot rotate an object, then scale in worldspace to produce a skew.

![World Coordinates Icon](images/toolbar_icons/world_coordinates.png) World Coordinates (`Edit` > `Transform` > `World Coords`)
Align the selected tool's gizmo with the world coordinate system. Thus, the X handle of the move gizmo will point toward the absolute X of the world, and Z will always be 'up', toward the sky. TIP: coordinate space selections currently do not work properly for objects that are children of other objects.

!!! note:

	The blue background highlight indicates the editor is actively using world coordinates.

![Local Coordinates Icon](images/toolbar_icons/local_coordinates.png) Local Coordinates (`Edit` > `Transform` > `Local Coords`)
Align the selected tool's gizmo with the selected object. Use this if you want to move an object toward its own 'front', even if that 'front' does not point strait along a world axis line because the object has been rotated. TIP: coordinate space selections currently do not work properly for objects that are children of other objects.

![Select by Clicking Icon](images/toolbar_icons/select_by_clicking.png) Select by Clicking (`Edit` > `Select` > `Pick`)
When this mode is activated, clicking on an object will select it for editing. The object selection is used by all tools and windows to display properties. This button will light up blue when in `Select` mode. TIP: if you find that you are clicking and not selecting the object you wish, check the status bar at the bottom of the screen. If you see 'Pick: None' in the 4th box, you are not in select mode. 

![Select None Icon](images/toolbar_icons/select_none.png) Select None (`Edit` > `Select` > `Select None`)
Unselect the selected object, and exit select mode. Note that clicking the button will change the select mode to none, and you will have to click the 'Select By Clicking' button to enter selection mode again.

![Select Parent Icon](images/toolbar_icons/select_parent.png) Select Parent (Hierarchy->Select Parent)
When a node is selected, clicking this button will select the node's parent, if the node has one.

![Focus Camera Icon](images/toolbar_icons/focus_to_selected_object.png) Focus (Camera->Focus Selected)
Move the camera such that it frames the selected object in the view. This will reset the camera mode to 'Orbit'. TODO: make sure the Orbit icon lights as selected when this is clicked.

![Copy Icon](images/toolbar_icons/copy.png) Copy (Edit->Copy)
Copy the selected node to be pasted later. You must have a node selected for this operation. When copying, the entire hierarchy of the selected object will be copied as well. If the bounding box that marks the selection is red, you have selected a node that controls a part of a model that was loaded by and asset file (most likely from the 3DR). These objects cannot be copied.

![Paste Icon](images/toolbar_icons/paste.png) Paste (Edit->Paste)
Paste the copied node into the scene. This will make a new node with all the properties of the copied node. You will be assigned as the new nodes owner. This new node will be placed at the center of your view, at z=0. Note that when looking at the world at very shallow angles, this may place the object farther away then you expect.

![Duplicate Icon](images/toolbar_icons/duplicate.png) Duplicate (Edit->Duplicate)
A shortcut for copy, then paste. The only notable difference is that the new node will be placed exactly on top of the original.

![Delete](images/toolbar_icons/delete.png) Delete (`Edit` > `Delete`)
Deletes the currently selected object.

![Link Icon](images/toolbar_icons/link.png) Link (`Hierarchy` > `Link`)
This tool allows you to make one object a child of another. You must be the owner of both objects to complete this operation. You must first select an object before clicking this tool. When activated, the cursor will change to a cross hair, and allow you to pick a second object. When you choose the second object, the selected object will be added as a child of the object you pick.

![Unlink Icon](images/toolbar_icons/unlink.png) Unlink (`Hierarchy` > `Unlink`)
This button will unlink the selected object from its parent. The selected object must be a child of another object in the scene.

![Orbit Camera Icon](images/toolbar_icons/orbit_camera.png) Orbit Camera (`Camera` > `Default Cameras` > `Orbit`)
Activate 'Camera Orbit' mode. See the Camera Modes section for details on how the camera controls work.

!!! note:

	The blue background highlight indicates the editor is actively using the `Orbit` camera mode, which is the default camera mode for the editor.

![First Person Camera Icon](images/toolbar_icons/first_person_camera.png) First Person Camera (`Camera` > `Default Cameras` > `Avatar View`)
Activate 'First Person' mode. See the Camera Modes section for details on how the camera controls work.

![Navigate Camera Icon](images/toolbar_icons/navigation_camera.png) Navigate Camera (`Camera` > `Default Cameras` > `Navigate`)
Activate 'Navigate' mode. See the Camera Modes section for details on how the camera controls work.

![Fly Camera Icon](images/toolbar_icons/free_camera.png) Free Camera (`Camera` > `Default Cameras` > `Fly`)
Activate 'Free Camera' mode. See the Camera Modes section for details on how the camera controls work.

![Create Sphere Icon](images/toolbar_icons/sphere.png) Create Sphere (`Create` > `Primitives` > `Sphere`)
Create a new sphere object at the center of the view. See the Primitive Objects sections for information on the object settings.

![Create Box Icon](images/toolbar_icons/box.png) Create Box (`Create` > `Primitives` > `Box`)
Create a new box object at the center of the view. See the Primitive Objects sections for information on the object settings.

![Create Cylinder Icon](images/toolbar_icons/cylinder.png) Create Cylinder (`Create` > `Primitives` > `Cylinder`)
Create a new Cylinder object at the center of the view. See the Primitive Objects sections for information on the object settings.

![Create Cone Icon](images/toolbar_icons/cone.png) Create Cone (`Create` > `Primitives` > `Cone`)
Create a new cone object at the center of the view. See the Primitive Objects sections for information on the object settings.

![Create Plane Icon](images/toolbar_icons/plane.png) Create Plane (`Create` > `Primitives` > `Plane`)
Create a new plane object at the center of the view. See the Primitive Objects sections for information on the object settings.

![Script Editor Icon](images/toolbar_icons/script_editor.png) Script Editor Window (`Windows` > `Script Editor`)
Show the Script Editor window. You should have an object selected when opening this window. See Tool Windows for more information.

![Chat Icon](images/toolbar_icons/chat.png) Chat Window (`Windows` > `Chat`)
Show the Chat window. See Tool Windows for more information.

![Asset Library Icon](images/toolbar_icons/model_library.png) Asset Library Window (`Windows` > `Models`)
Show the Asset Library window. See Tool Windows for more information.

**Hotkeys**

These are some hotkeys that are helpful to remember when using the VW Sandbox Editor.  While in the editing mode the following hotkeys are available:

* `q` - select object
* `w` - move
* `e` - rotate
* `r` - scale
* `[shift] d` - duplicate
* `[delete]` - delete

### Organizing, Accessing, and Relating Objects



## Editing and Playing

You'll typically go through these steps to create and share a simulation.

1. Create the simulation
1. Edit the simulation
1. Test the simulation
1. Publish the simulation

### Edit

When you're in **edit** mode, you see and can use the Editor tools and interact with the world. The edit mode is the default mode for a world -- when you create a new simulation, you'll be in the edit mode.

!!! note:

	When you are in edit mode, the server will keep backups of the world every few minutes.

### Play, Pause, and Stop

You can **play** the simulation by clicking the play button in the lower left side of the Editor.  When the Editor is in play mode, the Editor tools are disabled.  You can a**pause** the simulation, which is sometimes helpful to activate the tools to for example change camera angles or inspect items without stopping the simulation.  When you click **stop** the simulation will reset and you will again be able to use the Editor tools.

### View Performance

Performance of a simulation is usually based on the interaction of CPU and GPU resources and simulation complexity.  As you work on your simulation, you can check the Frames Per Second (FPS) of the user experience on the current machine by navigating to the `Rendering` > `Toggle Stats` menu item, which will toggle an overlay window in the top left corner showing the Frames per Second (FPS) of the simulation on and off.

![Toggle Stats](images/toggle_stats.png)

Toggling the Stats on will result in an overlay window in the upper left hand corner of the simulation that shows the current FPS, the range of observed FPS values, and a graph showing the observed FPS values over time.

![60 FPS Overlay Window](images/60_fps.png)

### Publish

**Publishing** a simulation involves changing the `Settings` on the simulated world's landing page.  Settings such as whether the Editor tools should be shown or what camera users should be in upon login are commonly set to "publish" a world.  See the [Change Simulation Settings](#change-simulation-settings) section for other options that can be set when the owner of a world is ready to make it ready for other users.

### Test

Typically, **testing** is done in the simulated world using the play, pause, and stop controls.  However, it can sometimes be difficult to iteratively change the settings of a world for publish, determining that something needs to be changed, and then changing the settings again to edit, and returning to edit.  

To mitigate this difficulty, a **Test Publish** mode is available.  While in **edit** mode, you should see an option under the `File` menu called `World Settings`.  In `World Settings`, you have the same options as are available on the world settings page. Fill these out as you would when publishing the world. You can use the "Test Publish" mode to get a real time view of exactly how the published world will behave. This feature will create a clone of your world on the server, set the publish settings, and launch it in a child window. The main window will be disabled. When the child window closes, the temporary world is delete off the server, and the main window is re-enabled.

Again, usually the play/pause feature of the editor should be enough to test, but you can use the above workflow to test aspects of your scene that play/pause cannot simulate -- for instance, you might want to test code that responds to a users log in action.

### Management

You can manage a simulated world you create by going to the landing page for the world.  The landing page contains the Launch button.

![World Management Buttons](images/world-management.png)

In addition to the Launch button, are other world management buttons.  World management options include restoring past versions, deleting the world, duplicating it, and embedding it as an IFrame on other websites.

### Change Simulation Settings

The Settings page provides options to control the configuration of the simulated world to allow it to serve as a virtual world that persists state changes or a game that resets when closed.

![World Settings Buttons](images/world-settings.png)

!!! note "Note:"
    World Settings are only provided to owners of simulated worlds.

If you would like the world to function as a virtual world, select options to persist world state on close and create an avatar for each user.

If you would like the world to function as a simulation or game, deselect options to persist world state and avatar creation.  You may also want to select the option to limit the simulation to single player if you want to limit multiplayer behavior.

Independent of the kind of simulation, choices for who can access the simulation and what users will see when they login are provided.  Anonymous users can be allowed or not allowed to join.  Owners can make simulations into more published forms by not showing the editor tools and choosing a specific camera for users (e.g., a chase camera).

!!! note "Note:"
    If you want to choose a camera other than the default Editor Camera for users to use, you must create the camera.  See the  [Creating Cameras](graphics.md#creating-cameras) section for more information.

## Importing 3D Models and Textures

You can import 3D models and textures using the asset server, which is accessible via the `Assets` menu item.  

Uploading your 3D models as COLLADA is the easiest approach. If you have the COLLADA model hosted remotely, you can simply go to `Asset` > `Load Mesh by URL` and choose `Collada`. 

!!! note:

	The server that hosts the file must implement CORS and have no authentication requirements.

 Alternatively, you can upload the COLLADA model to the asset server and then load it into the Editor.  Assuming you are logged in, below are the steps:

1.  `Asset` > `Create New Asset` > `From File`
1.  Give the asset a name
1.  Click `Create Asset` to upload the .dae
1.  Click `Upload`
1.  Drag and drop the model from the `Content Libraries` > `My Models`

!!! note:

	We also support uploading glTF models, but while this is a better performance route, it is also more complicated.  For more information on using glTF models, see [Using glTF 3D Models](graphics.md#using-gltf-3d-models) in the Graphics section.

You can add a **texture** to an object by selecting the object and viewing the Material Editor.  Expand the Texture Layer and click on the image to choose a new image.

See [Audio](audio.md) for information about uploading audio assets.

## Simulation Authoring

All objects in the world can be assigned a friendly name. These names appear in the GUI for all action, but need not be unique - they are just for your convenience. To name an object, select the object and open the Object Properties window. Under the 'Flags' heading, find the 'name' field. Type the name here. 

![Property Name](../images/properties-name.png)

When you copy, duplicate, or paste an object, the name will be incremented automatically if it ends with a number.

The name is stored in the `DisplayName` property of an object. From script, all objects are indexed by name under `this.children_by_name`.

### Script Editor

![Script Editor](images/script_editor.png)

Code you write with the ScriptEditor is immediately injected into the multiplayer engine as new properties, methods, and events for the selected object.  You can see which selected object the ScriptEditor is focused on in the blue title window at the top and in the status bar at the bottom.  In the screenshot, the ScriptEditor is focused on `sphere1`.

The ScriptEditor has three tabs across the top: `Methods`, `Events`, and `Properties`.  Depending on which tab is selected, the list of items will be displayed vertically on the left and the code for the given selected item is in the main content window on the right.  In the screen shot above, the `Methods` tab is selected and the `tick` method is selected.

!!! note:

	The editor uses js_beautify on all input code before displaying it. On some systems, the JavaScript engine may insert "use strict."  This is normal and not a problem. 

The two up and down arrow buttons in the upper right hand corner of the script editor expand the ScriptEditor window (up) and minimize/hide the ScriptEditor window (down).

![ScriptEditor Window Size Controls](images/script_editor_window_size_buttons.png)

### The Tick Heartbeat

The `tick()` function is called by the engine 20 times every second.  It is the heartbeat of the multiplayer simulation.  Each simulation object can define the `tick` method and this is typically where simulation logic originates.

### Moving Objects using Transforms

Every simulation object has a Scripting API accessible to it via the `this` object.  To move an object, you can add logic to the `tick` method to change the current position of the object.  You will want to use `this.transformAPI.setPosition(x,y,z)` to move the object.

### Lights, Camera, Action!

To create a new light, go to `Create` > `Lights` and choose the desired type of light (Point, Spot, or Directional).  See [Lighting](graphics.md#lighting) for more information or the tutorial on [Lighting and Materials](tutorials/lighting-and-materials.md).

To create a new camera, go to `Create` > `Camara` > `Perspective`.  See [Creating Cameras](graphics.md#creating-cameras).

### Working with a Team

## Searching for Objects

### Asset Server Filtering

### Finding Nodes through Script

## User Input

### Key Up, Key Down, and Mouse Movement

