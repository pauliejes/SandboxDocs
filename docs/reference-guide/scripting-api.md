<h1>Scripting API</h1>

!!! Warning:
	Your simulation logic should be limited to the use of the Scripting API and simple logic for its use.

	You should not write any asynchronous JavaScript in the ScriptEditor -- no callbacks.  You should not be talking to an external server (e.g., AJAX), manipulating the DOM, or spawning WebWorkers.  If you find yourself needing to do these things in your simulation, you might be ready to author your own engine driver.  See the [Architecture](../architecture.md) section and how to extend it.

[TOC]

# AudioAPI Reference

The Audio API provides properties and methods to control sound logic.


## Properties

Property             		| Type        | Brief Description
-------------------- 		| ----------- | ------------------------------
[end range](#end-range)     | Number      | The end of the audio range.
[id](#id)            		| String      | The name to identify the sound.
[looping](#looping)         | String      | Indicates whether or not the sound is to loop/repeat.
[playing](#playing)        	| Boolean     | Indicates whether or not the sound is currently in use. 
[position](#position)      	| Number      | Where the sound can be found.
[sound](#sound)            	| String      | The file of the sound.
[start range](#start-range) | Number      | The start of the audio range.
[volume](#volume)           | Number      | How loud the sound should play. 


### end range
Type: `Number`  
some number for the end

### id
Type: `String`  
The name to identify the sound

### looping
Type: `Boolean`  
Indicates whether or not the sound is to loop/repeat

### playing
Type: `Boolean`  
Indicates whether or not the sound is currently in use 

### position
Type: `Number`  
Where the sound can be found

### sound
Type: `String` `filename`  
The file of the sound

### start range
Type: `Number`  
some number for the start

### volume
Type: `Number`  
How loud 


## Methods

Method             									| Return Type | Brief Description
---------------------------------------				| ----------- | ------------------------------
[calledMethod(id, name, params)](#calledmethodid-name-params)| void	      | 
[deletedNode(id)](#deletednodeid)      				| void	      | Deletes the specified sound source node.
[Initialize()](#initialize)      					| void	      | Start it up.
[loop()](#loop)      								| void	      | Sets the `boolean` looping variable.
[pause()](#pause)      								| void	      | Halts playback of sound, holding position along track to resume where left off.
[play()](#play)      								| void	      | Plays sound.
[playSound(url, loop, volume)](#playsoundurl-loop-volume)		| void	      | Lets GUI elements play sounds.
[stop()](#stop)      								| void	      | Ends playback of sound, resets position.
[updateSourcePosition()](#updatesourceposition)		| void	      | Get the position of the source object. 
[updateVolume(camerapos)](#updatevolumecamerapos)   | void	      | HTML can't actually play it louder, however we can make it 'carry' farther by using the inverse and adjusting the range parameters of the falloff curve.
[unloop()](#unloop)      							| void	      | Sets the `boolean` looping variable.

### calledMethod(id, name, params)

This is a good place to explain.

**Arguments:**

`id` (`String`)  
The identification String.

`name` (`String`)  
The name of the command:

* `playSound`

	If the scene played the sound, it has no position and just plays at full volume. Nodes that are not the scene use their position to adjust the volume.

* `pauseSound`
* `stopSound`
* `deleteSound`

!!! note:
	Only delete sound if you are sure the sound will not play again any time soon

`params` (`Array`)  
Array of additional parameters

**Returns**
*(Nothing)*


### deletedNode(id)
Deletes the specified sound source node.

**Arguments:**
`id` (`String`)  
The String identifier of the node deleted.

**Returns:**
*(Nothing)*


### Initialize()
start it up

**Arguments:**
*(None)*

**Returns:**
*(Nothing)*



### loop()
Sets the `boolean` looping variable.

**Arguments:**
*(None)*

**Returns:**
*(Nothing)*



### pause()
Halts playback of sound, holding position along track to resume where left off.

**Arguments:**
*(None)*

**Returns:**
*(Nothing)*


### play()
Plays sound.

**Arguments:**
*(None)*

**Returns:**
*(Nothing)*


### playSound(url, loop, volume)

Lets GUI elements play sounds.

**Arguments:**

`url` (`String`)  
String specifying the URL.

`loop` (`Boolean`)  
Boolean indicating if the sound should be looped.

`volume` (`number`)  
How loud.

**Returns:**

*(Nothing)*

### stop()
Ends playback of sound, resets position.

**Arguments:**
*(None)*

**Returns:**
*(Nothing)*

### unloop()
Sets the `boolean` looping variable.

**Arguments:**
*(None)*

**Returns:**
*(Nothing)*

### updateSourcePosition

Get the position of the source object. 

!!! note:
	The 3D driver keeps track of the position.

**Arguments:**
*(None)*

**Returns:**
*(Nothing)*

### updateVolume(camerapos)

HTML can't actually play it louder, however we can make it 'carry' farther by using the inverse and adjusting the range parameters of the falloff curve.

**Arguments**
`camerapos` (`number`)  
Location of camera.

**Returns**
*(Nothing)*




### ticked()
Update the sound volume based on the position of the camera and the position of the object

**Arguments:**
*(None)*

**Returns:**
*(Nothing)*


# ClientAPI Reference

## Methods


### getUserNameForConnectionID(id)

Talk more about that.

**Arguments:**

`id` (`String`)  
String unique to each user.

**Returns:**

`name` (`String`)  
The user's name.


### getConnectionIDForUserName(name)

Discuss the various ins and outs.

**Arguments:**

`name` (`String`)  
The user's name.

**Returns:**

`id` (`String`)  
String unique to each user.


### getAvatarForUserName(name)

What's in a name?

**Arguments:**

`name` (`String`)  
The user's name.

**Returns:**

`avatar` (`node`)  
The user's 3D avatar. 


### focus(cid, nodeID)

Focus.

**Arguments:**

`cid` (`String`)  
The client's unique identification string.

`nodeID` (`String`)  
The node's unique identification string.

**Returns:**

*(Nothing)*


### getCameraIDForClient(id)

Give me that thingamajig, so I can take a picture.

**Arguments:**

`id` (`String`)  
The client's unique identification string.

**Returns:**

`cameraID` (`String`)  
The camera's unique identification string.


### getCameraForClient(id)

Now that we've got the camera, we are out of here!

**Arguments:**

`id` (`String`)  
The client's unique identification string.

**Returns:**

`camera` (`node`)  
The first person camera for the user.


# CommsAPI Reference

The communications properties and methods are used to chat, call, etc.

## Methods


### PM(from_client_id, to_client_id)

Yeah, I don't know what that is. Private Messaging??

**Arguments:**

`from_client_id` (`String`)  
Sending client's identification string.

`to_client_id` (`String`)  
Receiving client's identification string.

**Returns:**

*(Nothing)*


### Chat()

Opens a chat window.

**Arguments:**

*(None)*

**Returns:**

*(Nothing)*


### VideoCall(from_client_id, to_client_id)

Establishes video call between two users.

**Arguments:**

`from_client_id` (`String`)  
Sending client's identification string.

`to_client_id` (`String`)  
Receiving client's identification string.

**Returns:**

*(Nothing)*


### VoiceCall(from_client_id, to_client_id)

Establishes voice call between two users.

**Arguments:**

`from_client_id` (`String`)  
Sending client's identification string.

`to_client_id` (`String`)  
Receiving client's identification string.

**Returns:**

*(Nothing)*

# Scene Reference

The `Scene` provides properties and methods accessible to all simulation objects.

## Properties

### SimTime

Returns the number of ticks that have been processed.

### traceAPI

Returns the Scene's [traceAPI](#traceAPI) endpoint.

## Methods

### findNode(displayName)

Search the `Scene` for the provided simulation object displayName

**Arguments:**

displayName: the DisplayName of the simulation object to be found

**Returns:**

`foundObject` (`object`)

The simulation object matching the provided displayName or null if no matching object is found.

### findNodeByID

Search the `Scene` for the provided simulation object ID.

**Arguments:**

ID: the ID of the simulation object to be found

**Returns:**

`foundObject` (`object`)

The simulation object matching the provided ID or null if no matching object is found.


# PhysicsAPI Reference

The Physics API provides methods to apply forces and velocities to objects.


## Methods


### addForceAtCenter(x, y, z, coords)

Applies force at center of node. Accepts X, Y, Z, and Coordinates.

**Arguments:**

`x` (`number`)  
Force applied along x-axis.

`y` (`number`)  
Force applied along y-axis.

`z` (`number`)  
Force applied along z-axis.

`coords` (`number`) (optional)  
Coordinates where force is to be applied.

**Returns:**

*(Nothing)*


### addForceImpulse(x, y, z, coords)

Accepts X, Y, Z, and Coordinates.

**Arguments:**

`x` (`number`)  
Force applied along x-axis.

`y` (`number`)  
Force applied along y-axis.

`z` (`number`)  
Force applied along z-axis.

`coords` (`number`) (optional)  
Coordinates where force is to be applied.

**Returns:**

*(Nothing)*


### addTorqueImpulse(x, y, z, coords)

Accepts X, Y, Z, and Coordinates.

**Arguments:**

`x` (`number`)  
Torque applied along x-axis.

`y` (`number`)  
Torque applied along y-axis.

`z` (`number`)  
Torque applied along z-axis.

`coords` (`number`) (optional)  
Coordinates where torque is to be applied.

**Returns:**

*(Nothing)*


### addTorque(x, y, z, coords)

Accepts X, Y, Z, and Coordinates.

**Arguments:**

`x` (`number`)  
Torque applied along x-axis.

`y` (`number`)  
Torque applied along y-axis.

`z` (`number`)  
Torque applied along z-axis.

`coords` (`number`) (optional)  
Coordinates where torque is to be applied.

**Returns:**

*(Nothing)*


### addForceOffset(x, y, z, x1, y1, z1, coords)

Accepts X, Y, Z, X1, Y1, Z1 and Coordinates.

**Arguments:**

`x` (`number`)  
Force applied along x-axis.

`y` (`number`)  
Force applied along y-axis.

`z` (`number`)  
Force applied along z-axis.

`x1` (`number`)  
Force applied along second x-axis.

`y1` (`number`)  
Force applied along second y-axis.

`z1` (`number`)  
Force applied along second z-axis.

`coords` (`number`) (optional)  
Coordinates where force is to be applied.

**Returns:**

*(Nothing)*


### setLinearVelocity(x, y, z, coords)

Sets the linear velocity. Accepts X, Y, Z, and Coordinates.

**Arguments:**

`x` (`number`)  
Velocity applied along x-axis.

`y` (`number`)  
Velocity applied along y-axis.

`z` (`number`)  
Velocity applied along z-axis.

`coords` (`number`) (optional)  
Origin coordinates of linear velocity.

**Returns:**

*(Nothing)*


### setAngularVelocity(x, y, z, coords)

Sets the angular velocity. Accepts X, Y, Z, and Coordinates.

**Arguments:**

`x` (`number`)  
Velocity applied along x-axis.

`y` (`number`)  
Velocity applied along y-axis.

`z` (`number`)  
Velocity applied along z-axis.

`coords` (`number`) (optional)  
Coordinates where angular velocity is to be applied.

**Returns:**

*(Nothing)*


### getLinearVelocity()

Returns the current internal Linear Velocity value.

**Arguments:**

*(None)*

**Returns:**

`linearVelocity` (`number`)  
Current internal linear velocity value.


### getAngularVelocity()

Returns the current internal Angular Velocity value.

**Arguments:**

*(None)*  

**Returns:**

`angularVelocity` (`number`)  
Current internal angular velocity value.



# Simulation Object Reference

Each [Simulation Object](#simulation-object) provides properties and methods to manipulate the simulation object.  

## Properties

Any property that the node has defined will be availble.  In addition, some standard properties are provided.

### children

### children_by_name

### DisplayName

The name of the object that appears in the Properties panel in the Editor.

### EditorData

## Methods

Any method that the node has defined will be available.  In addition, some standard methods are provided.

### AudioAPI

Returns the simulation object's [AudioAPI](#audioapi) endpoint.

**Arguments:**

*(None)*

**Returns:**

`audioAPI` (object)

The [AudioAPI](#audioapi) endpoint.

### Bind

### Broadcast

### Client

Returns the socket identifier (GUID) of the person who sent the message that is being processed.  On tick() it is null.  A button's onClick() this.client is the person who clicked the button.

Related to the ClientAPI.  ClientAPI can resolve name of user of client given socket id.

### Moniker

Your socket identifier (GUID).

### PhysicsAPI

Returns the simulation object's [PhysicsAPI](#physicsapi) endpoint.

**Arguments:**

*(None)*

**Returns:**

`physicsAPI` (`object`)

The [PhysicsAPI](#physics) endpoint.

### TransformAPI

Returns the simulation object's [TransformAPI](#transformAPI) endpoint.

**Arguments:**

*(None)*

**Returns:**

`transforms` (`object`)

The [TransformAPI](#transformAPI) endpoint.

### Random

Return, preserving replicated computation, a random number between 0 (inclusive) and 1 (exclusive).  Similar to JavaScript's `Math.random()`, but is safe for replicated computation.

**Arguments:**

*(None)*

**Returns:**

`randomNumber` (`Number`)

The generated random number between 0 and 1.

### Time

Returns the current simulation time stamp.  Duration since the server started the simulation.






# traceAPI Reference

## Methods

### frustCast(origin, direction, options)

**Arguments:**

`origin` (``)  


`direction` (``)  


`options` (``)  

**Returns:**

*()*

### rayCast(origin, direction, options)

**Arguments:**

`origin` (``)  


`direction` (``)  


`options` (``)  

**Returns:**

*()*

### sphereCast(origin, direction, options)

**Arguments:**

`origin` (``)  


`direction` (``)  


`options` (``)  

**Returns:**

*()*

# TransformAPI Reference

Facilitates manipulation of objects by allowing manipulation of their properties such as position, and rotation.

Facilitates movement, rotation, and more of simulation objects.


## Methods

### move(x, y, z, coordinateSystem)

Moves a node

**Arguments:**

`x` (`number`)  
Movement along the x-axis in meters.

`y` (`number`)  
Movement along the y-axis in meters.

`z` (`number`)  
Movement along the z-axis in meters.

`coordinateSystem` (`String`)  
Specify either 'global' or 'local' coordinate system.

**Returns:**

*(Nothing)*


### getPosition()

Return a node's local position?

**Arguments:**

*(None)*

**Returns:**

`localPosition` (`Array of numbers`)  
Array containing local x, y, and z coordinates.


### getWorldPosition()

Return a node's global position.

**Arguments:**

*(None)*

**Returns:**

`globalPosition` (`Array of numbers`)  
Array containing global x, y, and z coordinates.


### localToGlobal(x, y, z)

Exchanges local x, y, and z coordinates for global x, y, and z coordinates.

**Arguments:**

`x` (`number`)  
Movement along the x-axis in meters.

`y` (`number`)  
Movement along the y-axis in meters.

`z` (`number`)  
Movement along the z-axis in meters.

**Returns:**

`vector` (`Array of numbers`)  
Array containing global x, y, and z coordinates.


### localToGlobalRotation(x, y, z)

Converts local values of rotation to global values of rotation.

**Arguments:**

`x` (`number`)  
Movement around the x-axis in meters.

`y` (`number`)  
Movement around the y-axis in meters.

`z` (`number`)  
Movement around the z-axis in meters.

**Returns:**

`vector` (`Array of numbers`)  
Array containing global x, y and z values of rotation.


### globalToLocal(x, y, z)

Exchanges global x, y, and z coordinates for local x, y, and z coordinates.

**Arguments:**

`x` (`number`)  
Position along the x-axis.

`y` (`number`)  
Position along the y-axis.

`z` (`number`)  
Position along the z-axis.

**Returns:**

`vector` (`Array[x coordinate, y coordinate, z coordinate]`)  
Array containing local x, y, and z coordinates.


### globalToLocalRotation(x, y, z)

Converts local values of rotation to global values of rotation.

**Arguments:**

`x` (`number`)  
Movement around the x-axis in meters.

`y` (`number`)  
Movement around the y-axis in meters.

`z` (`number`)  
Movement around the z-axis in meters.

**Returns:**

`vector` (`Array[x coordinate, y coordinate, z coordinate]`)  
Array containing global x, y and z values of rotation.


### globalRotationToLocalRotation(x, y, z)

Converts global rotation values to local rotation values.

`x` (`number`)  
Movement around the x-axis in meters.

`y` (`number`)  
Movement around the y-axis in meters.

`z` (`number`)  
Movement around the z-axis in meters.

**Returns:**

`vector` (`Array[x coordinate, y coordinate, z coordinate]`)  
Array containing local x, y and z values of rotation.


### setPosition(x, y, z)

Accepts X, Y, and Z coordinates to establish a new position.

**Arguments:**

`x` (`number`)  
Position along the x-axis.

`y` (`number`)  
Position along the y-axis.

`z` (`number`)  
Position along the z-axis.

**Returns:**

*(Nothing)*


### rotate(x, y, z, coordinateSystem)

Accepts X, Y, Z and Coordinate System and rotates.

**Arguments:**

`x` (`number`)  
Angle of movement around the x-axis.

`y` (`number`)  
Angle of movement around the y-axis.

`z` (`number`)  
Angle of movement around the z-axis.

**Returns:**

*(Nothing)*


### rotateX(angle, coordinateSystem)

Rotates the node around the x-axis.

**Arguments:**

`angle` (`number`)  
Angle of movement around the x-axis.

`coordinateSystem` (`String`)
Designates whether local, global, or parent coordinates are given.

**Returns:**

*(Nothing)*


### rotateY(angle, coordinateSystem)

Rotates the node around the y-axis.

**Arguments:**

`angle` (`number`)  
Angle of movement around the y-axis.

`coordinateSystem` (`String`)
Designates whether local, global, or parent coordinates are given.

**Returns:**

*(Nothing)*


### rotateZ(angle, coordinateSystem)

Rotates the node around the z-axis.

**Arguments:**

`angle` (`number`)  
Angle of movement around the z-axis.

`coordinateSystem` (`String`)
Designates whether local, global, or parent coordinates are given.

**Returns:**

*(Nothing)*


Coordinates:
	Local
	Global
	Parent



### rotateAroundAxis(angle, axis, coordinateSystem)

Accepts Angle, Axis, and Coordinate System and rotates node around given axis.

**Arguments:**

`angle` (`number`)  
The angle for rotation.

`axis` (`Array of numbers`)
Designates which axis for rotation.

`coordinateSystem` (`String`)
Designates which coordinate system is given (Local, global, or parent).

**Returns:**

*(Nothing)*


### getRotation()

By some form of magic, returns a number representing the rotation

**Arguments:**

*(None)*

**Returns:**

`euler` (`Array of numbers`)  
Angles of rotation around x, y and z axes.


### setRotation(x, y, z)

Sets the rotation of a node given specified angles.

**Arguments:**

`x` (`number`)  
Angle of rotation around the x-axis.

`y` (`number`)  
Angle of rotation around the y-axis.

`z` (`number`)  
Angle of rotation around the z-axis.

**Returns:**

*(Nothing)*


### getScale()

Returns the magnitude of the node.

**Arguments:**

*(None)*

**Returns:**

`vector` (`Array of numbers`)  
Array of x, y, and z vectors.


### setScale(x, y, z)

Accepts X, Y, and Z to set the scale of a node.

**Arguments:**

`x` (`number`)  
Scale of the x-axis.

`y` (`number`)  
Scale of the y-axis.

`z` (`number`)  
Scale of the z-axis.

**Returns:**

*(Nothing)*


### scaleMatrix(x, y, z, mat)

Accepts X, Y, Z, and Matrix.

**Arguments:**

`x` (`number`)  
Scale of the x-axis.

`y` (`number`)  
Scale of the y-axis.

`z` (`number`)  
Scale of the z-axis.

`mat` (`Array of numbers`)  
Current matrix of the node.

**Returns:**

`matrix` (`Array of numbers`)  
Updated matrix of the node being scaled.


### lookAt(t, clamp, axis, up, fromOffset)

Facilitates examination of a node.

**Arguments:**

`t` (`String`)  
Identification string of the target being looked at.

`clamp` (`String`)  
Axis held steady while examining the node.

`axis` (`String`)  
Designates the axis. More needed. Default value is 'Y'.

`up` (`String`)  
I'm really not sure.

`fromOffset` (`number`)  
Value of the offset of the node.

**Returns:**

*(Nothing)*
