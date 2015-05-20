# Audio API

Read carefully, this is going to be hard to hear.

Includes values...
1. id - the name to identify the sound
2. sound - the file of the sound
3. position - where the sound can be found
4. volume - how loud
5. end range - ??
6. start range - ??
7. looping - boolean indicator whether or not the sound is to loop/repeat
8. playing - boolean indicator whether or not the sound is currently in use  

#### **Play, Pause, and Stop**

Standard features of Play, Pause, and Stop, respectively.

#### **Loop/Unloop**

Sets the boolean looping variable.

#### **Update Source Position**

Get the position of your source object.

Note: the 3D driver keeps track of the postion.

#### **Update Volume**

HTML can't actually play it louder, however we can make it 'carry' farther by using the inverse and adjusting the range parameters of the falloff curve.

## **The Driver**

1. Initialize - start it up
2. Play sound - lets GUI elements play sounds
3. Called Method - takes id, name, and params
	1. if the scene played the sound, it has no position and just plays at full volume
	2. nodes that are not the scene use their position to adjust the volume
	3. pause sound
	4. stop sound
	5. delete sound - **note** only use this if you are sure the sound will not play again any time soon
4. Ticked - update the sound volume based on the position of the camera and the position of the object
5. Deleted Node
