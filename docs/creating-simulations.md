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

### View Performance (FPS)

`Rendering` > `Toggle Stats` will place an overlay window in the top left corner showing the Frames per Second (FPS) of the simulation.  

### Change Simulation Settings

## Importing Assets

### FBX Import and Entity Library

## Simulation Authoring

### Script Editor

### The Tick Heartbeat

### Moving Objects using the Transfrom API

### Lights, Camera, Action!

### Working with a Team

## Searching for Objects

### Asset Server Filtering

### Finding Nodes through Script

## User Input

### Key Up, Key Down, and Mouse Movement

