# Physics API

The Physics API provides methods to apply forces and velocities to objects.

<a id='Methods'></a>
## Methods

<a id='addForceAtCenter'></a>
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

<a id='addForceImpulse'></a>
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

<a id='addTorqueImpulse'></a>
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

<a id='addTorque'></a>
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

<a id='addForceOffset'></a>
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

<a id='setLinearVelocity'></a>
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

<a id='setAngularvelocity'></a>
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

<a id='getLinearvelocity'></a>
### getLinearVelocity()

Returns the current internal Linear Velocity value.

**Arguments:**

*(None)*

**Returns:**

`linearVelocity` (`number`)  
Current internal linear velocity value.

<a id='getAngularVelocity'></a>
### getAngularVelocity()

Returns the current internal Angular Velocity value.

**Arguments:**

*(None)*  

**Returns:**

`angularVelocity` (`number`)  
Current internal angular velocity value.
