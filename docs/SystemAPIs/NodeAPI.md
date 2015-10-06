# Node API

The Node API provides properties and methods to manipulate a simulation object, which is a node in the simulation.  The Node API is the primary API for manipulating simulation objects and is accessible through the ScriptEditor by selecting an object and typing `this.`, which will show an autocomplete list of properties and methods.  In addition, each node provides access to the Transform, Physics, and Audio APIs.

## Properties

Any property that the node has defined will be availble.  In addition, some standard properties are provided.

### DisplayName

The name of the object that appears in the Properties panel in the Editor.

## Methods

Any method that the node has defined will be available.  In addition, some standard methods are provided.

### AudioAPI

Returns the node's [AudioAPI](http://sandboxdocs.readthedocs.org/en/latest/SystemAPI/AudioAPI/ "Audio API") endpoint.

**Arguments:**

*(None)*

**Returns:**

`audioAPI` (`AudioAPI`)

The [AudioAPI](http://sandboxdocs.readthedocs.org/en/latest/SystemAPI/AudioAPI/ "Audio API") endpoint.

### PhysicsAPI

Returns the node's [PhysicsAPI](http://sandboxdocs.readthedocs.org/en/latest/SystemAPI/PhysicsAPI/ "Physics API") endpoint.

**Arguments:**

*(None)*

**Returns:**

`physicsAPI` (`PhysicsAPI`)

The [PhysicsAPI](http://sandboxdocs.readthedocs.org/en/latest/SystemAPI/PhysicsAPI/ "Physics API") endpoint.

### TransformAPI

Returns the node's [TransformAPI](http://sandboxdocs.readthedocs.org/en/latest/SystemAPI/TransformAPI/ "Transform API") endpoint.

**Arguments:**

*(None)*

**Returns:**

`transformAPI` (`TransformAPI`)

The [TransformAPI](http://sandboxdocs.readthedocs.org/en/latest/SystemAPI/TransformAPI/ "Transform API") endpoint.

### Random

Return, preserving replicated computation, a random number between 0 (inclusive) and 1(exclusive).  Similar to `Math.random()`, but is safe for replicated computation.

**Arguments:**

*(None)*

**Returns:**

`randomNumber` (`Number`)

The generated random number between 0 and 1.
