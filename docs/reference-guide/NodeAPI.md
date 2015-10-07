# Node API

The Node API provides properties and methods to manipulate a simulation object, which is a node in the replicated computation model.  The Node API is the primary API for manipulating simulation objects and is accessible through the Script Editor by selecting an object and typing `this.`, which will result in an autocomplete list of available properties and methods.  The autocomplete list should include any properties and methods the object defines as well as access to the Transform, Physics, and Audio APIs.

## Properties

Any property that the node has defined will be availble.  In addition, some standard properties are provided.

### DisplayName

The name of the object that appears in the Properties panel in the Editor.

## Methods

Any method that the node has defined will be available.  In addition, some standard methods are provided.

### AudioAPI

Returns the node's [AudioAPI](AudioAPI "Audio API") endpoint.

**Arguments:**

*(None)*

**Returns:**

`audioAPI` (`AudioAPI`)

The [AudioAPI](AudioAPI "Audio API") endpoint.

### PhysicsAPI

Returns the node's [PhysicsAPI](PhysicsAPI "Physics API") endpoint.

**Arguments:**

*(None)*

**Returns:**

`physicsAPI` (`PhysicsAPI`)

The [PhysicsAPI](PhysicsAPI "Physics API") endpoint.

### TransformAPI

Returns the node's [TransformAPI](TransformAPI "Transform API") endpoint.

**Arguments:**

*(None)*

**Returns:**

`transformAPI` (`TransformAPI`)

The [TransformAPI](TransformAPI "Transform API") endpoint.

### Random

Return, preserving replicated computation, a random number between 0 (inclusive) and 1 (exclusive).  Similar to JavaScript's `Math.random()`, but is safe for replicated computation.

**Arguments:**

*(None)*

**Returns:**

`randomNumber` (`Number`)

The generated random number between 0 and 1.
