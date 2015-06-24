# Transform API

Facilitates manipulation of nodes by allowing manipulation of their properties such as position, and  rotation.

Facilitates movement, rotation, and more of nodes.

<a id='methods'></a>
## Methods

<a id='move'></a>
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
Specify either 'global' or local coordinate system.

**Returns:**

*(Nothing)*

<a id='getPosition'></a>
### getPosition()

Return a node's local position?

**Arguments:**

*(None)*

**Returns:**

`localPosition` (`Array of numbers`)  
Array containing local x, y, and z coordinates.

<a id='getWorldPosition'></a>
### getWorldPosition()

Return a node's global position.

**Arguments:**

*(None)*

**Returns:**

`globalPosition` (`Array of numbers`)  
Array containing global x, y, and z coordinates.

<a id='localToGlobal'></a>
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

<a id='localToGlobalRotation'></a>
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

<a id='globalToLocal'></a>
### **Global to Local**

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

<a id='globalToLocalRotation'></a>
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

<a id='globalRotationToLocalRotation'></a>
### **Global Rotation to Local Rotation**

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

<a id='setPosition'></a>
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

<a id='rotate'></a>
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

<a id='rotateX'></a>
### rotateX(angle, coordinateSystem)

Rotates the node around the x-axis.

**Arguments:**

`angle` (`number`)  
Angle of movement around the x-axis.

`coordinateSystem` (`String`)
Designates whether local, global, or parent coordinates are given.

**Returns:**

*(Nothing)*

<a id='rotateY'></a>
### rotateY(angle, coordinateSystem)

Rotates the node around the y-axis.

**Arguments:**

`angle` (`number`)  
Angle of movement around the y-axis.

`coordinateSystem` (`String`)
Designates whether local, global, or parent coordinates are given.

**Returns:**

*(Nothing)*

<a id='rotateZ'></a>
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


<a id='rotateAroundAxis'></a>
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

<a id='getRotation'></a>
### getRotation()

By some form of magic, returns a number representing the rotation

**Arguments:**

*(None)*

**Returns:**

`euler` (`Array of numbers`)  
Angles of rotation around x, y and z axes.

<a id='setRotation'></a>
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

<a id='getScale'></a>
### getScale()

Returns the magnitude of the node.

**Arguments:**

*(None)*

**Returns:**

`vector` (`Array of numbers`)  
Array of x, y, and z vectors.

<a id='setScale'></a>
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

<a id='scaleMatrix'></a>
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

<a id='lookAt'></a>
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
