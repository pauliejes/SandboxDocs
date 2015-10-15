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

The `tick()` method is called by the engine 20 times every second.  It is the heartbeat of the multiplayer simulation.  Each simulation object can define the `tick` method and this is typically where simulation logic originates.

# Simulation Object

# Transforms

# Physics

# Audio

# Events

# Variables and Methods

# Broadcast

Broadcast data to simulation objects that are within the given range and have the function_target defined.

```
this.broadcast(function_target, data, range);
```

# Raycasts

```
this.Scene.traceAPI.rayCast(origin, direction, options)
```

# Vector Functions

# Reference Guide

See the [Scripting API](reference_guide/scripting-api.md) for complete reference information.
