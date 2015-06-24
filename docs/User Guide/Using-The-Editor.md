# Using the Editor

## Basic Workflow

The Sandbox supports 2 main modes of operation - play and edit. 

### Editing
When you're in edit mode, you see all the usual GUI tools in the interface, and can interact with the world. This is the default mode for a world - when you create one, you'll be in this state.

Edit mode has a few special features - you can pause and play the entire simulation with the buttons in the bottom left of the screen. Clicking Play will cause the simulation to execute, and stop will cause it to reset. When the world is 'playing', the GUI is disabled. This gives you a quick way to test behaviors or interactivity. 

While in Edit mode, the server will keep backups of the world every few minutes.

### Playing 
When you are happy with the world (or game, or simulation....), you can 'publish' it. Publishing the world allows you some special options, like whether or not the system should generate avatars for each user, what camera the users should be assigned, and whether or not the users can see the editing tools.

Published worlds do not get saved - when the last user logs out, the world resets to the state it was in when it was published. 

Published worlds can be set to 'Single Player'. This means that when a user logs in, they are actually in a private copy of the simulation. This copy is not connected to the server - it neither saves its state, nor sends messages to the server about interactions. In some cases, this can result in significantly better performance for the end user, because server round trim latency is eliminated. 

### Testing

While in Edit mode, you should have an option on the file menu called "Test World" and one called "World Settings". In "World Settings", you have the same options as are available on the Publish page. Fill these out as you would when publishing the world. You can use the "Test World" command to get a real time view of exactly how the published world will behave. This feature will create a clone of your world on the server, set the publish settings, and launch it in a child window. The main window will be disabled. When the child window closes, the temporary world is delete off the server, and the main window is re-enabled. 

Usually, the play/pause feature of the editor should be enough to test, but you can use the above workflow to test aspects of your scene that play/pause cannot simulate - for instance, you might want to test code that responds to a users log in.

### Workflow
So, you'll go through these steps to create and share a world.

1. Create your world
1. Edit the world
1. Test the world
1. Publish the world

# Editor Camera Modes
NOTE: The current camera controls assume you have a standard three button mouse.
NOTE: These camera controls apply to the default editor camera only. Selecting one will activate the default camera.

###  Orbit Camera (Camera->Orbit)
Orbit mode allows you to rotate the camera around a fixed point in space. This is useful to examine an object from many angles, and is the default camera mode. When in this mode, click the right mouse button and drag within the 3D view to rotate. Push your middle mouse button (or mouse wheel) and drag to pan the view. This will move the center of rotation around the scene. Roll the mouse wheel to zoom in or out from the center.

###  First Person Camera (Camera->First Person)
The first person camera mode will orient the camera behind your avatar. When in this mode, the mouse will not affect the camera placement. You may move your avatar with the arrow keys or the W, A, S, D, Z, and C keys. The camera will follow accordingly.

###  Navigate Camera (Camera-> Navigate)
The Navigate camera mode is complex, but also powerful. It's best used to navigate around a large region of space. The right mouse button functions as it does in Orbit mode, rotating around a fixed point in space. The name 'Navigate' comes from the method of moving this center. Push down with the middle mouse button (or mouse wheel) and pull the camera toward the bottom of the screen. This will move the camera such that the point you clicked stays under the mouse pointer. If you click a point off on the horizon, pulling down will move you closer to that point. Likewise, you can click a point at your feet with the middle button, and push it toward the horizon. This moves you quickly back away from that point. Additionally, you can middle click a point and roll the mouse wheel. This moves the center of rotation to that exact point in space, and zooms into a fixed distance from that point. You can use this method to quickly frame a given point in space, even if that point is not the center of an object. If you simply want to focus on an object, you should select that object and use the 'Focus' button. This will center you and place the camera in Orbit mode.

###  Free Camera (Camera-> Free)
The free camera mode allows a sort of first person perspective, but not attached to your avatar. Click and drag with the left mouse button to turn the view. Use the mouse wheel to move forward or back. Push the middle button and drag to pan the view.

###  Focus (Camera->Focus Selected)
Move the camera such that it frames the selected object in the view. This will reset the camera mode to 'Orbit'.

### Fly(Camera->Fly)
The camera will move forward at a set speed. Right click and drag to turn, and roll the mouse wheel to change speed.

# Hotkeys
When in the editing mode:

* q - select object
* w - move
* e - rotate
* r - scale
* [shift] d - duplicate
* [delete] - delete

#Naming Objects
All objects in the world can be assigned a friendly name. These names appear in the GUI for all action, but need not be unique - they are just for your convenience. To name an object, select the object and open the Object Properties window. Under the 'Flags' heading, find the 'name' field. Type the name here. 

When you copy, duplicate, or paste an object, the name will be incremented automatically if it ends with a number.

The name is stored in the `DisplayName` property of an object. From script, all objects are indexed by name under `this.children_by_name`.