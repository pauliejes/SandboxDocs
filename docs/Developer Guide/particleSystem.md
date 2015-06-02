# Particle System

Explain the intricacies and usefulness of the particle system housed in `particlesystem.js`.

## CreateParticleSystem(nodeID, childID, childName) class

More technical and specific description of what the particle system does.

**Arguments:**

`nodeID` (`String`)  
Unique identifier corresponding to a particular node.

`childID` (`String`)  
Unique identifier corresponding to the child node. 

`childName` (`String`)
Name of the child node.

**Returns:**

`particleSystem` (`THREE.Vector3`)  
A system of particles...

### Constructor

#### new THREE.PointCloud(particles, shaderMaterial_default)

Brief description of constructor.

**Arguments:**

`particles` (`THREE.Geometry`)  
Brief insight into argument. If the argument is optional add that in parentheses at the end.

`shaderMaterial_default` (`THREE.ShaderMaterial`)  
If there are no arguments explicitly state and italicize. In such a case there is no need for a description.

### Properties

#### particles

Type: `THREE.Geometry`

Create the particle variables.

#### vertShader_default

Type: `Object`

Default material expects all computation done cpu side, this just renders. **Note:** since the color, size, spin, and orientation are just linear interpolations, they can be done in the shader.

#### fragShader_default

Type: `Object`

Default material expects all computation done cpu side, this just renders. **Note:** since the color, size, spin, and orientation are just linear interpolations, they can be done in the shader.

#### attributes_default

Type: `Object`

The default shader, the one used by the analytic solver, just has some simple stuff. Includes: `size`, `vertexColor`, and `random`.


#### uniforms_default

Type: `Object`

The default shader, the one used by the analytic solver, just has some simple stuff. Includes: `amplitude`, `texture`, `pCount`, `maxRate`, `useTexture`, `maxSpin`, `minSpin`, `screenSize`, `maxOrientation`, `minOrientation`, `time`, `fractime`, `sizeRange`, `textureTiles`, `colorRange`, `startColor`, `endColor`, `startSize`, `endSize`, and `alphaTest`.

#### shaderMaterial_default

Type: `THREE.ShaderMaterial`

Materials to be shaded.	Includes: `uniforms`, `attributes`, `vertexShader`, and `fragmentShader`.

#### vertShader_interpolate

Type: `Object`

The interpolate shader blends from one simulation step to the next on the shader. This allows for a complex simulation to run at a low framerate, but still have smooth motion.  This is very efficient, as it only requires sending data up to the gpu on each sim tick. reuse the frag shader from the normal material.

#### attributes_interpolate

Type: `Object`

The interpolation does need to remember that previous position. Includes: `random`, `previousPosition`, `age`, and `lifespan`.

#### shaderMaterial_interpolate

Type: `THREE.ShaderMaterial`

Enter useful inforamtion here. Includes: `uniforms`, `attributes`, `vertexShader`, and `fragmentShader`.

#### vertShader_analytic

Type: `Object`

Analytic shader does entire simulation on GPU. It cannot account for drag, gravity, nor can it generate new randomness. Each particle has it's randomness assigned and it just repeats the same motion over and over. Also, the other solvers can hold a particle until it can be reused based on the emitRate. This cannot, as the entire life of the particle must be computed from an equation given just time t. It does offsett them in time to avoid all the particles being generated at once. also, it does not account for emitter motion. The upside is it is very very efficient, no CPU intervention required.

#### fragShader_analytic

Type: `Object`

Divides into 4 or 9 "virtual" textures to be able to have different images on particles. Gets the color from the texture and blends with the vertexColor.

#### attributes_analytic

Type: `Object`

Describe attributes analytic here. Includes: `acceleration`, `velocity`, `previousPosition`, `age`, `lifespan`, `random`, `vertexColor`, and `size`.

#### shaderMaterial_analytic

Type: `THREE.ShaderMaterial`

describe shader material analytic here. Includes: `uniforms`, `attributes`, `vertexShader`, and `fragmentShader`.

###Methods

#### create Particle(i)

Creates a new particle. Creates and stores all the values for vertex attributes in each shader.

**Arguments:**

`i` (`number`)  
The number of the new particle.

**Returns:**

`particle` (`THREE.Vector3`)  
Brief description of returned value. Or if there is no returned value:

#### generatePoint()

Generate a new point in space based on the emitter type and size.
**Arguments:**

*(None)*

**Returns:**

`point` (`THREE.Vector3`)  
A new point in space.

#### rebuildParticles()

