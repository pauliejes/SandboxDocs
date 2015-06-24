# Assets

## Upload a 3D Model
With the Sandbox, you can upload 3D asset file from your own computer into a world. This article explains how.

Supported Formats:

1. 3DS
1. OBJ
1. FBX
1. DAE
1. OSG

Asset files that are uploaded to the Sandbox are not actually stored on the Sandbox server. Instead, they are indexed and tracked by the [ADL 3D Repository](https://3dr.adlnet.gov). This service converts and hosts the model and texture files. 

First, you'll need to create a .Zip file with the 3D model and all its texture. Make sure that you include all the textures that the model requires.

Choose **Create->Upload a 3D model** from the main menu. You should see something like this:

![image](https://cloud.githubusercontent.com/assets/1257870/3497975/e4a57736-05f0-11e4-9c28-c5330a750f0f.png)

Either drag and drop your file, or click 'Browse'. Once you've selected a file, the upload button will enable. Be sure to give the object a title.

Click upload, and wait. If the upload is successful and conversion works, the model should appear in the scene.


## Import a 3D model from a URL
Common mesh importation is done form the ADL 3D Repository however, the online site Dropbox is also an excellent place to store and retrieve COLLADA models and textures.

NOTE: there are a few ways to import meshes. The 3DR integration service is the easiest and best way to import models, but it is also possible to supply a URL to a COLLADA file. The server that hosts the file must implement CORS, and have no authentication requirements. 

NOTE: Also, when directly adding a file URL, you are at the mercy of the importers and exporters - our system is completely bypassed.

## Animation
The ADL 3D Repository strips out animation on COLLADA files.  Dropbox will retain the animation with your .dae file.

When an object is imported via a direct URL, if the model contains an animation sequence, you will find a tab in the [PrimitiveEditor](PrimitiveEditor) that controls that animation frame. 