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

# Face Reference

In a [FaceIntersect](#faceintersect-reference), the face is an object representing the polygon of the mesh that was intersected.

Name 		| Type 			| Description
----------- | --------- 	| --------------------
area		| Number 		| The face area
norm 		| Array[3] 		| The face normal
v0 			| Array[3]		| A vert
v1 			| Array[3] 		| A vert
v2 			| Array[3] 		| A vert

See [FaceIntersect](#faceintersect-reference).

# FaceIntersect Reference

An object representing the intersection of a ray or sphere cast with a simulation object.

Name 		| Type 				| Description
----------- | --------- 		| --------------------
distance	| Number 			| Distance in meters between the intersection and the origin of the cast.
face 		| [Face](#face-reference) | An object representing the intersecting mesh polygon.
node 		| [Simulation Object](#simulation-object-reference) | The Simulation Object that the ray intersected.
norm 		| Array[3] 			| A vector (x, y, z) representing the normal of the intersection.
object 		| THREE.Mesh 		| The three.js graphics object of the intersection. 
point 		| Array[3] 			| The point of the intersection, in world space.

See the [traceAPI's](#traceapi-reference) [rayCast(origin, direction, options)](#raycastorigin-direction-options) and [sphereCast(origin, radius, options)](#spherecastorigin-radius-options) methods, which return [FaceIntersect](#faceintersect-reference) objects.


# PhysicsAPI Reference

The Physics API provides methods to apply forces, torques, and velocities to objects.


## Methods

!!! note:
	The VW Sandbox physics methods implement Bullet Physics.  Please refer to the Bullet Physics manual for more information.

!!! note:
	All methods that take a vector X, Y, Z as an argument, can take individual X, Y, Z values or an Array[3] as the first argument as a convenience.


Method 																| Return Type 	| Brief Description
------------------------------------------------------------------- | -------------	| -----------------
[addForceAtCenter(x, y, z)](addforceatcenterx-y-z)					| void			| Applies a force at the center of mass of the object.
[addForceImpulse(x, y, z)](addforceimpulsex-y-z)					| void			| Applies a given acceleration represented by x, y, z (in world coordinates) to the object regardless of its mass.
[addForceOffset(x, y, z, x1, y1, z1)](addforceoffsetx-y-z-x1-y1-z1)	| void 			| Applies a force x, y, z at the position offset x1, y1, z1 from the object's center of mass in world coordinates.
[addTorque(x, y, z)](addtorquex-y-z)								| void			| Apply a rotational force whose direction is represented by x, y, z to the center of mass of the object.
[addTorqueImpulse(x, y, z)](addtorqueimpulsex-y-z) 					| void			| Applies a given angular acceleration represented by x, y, z (in world coordinates) to the object regardless of its mass.
[getAngularVelocity()](getangularvelocity)							| Array[3]		| Returns the vector x, y, z representing the rate of rotation in world coordinates.
[getLinearVelocity()](getlinearvelocity)							| Array[3]		| Returns the vector x, y, z representing the rate of change of its position in world coordinates.
[setAngularVelocity(x, y, z)](setangularvelocityx-y-z-coords) 		| void			| Immediately set the object's rate of rotation to the vector x, y, z in world coordinates.
[setLinearVelocity(x, y, z)](setlinearvelocityx-y-z-coords) 		| void			| Immediately set the object's rate of change of its position to the vector x, y, z in world coordinates.
[wake()](#wake)														| void			| Make an object wake up from its sleeping state.


### addForceAtCenter(x, y, z)

Applies a force at the center of mass of the object.

**Parameters**

Name 		| Type 		| Description
----------- | --------- | ----------------------
x 			| Number 	| Force applied along X axis.
y 			| Number 	| Force applied along Y axis.
z 			| Number 	| Force applied along Z axis.


### addForceImpulse(x, y, z, coords)

Applies a given acceleration represented by x, y, z (in world coordinates) to the object regardless of its mass.

**Parameters**

Name 		| Type 		| Description
----------- | --------- | ----------------------
x 			| Number 	| Force applied along X axis.
y 			| Number 	| Force applied along Y axis.
z 			| Number 	| Force applied along Z axis.


### addForceOffset(x, y, z, x1, y1, z1)

Applies a force x, y, z at the position offset x1, y1, z1 from the object's center of mass in world coordinates.

**Parameters**

Name 		| Type 		| Description
----------- | --------- | ----------------------
x 			| Number 	| Force applied along X axis.
y 			| Number 	| Force applied along Y axis.
z 			| Number 	| Force applied along Z axis.
x1 			| Number 	| X component of offset position.
y1 			| Number 	| Y component of offset position.
z1 			| Number 	| Z component of offset position.


### addTorque(x, y, z)

Apply a rotational force whose direction is represented by x, y, z to the center of mass of the object.

**Parameters**

Name 		| Type 		| Description
----------- | --------- | ----------------------
x 			| Number 	| Torque applied along X axis.
y 			| Number 	| Torque applied along Y axis.
z 			| Number 	| Torque applied along Z axis.


### addTorqueImpulse(x, y, z)

Applies a given angular acceleration represented by x, y, z (in world coordinates) to the object regardless of its mass.

**Parameters**

Name 		| Type 		| Description
----------- | --------- | ----------------------
x 			| Number 	| Torque applied along X axis.
y 			| Number 	| Torque applied along Y axis.
z 			| Number 	| Torque applied along Z axis.


### getAngularVelocity()

Returns the vector x, y, z representing the rate of rotation in world coordinates.

**Return**

`Array[3]` - the rate of rotation in world coordinates.


### getLinearVelocity()

Returns the vector x, y, z representing the rate of change of its position in world coordinates.

**Arguments:**

*(None)*

**Returns:**

`number` -   
Current internal linear velocity value.






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

### broadcast(signal, data, range)

Calls the `signal` method passing the `data` array to any objects within the given `range`. 

**Arguments:**

`signal` (`String`)  
The method name to be called on listening objects.

`data` (`Array`)  
An array of data to be passed to listening objects.

`range` (`number`)  
The distance in meters within which listening objects will receive the broadcast message.

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

Method  								| Return Type 	 | Description
--------------------------------------- | -------------- | --------------------
[rayCast(origin, direction, options)](#raycastorigin-direction-options)		| [FaceIntersect](#faceintersect-reference)	| Casts a ray from an origin in a given direction, sorting all the intersections with simulation objects, and returning the nearest intersection.  All parameters are world space.
[sphereCast(origin, radius, options)](#spherecastorigin-radius-options) 	| [FaceIntersect](#faceintersect-reference) | Casts a ray from an origin in all directions to a given radius, returning an array of all intersections.  Used to see if an object is within the sphere's radius.  All parameters are world space.



### rayCast(origin, direction, options)

Casts a ray from an origin in a given direction, sorting all the intersections with simulation objects, and returning the nearest intersection.  All parameters are world space.

```javascript
		var offset = this.transformAPI.localToGlobalRotation(0, 0, 1);
        var center = this.transformAPI.getPosition();
        var hit = this.Scene.traceAPI.rayCast(center, offset,
        {
            ignore: [findviewnode(this.id)]
        });
        if (hit && hit.distance < 2)
        {
            this.explode();
            return;
        }
```

**Parameters**

Name 		| Type 		| Description
----------- | --------- | --------------------
origin 		| Array[3] 	| A point in world space representing the origin of the ray.
direction  	| Array[3] 	| A direction the ray will travel in world space.
options 	| Object 	| A javascript object representing options (see below)

**options**

Name 			| Type 		| Description
--------------- | --------- | -------------------------
filter 			| function 	| A function to programatically decide to ignore a given object during intersection testing.  The function takes a parameter representing a threejs object and must return true or false.
ignore 			| Array 	| An array of object IDs to ignore.
OneHitPerMesh 	| Boolean 	| Default is false.  If true, stop finding additional interesctions once an intersection is found with each mesh object.

**Return**

[FaceIntersect](#faceintersect-reference) - the nearest intersection of the ray cast. 


### sphereCast(origin, radius, options)

Used to find all polygons with an invisible sphere defined by radius, returning an array of all intersections.  All parameters are world space.

**Parameters**

Name 		| Type 		| Description
----------- | --------- | --------------------
origin 		| Array[3] 	| A point in world space representing the origin of the sphere.
radius  	| Number 	| The radius of the sphere defining which intersecting simulation objects will be returned.
options 	| Object 	| A javascript object representing options (see below)

**options**

Name 			| Type 		| Description
--------------- | --------- | -------------------------
filter 			| function 	| A function to programatically decide to ignore a given object during intersection testing.  The function takes a parameter representing a threejs object and must return true or false.
ignore 			| Array 	| An array of object IDs to ignore.
OneHitPerMesh 	| Boolean 	| Default is false.  If true, stop finding additional interesctions once an intersection is found with each mesh object.

**Return**

[FaceIntersect](#faceintersect-reference)[] - an Array of intersections. 



# TransformAPI Reference

The TransformAPI provides methods to access and change an object's position and rotation.  The TransformAPI also provides methods to translate vectors between coordinate systems.

## Methods

Methods | Return Type | Brief Description
------- | ----------- | -----------------
[getPosition()](#getposition) | Array[3] | Return an object's position relative to its parent.
[getRotation()](#getrotation) | Array[3]  | Returns an object's rotation relative to its parent (in Euler XYZ format).
[getScale()](#getscale) | Array[3]  | Return an object's scale relative to its parent.
[getWorldPosition()](#getworldposition) | Array[3]  | Return an object's global position (relative to the Scene).
[globalRotationToLocalRotation(x, y, z)](#globalrotationtolocalrotationx-y-z) | Array[3] | Converts a global rotation to a local rotation.
[globalToLocal(x, y, z)](#globaltolocalx-y-z) | Array[3] | Moves a point from global space to local space.
[globalToLocalRotation(x, y, z)](#globaltolocalrotationx-y-z) | Array[3] | Converts a global direction vector into the local coordinate system.
[localToGlobal(x, y, z)](#localtoglobalx-y-z) | Array[3] | Moves a point from local space to global space.
[localToGlobalRotation(x, y, z)](#localtoglobalrotationx-y-z) | Array[3] | Converts a local direction vector into the global coordinate system.
[lookAt(t, clamp, axis, up, fromOffset)](#lookatt-clamp-axis-up-fromoffset) | void | Set the rotation of the object to align the `axis` parameter ('X', 'Y', '-Y', 'Z') to point at the `t` position (Array[3]).  The up value ('X', 'Y', or 'Z') defines the rotation around the lookAt vector.  `clamp` ('X', 'Y', or 'Z') can be used to force rotation on only one axis (defaults to null).  `fromOffset` (Array[3]) is a position added to the object's current position (defaults to null).
[move(x, y, z, coordinateSystem)](#movex-y-z-coordinatesystem) | void | Moves an object by a given amount in meters.
[rotate(x, y, z, coordinateSystem)](#rotatex-y-z-coordinatesystem) | void | Rotates the object by given amount (angles in degrees)
[rotateX(angle, coordinateSystem)](#rotatexangle-coordinatesystem) | void | Rotates the object by the given angle (in degrees) around the (local or global) x-axis.
[rotateY(angle, coordinateSystem)](#rotateyangle-coordinatesystem) | void | Rotates the object by the given angle (in degrees) around the (local or global) y-axis.
[rotateZ(angle, coordinateSystem)](#rotatezangle-coordinatesystem) | void | Rotates the object around the z-axis.
[rotateAroundAxis(angle, axis, coordinateSystem)](rotatearoundaxisangle-axis-coordinatesystem) | void | Rotates object around given axis by the given angle.
[setPosition(x, y, z)](#setpositionx-y-z) | void | Set an object's position relative to its parent.
[setRotation(x, y, z)](#setrotationx-y-z) | void | Set an object's rotation by the given angles (in degrees) (in Euler XYZ order) relative to its parent.
[setScale(x, y, z)](#setscalex-y-z) | void | Set an object's scale relative to its parent.


### getPosition()

Return an object's position relative to its parent.

**Return**

`Array[3]` - object position [x, y, z] relative to its parent.


### getRotation()

Returns an object's rotation relative to its parent (in Euler XYZ format).

**Return**

`Array[3]` - angles (in degrees) of rotation [x, y, z] relative to its parent.


### getScale()

Return an object's scale relative to its parent.

**Return**

`Array[3]` - object scale [x, y, z] relative to its parent.


### getWorldPosition()

Return an object's global position relative to the Scene.

**Return**

`Array[3]` - object's global position [x, y, z] relative to the Scene.


### globalRotationToLocalRotation(x, y, z)

Converts a global rotation to a local rotation.

**Parameters**

Name 	| Type 		| Description
------- | ---------	| -----------
x 		| Number 	| Movement around the X axis in meters.
y 		| Number	| Movement around the Y axis in meters.
z 		| Number	| Movement around the Z axis in meters.

**Return**

`Array[3]` - containing local x, y and z values of local rotation.



### globalToLocal(x, y, z)

Moves a point from global space to local space.

**Parameters**

Name 	| Type 		| Description
------- | ---------	| -----------
x 		| Number 	| Position along the X axis in global space.
y 		| Number	| Position along the Y axis in global space.
z 		| Number	| Position along the Z axis in global space.

**Return**

`Array[3]` - a point [x, y, z] in local space.


### globalToLocalRotation(x, y, z)

Converts a global direction vector into the local coordinate system.

**Parameters**

Name 	| Type 		| Description
------- | ---------	| -----------
x 		| Number 	| X component of global direction.
y 		| Number	| Y component of global direction.
z 		| Number	| Z component of global direction.


**Return**

`Array[3]` - A direction vector [x, y, z] in the local coordinate system.



### localToGlobal(x, y, z)

Moves a point from local space to global space.

**Parameters**

Name 	| Type 		| Description
------- | ---------	| -----------
x 		| Number 	| Position along the X axis in local space.
y 		| Number	| Position along the Y axis in local space.
z 		| Number	| Position along the Z axis in local space.

**Return**

`Array[3]` - a point [x, y, z] in global space.


### localToGlobalRotation(x, y, z)

Converts a local direction vector into the global coordinate system.

**Parameters**

Name 	| Type 		| Description
------- | ---------	| -----------
x 		| Number 	| X component of local direction.
y 		| Number	| Y component of local direction.
z 		| Number	| Z component of local direction.


**Return**

`Array[3]` - A direction vector [x, y, z] in the global coordinate system.



### lookAt(t, clamp, axis, up, fromOffset)

Set the rotation of the object to align the `axis` parameter ('X', 'Y', '-Y', 'Z') to point at the `t` position (Array[3]).  The up value ('X', 'Y', or 'Z') defines the rotation around the lookAt vector.  `clamp` ('X', 'Y', or 'Z') can be used to force rotation on only one axis (defaults to null).  `fromOffset` (Array[3]) is a position added to the object's current position (defaults to null).

**Parameters**

Name 		| Type 		| Description
-----------	| ---------	| -----------
t 			| Array[3] 	| The position to look at.
clamp		| String	| Force rotation on only 'X', 'Y', or 'Z'.  Defaults to null.
axis		| String	| The axis the object should align with 'X', 'Y', '-Y', or 'Z'.
up 			| String 	| Defines the up axis of the lookAt vector 'X', 'Y', or 'Z'.
fromOffset 	| Array[3]	| A position added to the object's current position.  Defaults to null.



### move(x, y, z, coordinateSystem)

Moves an object by a given amount in meters.

**Parameters**

Name 				| Type 		| Description
------------------- | ---------	| -----------
x 					| Number 	| Meters to move along the X axis.
y 					| Number	| Meters to move along the Y axis.
z 					| Number	| Meters to move along the Z axis.
coordinateSystem 	| Number	| The coordinate system of the input ('global' or 'local').


### rotate(x, y, z, coordinateSystem)

Rotates the object by given amount (angles in degrees)

**Parameters**

Name 				| Type 		| Description
------------------- | ---------	| -----------
x 					| Number 	| Angle on the X axis to rotate in degrees.
y 					| Number	| Angle on the Y axis to rotate in degrees.
z 					| Number	| Angle on the Z axis to rotate in degrees.
coordinateSystem 	| Number	| The coordinate system of the input ('global' or 'local').


### rotateX(angle, coordinateSystem)

Rotates the object by the given angle (in degrees) around the (local or global) X axis.

**Parameters**

Name 				| Type 		| Description
------------------- | ---------	| -----------
angle 				| Number 	| Angle on the X axis to rotate in degrees.
coordinateSystem 	| Number	| The coordinate system of the input ('global' or 'local').


### rotateY(angle, coordinateSystem)

Rotates the object by the given angle (in degrees) around the (local or global) Y axis.

**Parameters**

Name 				| Type 		| Description
------------------- | ---------	| -----------
angle 				| Number 	| Angle on the Y axis to rotate in degrees.
coordinateSystem 	| Number	| The coordinate system of the input ('global' or 'local').


### rotateZ(angle, coordinateSystem)

Rotates the object by the given angle (in degrees) around the (local or global) Y axis.

**Parameters**

Name 				| Type 		| Description
------------------- | ---------	| -----------
angle 				| Number 	| Angle on the Y axis to rotate in degrees.
coordinateSystem 	| Number	| The coordinate system of the input ('global' or 'local').


### rotateAroundAxis(angle, axis, coordinateSystem)

Rotates object around given axis by the given angle.

**Parameters**

Name 				| Type 		| Description
------------------- | ---------	| -----------
angle 				| Number 	| Angle on the Y axis to rotate in degrees.
axis				| String	| The axis of rotation 'X', 'Y', or 'Z'.		| 
coordinateSystem 	| Number	| The coordinate system of the input ('global' or 'local').


### setPosition(x, y, z)

Set an object’s position relative to its parent.

**Parameters**

Name 	| Type 		| Description
------- | ---------	| -----------
x 		| Number 	| Position along the X axis relative to its parent.
y 		| Number	| Position along the Y axis relative to its parent.
z 		| Number	| Position along the Z axis relative to its parent.



### setRotation(x, y, z)

Set an object’s rotation by the given angles (in degrees) (in Euler XYZ order) relative to its parent.

**Parameters**

Name 	| Type 		| Description
------- | ---------	| -----------
x 		| Number 	| Angle (in degrees) of rotation around the X axis relative to its parent.
y 		| Number	| Angle (in degrees) of rotation around the Y axis relative to its parent.
z 		| Number	| Angle (in degrees) of rotation around the Z axis relative to its parent.


### setScale(x, y, z)

Set an object’s scale relative to its parent.

**Parameters**

Name 	| Type 		| Description
------- | ---------	| -----------
x 		| Number 	| Scale along the X axis relative to its parent.
y 		| Number	| Scale along the Y axis relative to its parent.
z 		| Number	| Scale along the Z axis relative to its parent.