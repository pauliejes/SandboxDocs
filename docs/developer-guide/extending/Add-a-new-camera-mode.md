# Add a New Camera Mode

Camera modes are manipulations of the Editor Camera. This camera is a special case object that is not part of the VWF simulation. You should not rely on the Editor Camera control code for your in game camera motions. 

The code that drives the Editor Camera is located in `support/client/lib/vwf/views/threejs/`.See [File Organization](http://sandboxdocs.readthedocs.org/en/latest/Developer%20Guide/File-Organization/ "File Organization"). Here, you will find `avatarCameraController.js` and `oldCameraController.js` as well as a few others. 

The file `editorCameraController.js` loads and controls the camera controllers. Add your new controller here just as the existing ones are. Also, you might want to add an entry to the menubar to activate it.