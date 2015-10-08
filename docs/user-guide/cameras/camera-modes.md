# Camera Modes

This documentation refers to the various interaction modes for the Editor Camera. This information is not relevant to cameras with are entities within a scene.

!!! note "Note:"
    The current camera controls assume you have a standard three button mouse.

!!! note "Note:"
	These camera controls apply to the default Editor Camera only. Selecting one will activate the default camera.

<a id='mode1'></a>
## Orbit

This is the default mode. The camera orbits around an imaginary point in space. The camera can swing around this point while facing it, or move toward or away from the point. The point itself can be translated to different locations in the scene.

### Interactivity
* right click and drag to orbit
* middle click and drag to pan (move the focus point)
* mouse wheel to zoom in or out
* hold shift and move the mouse to orbit
* use the arrow keys to orbit
* hold shift and use the up and down keys to zoom
* hold space and use the arrow keys to pan
* touch and drag on a touchscreen to orbit
* pinch a touchscreen to zomm
* Two-finger touch and drag to pan

<a id='mode2'></a>
## First/Thrid Person

This mode is only available when the scene is generating avatars for users. The camera can transition between first and third person modes by rolling the mousewheel. When this mode is active, certain mouse motions will control the avatar. 

###Interactivity in Third Person mode
* right click and drag to orbit around the avatar
* roll the mouse wheel to zoom. When you are close enough, you will enter First Person mode
* use the arrow keys or WASD to move the avatar

###Interactivity in First Person mode
* right click and drag to turn your viewpoint
* roll the mousewheel to exit back to Third Person mode
* use the arrow keys or WASD to contol the character

## Navigate Mode

This mode allows you to zoom to a very specifc point in space easily. It is related to Orbit mode in that it exposes the same functionality, with some additional features. 

###Interactivity
* all the same interactivity from the Orbit mode, plus:
* middle click and drag to zoom in or out from the point of interest
* middle click to animate the center point to a location in the scene. This uses a polygon accurate mouse intersection test
* tap space to set the center point (same as middle click)

## Free Mode

This mode is a first person style controller, but not tied to the avatar. 

### Interactivity
* right click and drag to turn the viewpoint
* roll the mouse wheel to move forward. You can move forward forever
* middle click and drag to pan
* use the arrow keys to turn the viewpoint
* use space and the arrow keys to pan
* use ctrl and the up or down button to move forward or back

## Device Orientation

This mode will attempt to use the sensors in your phone or tablet to position the viewpoint. This will have no effect on a desktop computer

### Interactivity
* physically move your tablet around space to change the viewpoint.

## Fly

A first person control mode that is always moving forward.

### Interactivity
* right click and drag to turn
* roll the mouse wheel to accelerate or decelerate