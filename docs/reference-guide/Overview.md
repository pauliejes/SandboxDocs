# Overview

The VW Sandbox provides multiple APIs that are accessible through the Script Editor to define and manipulate simulation logic.

The [Node API](NodeAPI.md "Node API") provides properties and methods to manipulate a simulation object, which is a node in the replicated computation model.  The Node API is the primary API for manipulating simulation objects and is accessible through the Script Editor by selecting an object and typing `this.`, which will result in an autocomplete list of available properties and methods.  

![Autocomplete](images/autocomplete.png)

The autocomplete list should include any properties and methods the object defines as well as access to the Transform, Physics, and Audio APIs.

The [Transform API](TransformAPI.md "Transform API") provides methods to manipulate the properties of nodes such as their position and rotation.  It also includes methods to convert between different coordinate systems. 

The [Physics API](PhysicsAPI.md "Physics API") provides methods to apply forces and velocities to objects.

The [Audio API](AudioAPI.md "Audio API") provides properties and methods to control sound logic.