Setup the particles with new values.

**Arguments:**

*(None)*

**Returns:**

*(Nothing)*

#### setupParticle(particle, mat, inv)

Set the particle initial values. Used when creating and reusing particles.

**Arguments:**

`particle` (`THREE.Vector3`)  
Brief description of argument. 

`mat` (`matrix`)
Array of numbers relating to the particle's placement in space.

`inv` (`number`)
I don't know.  Inventory, Inverse?

**Returns:**

*(Nothing)*

#### updateAnalyticShader(time)

When updating in `AnalyticShader` mode, the process is very simple just inform the shader of the new time.

**Arguments:**

`time` (`number`)  
Add to the old time and calculate using the combined time to update.

**Returns:**

*(Nothing)*

#### updateAnalytic(time)

In `Analytic` mode, run the equation for the position, and update each particle.

**Arguments:**

`time` (`number`)  
Add to the old time and calculate using the combined time to update.

**Returns:**

*(Nothing)*

#### updateEuler(time)

Timesliced Euler integrator which can do more complex sim.  It ticks 10 times a second, and blends tick with previous via a shader.

**Arguments:**

`time` (`number`)  
Add to the old time and calculate using the combined time to update.

**Returns:**

*(Nothing)*

#### updateParticleAnalytic(particle, mat, inv, delta_time)

Update a particle from the Analytic solver.

**Arguments:**

`particle` (`THREE.Vector3`)  
Brief description of argument. 

`mat` (`matrix`)
Array of numbers relating to the particle's placement in space.

`inv` (`number`)
I don't know.  Inventory, Inverse?

`delta_time` (`number`)  
The change in time since last update.    

**Returns:**

*(Nothing)*

#### updateParticleEuler(particle, mat, inv, step_dist)

Update a particle with the Euler solver.

**Arguments:**

`particle` (`THREE.Vector3`)  
Brief description of argument. 

`mat` (`matrix`)
Array of numbers relating to the particle's placement in space.

`inv` (`number`)
I don't know.  Inventory, Inverse?

`step_dist` (`number`)  
The amount between the previous and the current, the  step distance.

**Returns:**

*(Nothing)*

#### update(time)

Update the particle system.

**Arguments:**

`time` (`number`)  
The current time in millisecond from the system.

**Returns:**

*(Nothing)*

#### setSolverType(type)

Change the solver type for the system.

**Arguments:**

`type` (`String`)  
String indicating the type of solver to be used.

**Returns:**

*(Nothing)*

#### updateTransform(newtransform)

If you move the system, all the particles need to be recomputed to look like they stick in world space. Not that we don't do this for the `AnalyticShader`.  We could, but that solver is meant to be very high performance, so we don't.

**Arguments:**

`newtransform` (`number`)  
Get the current transform, and invert the new one.

**Returns:**

*(Nothing)*

#### setParticlecount(newcount)

Change the system count. **Note:** this must be set before the first frame renders, it cannot be changed at runtime.

**Arguments:**

`newcount` (`number`)  
The new number of particles to be a part of the system.

**Returns:**

*(Nothing)*

## particleSystem class

Description  

### Constructor

#### new particleSystem(childID, childSource, childName)

Brief description.

**Arguments:**

`childID` (`String`)
Unique identifier representing the child.

`childSource` (`String`)
Unique identifier representing the parent.

`childName` (`String`)
The name of the child.

### Properties

`ps` (`particleSystem`)  
Instance of a particle system.

### Methods

#### settingProperty(propertyName, propertyValue)

Sets a property of the particle system to the given value and rebuilds the particles.

**Arguments:**

`propertyName` (`String`)  
String matching the name of a particular particle system property.

`propertyValue` (`String`)  
String of a value corresponding to the particular property.

**Returns:**

*(Nothing)*

####initializingNode()

Starts up a node.

**Arguments:**

*(None)*

**Returns:**

*(Nothing)*

####gettingProperty(propertyName)

Provides the value of the given property.

**Arguments:**

`propertyName` (`String`)  
String corresponding to a particle system property.

**Returns:**

`propertyValue` (`String`)  
String conveying the value of the specified property.

####callingMethod(name, args)

Describe what this function does.

**Arguments:**

`name` (`String`)  
The name of the calling method.

`args` (`Array of Strings`)
The corresponding arguments.

**Returns:**

*(Nothing)*

####getRoot()

Gets the root of the node.

**Arguments:**

*(None)*

**Returns:**

`rootnode` (`Node`)  
The root of the node.
