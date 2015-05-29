# Client API

Enter meaningful text here.

## Client API Class

Short summary of `ClientAPI`

<a id='methods'></a>
###Methods

<a id='getUserNameForConnectionID'></a>
#### getUserNameForConnectionID(id)

Talk more about that.

**Arguments:**

`id` (`String`)  
String unique to each user.

**Returns:**

`name` (`String`)  
The user's name.

<a id='getConnectionIDForUserName'></a>
#### getConnectionIDForUserName(name)

Discuss the various ins and outs.

**Arguments:**

`name` (`String`)  
The user's name.

**Returns:**

`id` (`String`)  
String unique to each user.

<a id='getAvatarForUserName'></a>
#### getAvatarForUserName(name)

What's in a name?

**Arguments**

`name` (`String`)  
The user's name.

**Returns**

`avatar` (`node`)  
The user's 3D avatar. 

<a id='focus'></a>
#### focus(cid, nodeID)

Focus.

**Arguments:**

`cid` (`String`)  
The client's unique identification string.

`nodeID` (`String`)  
The node's unique identification string.

**Returns:**

*(Nothing)*

<a id='getCameraIDForClient'></a>
#### getCameraIDForClient(id)

Give me that thingamajig, so I can take a picture.

**Arguments:**

`id` (`String`)  
The client's unique identification string.

**Returns:**

`cameraID` (`String`)  
The camera's unique identification string.

<a id='getCameraForClient'></a>
#### getCameraForClient(id)

Now that we've got the camera, we are out of here!

**Arguments:**

`id` (`String`)  
The client's unique identification string.

**Returns:**

`camera` (`node`)  
The first person camera for the user.
