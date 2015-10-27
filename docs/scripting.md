<h1>Scripting</h1>

The Scripting guide will explain how to use the ScriptEditor for writing simulation logic.

[TOC]

# ScriptEditor

![Script Editor](images/script_editor.png)

Code you write with the ScriptEditor is immediately injected into the multiplayer engine as new properties, methods, and events for the selected object.  You can see which selected object the ScriptEditor is focused on in the blue title window at the top and in the status bar at the bottom.  In the screenshot, the ScriptEditor is focused on `sphere1`.

The ScriptEditor has three tabs across the top: `Methods`, `Events`, and `Properties`.  Depending on which tab is selected, the list of items will be displayed vertically on the left and the code for the given selected item is in the main content window on the right.  In the screen shot above, the `Methods` tab is selected and the `tick` method is selected.

!!! note:

	The editor uses js_beautify on all input code before displaying it. On some systems, the JavaScript engine may insert "use strict."  This is normal and not a problem. 

The two up and down arrow buttons in the upper right hand corner of the script editor expand the ScriptEditor window (up) and minimize/hide the ScriptEditor window (down).

![ScriptEditor Window Size Controls](images/script_editor_window_size_buttons.png)

# Tick Function

Simulations play in a synchronized manner where the engine moves each simulation client forward by 1/20th of a second, which is known as a "tick."  The engine will call the tick() method of each object every 1/20th of a second.  This length of time is equal to 50 milliseconds or .05 seconds.  The tick is the heartbeat of the simulation.  Each simulation object can define the `tick` method and this is typically where simulation logic originates.

# Simulation Object

Each simulation object in a Scene can be scripted using the ScriptEditor to add simulation logic.  To do so, select the object (either directly or through the Hierarchy) and click on the ScriptEditor (toolbar ![Script Editor Icon](images/toolbar_icons/script_editor.png) or through the `Windows` > `Script Editor` menu item).

When the Script Editor loads, it will be focused on the selected object.  Scripting simulation logic usually starts with creating a [tick()](#tick-function) function, which is called by the engine to move the simulation forward.  In the image below, we've moved the selected tank object (named T-1) forward by .01 meters every tick (.05 seconds), which is a rate of .2 meters / second.

![Example Moving Object Forward](/images/scripting-simulation-object.png)

Each simulation object provides access to properties and methods that you define on the simulation object and as well as engine provided properties and methods through the `this` keyword.  If you create a new property to keep track of fuel consumption, you can reference that property in your script.  The Scripting API provides access, and APIs for physics, transforms, audio, and communications.  For example, in the image above, `this.transformAPI` provides access to methods that transform simulation objects.  See the [Reference Guide](reference-guide/scripting-api.md#simulation-object-reference) for more information.

## User Defined Properties, Methods, and Events

### Events

You can write your own event handlers for events that the engine fires.  Events the engine fires include:

* `pointerClick` - When mouse buttons are pressed and released.
* `pointerDown` - When mouse buttons are pressed.
* `pointerMove` - Each movement of a mouse over an object.
* `pointerOut` - When mouse moves off of an object.
* `pointerOver` - When mouse moves over an object.
* `pointerUp` - When mouse buttons are released.
* `pointerWheel` - When the mouse wheel is turned.

### Variables and Methods

You can write your own properties and methods.  These properties and methods will be able to be called by simulation objects.

## Engine Provided Properties, Methods, and Events

### Scene

The engine provides access to the Scene object by calling `this.Scene`.  Common methods the Scene provides include finding and accessing other objects.  See [Finding Objects through Script](creating-simulations.md#finding-objects through-script) for more information.

### Transforms

The engine provides the TransformAPI to get and set the position, rotation, and scale of simulation objects.  The TransformAPI also provides methods to convert between local and global coordinate systems.

See the [TransformAPI Reference](reference-guide/scripting-api.md#transformapi-reference) for more information.    

### Physics

The engine provides the PhysicsAPI to add, get, and set forces, velocities, and torques for simulation objects.

See the [PhysicsAPI Reference](reference-guide/scripting-api.md#physicsapi-reference) for more information.

### Audio

The engine provides the AudioAPI to play, pause, stop, and delete audio files.

As an example, consider the scenario where we want a boat to play a motor running sound clip when the user drives the boat.

```javascript

function tick()
{
    if (this._keysDown.indexOf("W") !== -1)
    {
    	var sound = Engine.callMethod(this.id, "getSound", ["/sas/assets/c253157d"]);

	    if (sound == null || !sound.isPlaying())
	    {
	        this.audioAPI.playSound("/sas/assets/c253157d", false, 100);
	    }
	}	
}
```

In line 3, we check to see if the user is pressing down the W key.  If the user is pressing the W key, then we get a reference to the sound file by its asset server identifier (`/sas/assets/c253157d`).  In line 7, we check to see if the sound is not yet defined or playing.  In line 9, we call the AudioAPI's `playSound` method passing the asset server identifer, a boolean value indicating if we want the audio file to loop (false in this case), and  


See the [AudioAPI Reference](reference-guide/scripting-api.md#audioapi-reference) for more information.

### Broadcasting Messages to other Objects

You will sometimes find the need to send information from one object to other objects based on proximity using a publisher subscriber model.  The engine provides the broadcast method where a publisher object can broadcast data (an array) to other subscriber objects that are within a given range.

As an example, consider the scenario where we want a user to drive a boat and have other boats within a certain range to navigate to a point in front of the user-driven boat.  In the user-driven boat, you could add a broadcast method.

```javascript
var leader_projection = this.transformAPI.localToGlobal(-150, 0, 0);

this.broadcast("facLeaderInput", [leader_projection], 500);
```

In the broadcast above, Line 1 uses the TransformAPI to get a position, in world coordinates, that is 150 meters in front of the user driven boat and it stores this position as `leader_projection`.  Line 3 then uses the broadcast method to send the leader_projection data as the only value in the data array to any subscriber objects within 500 meters that define the `facLeaderInput` method.

Then, in a subscriber object, we could define the `facLeaderInput` method to store the position as a candidate position to guide the subscriber object's movement.

```javascript
function facLeaderInput(args)
{
    this.facLeaderMovementCandidate = args;
}
```

### Raycasting Invisible Rays

```javascript
this.Scene.traceAPI.rayCast(origin, direction, options)
```

### Vector Functions

The engine provides common vector functions that are necessary to calculate distances or directions.  The `MATH` library 

# Reference Guide

See the [Scripting API](reference-guide/scripting-api.md) for complete reference information.
