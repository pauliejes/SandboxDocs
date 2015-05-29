#Sandbox Audio API Reference

Defining options and controls with the audio of the Sandbox.

##Audio API class

<a id='properties'></a>
###Properties

<a id='id'></a>
#### id
Type: `String`
The name to identify the sound

<a id='sound'></a>
#### sound
Type: `String` `filename`
The file of the sound

<a id='position'></a>
#### position
Type: `number`
Where the sound can be found

<a id='volume'></a>
#### volume
Type: `number`
How loud

<a id='end_range'></a>
####end range
Type: `number`
some number for the end

<a id='start_range'></a>
####start range
Type: `number`
some number for the start

<a id='looping'></a>
####looping
Type: `boolean`
Indicates whether or not the sound is to loop/repeat

<a id='playing'></a>
####playing
Type: `boolean`
Indicates whether or not the sound is currently in use  

<a id='behaviors'></a>
###Behaviors

<a id='play'></a>
####play


Plays sound.

<a id='pause'></a>
####pause

Halts playback of sound, holding position along track to resume where left off.

<a id='stop'></a>
####stop

Ends playback of sound, resets position.

<a id='prototypeBehvaiors'></a>
###Prototype Behaviors

<a id='loop'></a>
####loop
Sets the `boolean` looping variable.

<a id='unloop'></a>
####unloop
Sets the `boolean` looping variable.

<a id='updateSourcePosition'></a>
####updateSourcePosition

Get the position of the source object. **Note:** The 3D driver keeps track of the position.

**Arguments:**

*(None)*

**Returns:**

World position of the source object `Type`

<a id='updateVolume'></a>
####updateVolume

HTML can't actually play it louder, however we can make it 'carry' farther by using the inverse and adjusting the range parameters of the falloff curve.

**Arguments**

`camerapos` `(Type)`

**Returns**

*(Nothing)*

<a id='driverMethods'></a>
###Driver Methods

<a id='initialize'></a>
####Initialize()

start it up

**Arguments:**

*(None)*

**Returns:**

*(Nothing)*

<a id='playSound'></a>
####playSound(url, volume)

Lets GUI elements play sounds.

**Arguments:**

`url` `(String)`  
String specifying the URL.

`volume` `(number)`  
How loud.

**Returns:**

*(Nothing)*

<a id='calledMethod'></a>
####calledMethod(id, name, params)

This is a good place to explain.

**Arguments:**

`id` `(String)`  
The identification String.

`name` `(String)`  
The name of the command:

* `playSound`

	If the scene played the sound, it has no position and just plays at full volume. Nodes that are not the scene use their position to adjust the volume.

* `pauseSound`

* `stopSound`

* `deleteSound`

	**Note:** only delete sound if you are sure the sound will not play again any time soon

`params` `(Array)`  
Array of additional parameters

**Returns**

*(Nothing)*

####ticked()

Update the sound volume based on the position of the camera and the position of the object

**Arguments:**

*(None)*

**Returns:**

*(Nothing)*

####deletedNode(id)

Deletes the specified sound source node.

**Arguments:**

`id` `(String)`  
The String identifier of the node deleted.

**Returns:**

*(Nothing)*
