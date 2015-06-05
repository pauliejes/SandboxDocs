## Add a new menu item

The menu items in the dropdown menus are defined in `support\client\lib\vwf\view\editorview\menus.html`. You can simply add new divs to this HTML file to create new dropdowns or submenus. Styles will be applied automatically. 

Handling the click events for these divs should be in `support\client\lib\vwf\view\editorview\Menubar.js`. Note that all editor actions are unsynchronized code. This means that you should not directly create or modify entities by calling `vwf.createChild` or `vwf.setProperty` or the other VWF API methods. The correct thing to do it bounce the message off the reflector server by calling `vwf_view.kernel.createChild` or `vwf_view.kernel.setProperty` or the other external VWF API methods.

It's also good pratice to check that the given user has permission to perform the action. While the reflector server will reject unauthroized messages, you should check permission beforehand so you can prompt the user with good feedback. The reflector will produce no output when rejecting your messages.

## Add a new editor in the side panel

In order to create a new editor in the side panel, there are a few steps. 

1. Create new editor panel JavaScript file
1. Load the new editor when the EditorView loads
1. Optionally create a global reference
1. Initialize the editorpanel

To create the file, add a new JS file in `support/client/lib/vwf/view/EditorView/`. This file should be a requireJS module, and have a GetSingleton function that creates and return the object. See this example below from `PhysicsEditor.js`

```
define([], function() {
    var PhysicsEditor = {};
    var isInitialized = false;
    return {
        getSingleton: function() {
            if (!isInitialized) {
               var baseclass = require("vwf/view/editorview/panelEditor");
              
                baseclass(PhysicsEditor,'PhysicsEditor','Physics','material',true,true,'#sidepanel')
                
                PhysicsEditor.init()
                initialize.call(PhysicsEditor);
                PhysicsEditor.bind()
                isInitialized = true;
            }
            return PhysicsEditor;
        }
    }
    function initialize()
    {
    	...
    	//set up the object here
    	this.BuildGUI = function()
    	{

    	}
    }
}
```
When calling the baseclass **panelEditor.js**, provide the parameters in this order:

1. The object itself, usually a new blank JS object
1. A name for the object
1. The title that will appear in the titlebar
1. The icon class from the icon sheet
1. Whether or not the editor will disable when there is no selection
1. Whether or not BuildGUI wll be called when the selection is changed
1. The div selector to attach to. Use `#sidepanel` for the normal SidePanel. 

Your object will inherit the functions 

1. show
1. hide
1. isOpen
1. enable
1. disable
1. isDisabled

You might also want to add a button to the toolbar or a menu item. Now that you have the class, you'll need to load it during the boot sequence. To do this, it first must be listed as a dependancy of the EditorView. Open `support/client/lib/vwf/view/EditorView.js` and find the string `define([...`. This is the list of modules that the EditorView depends on. These will be loaded by require.js when the system is started. Add your file to this list. 

You'll need to call the getSingleton function. Within the `if(needTools)` block, add
```
window._YourEditor = require("vwf/view/editorview/yourEditor").getSingleton();
```
If you don't need global or console access to the object, you may choose not to store the module in the global namespace.

You can also add a line
```
this.addManager(window._YourEditor)
```
The EditorView will route VWF API notification calls to your editor, similar to a VWF View Driver.

## Add a new editor camera mode

Camera modes used during editing are fundementally different than cameras used during gameplay. You really should try to avoid using the editor camera as part of a published simulation. 

There is only one editorCamera. This camera is controlled with several different algorithms as defined in the various camera controller modules. Adding a new camera object independant of the existing editorCamera is beyond the scope of this discussion.

You can add new editor camera modes by creating a new file in `support/client/lib/vwf/view/threejs/`. This file should be a require.js define call that returns an object. This object should implement
```
   this.initialize = function(camera){...}  //store the incoming camera
   this.activate = function(){...}          //this controller has been activated
   this.deactivate = function(){...}        //this controller has been deactivated
   this.setCameraMode = function(mode){...} //used for controllers that are registered to more than one mode string
   this.updateCamera = function(){...}      //here, you should set the position and orientation of the camera passed into initialize
```   
Next, add your module as a dependancy for the module in `support/client/lib/vew/view/threejs/editorCameraController.js`, and associate it with a mode string by adding
```
  yourModule.initialize(this.camera);
  this.addController('modeName',yourModule);
```
Your new mode will receive JQuery input events when the user takes mouse actions on the 'index-vwf' div, and your mode is active. Take a quick look at 'vwf/view/editorView/threejs/editorCameraController' to see what functions are available.
You can activate your new controller by calling 
```
   require('vwf/view/editorView/threejs/editorCameraController').setCameraMode('modeName')
```

## Show or hide GUI components

Each of the major GUI components can be hidden.
```
require("vwf/view/editorview/WindowResize").hideLibrary()
require("vwf/view/editorview/WindowResize").showLibrary()
require("vwf/view/editorview/WindowResize").hideSidePanel()
require("vwf/view/editorview/WindowResize").showSidepanel()
require("vwf/view/editorview/WindowResize").hideMenubar()
require("vwf/view/editorview/WindowResize").showMenubar()
require("vwf/view/editorview/WindowResize").hideToolbar()
require("vwf/view/editorview/WindowResize").showToolbar()
require("vwf/view/editorview/WindowResize").hideStatusbar()
require("vwf/view/editorview/WindowResize").showStatusbar()
```

## Add a new Avatar
Todo

## Add a new Entity Library

Entity libraries are JSON files that populate the EntityLibrary GUI element on the left hand side of the interface. The Editor can load multiple libraries, and each library can contain multiple entities. Default libraries are configured in `public\adl\sandbox\contentLibraries\libraries.json`. This is a simple JSON object that contains an map of library names and URLS in the form
```
{
    "Demo Entities": {
        "url": "./contentlibraries/entities.json"
    },
}
```

Each referenced url for an entity library file should resolve to a JSON object. This URL need not be on the same server as the Sandbox engine. A library file is a map of titles and data in the form
```
"Grassy Plain":{
		"url":"./contentlibraries/environments/vwf/grassyplain.vwf.json",
		"preview":"./contentlibraries/environments/thumbs/grassyplain.png",
		"type":"environment"
	}, ...
```	
These objects have several available keys, at minimum you should provide the url,preview,and type. 'url' is the location of the resource JSON data. This data need not be on the same server as the library file itself. 'preivew' is simply an image that will be displayed. 'type' effects the behavior of the EntityLibrary, and also the interpretation of the data in 'url'. 'type' can be

1. asset         - use this for any 3D entity. The data at the url should be a VWF node definition
1. child         - use this for behaviors. The library will only all this object to be dropped onto another object. url should be a VWF node 
1. enviornment   - this is a package of scene settings. 
1. material      - this is a MaterialDef value

There are a few other properites that can be added to the library object definition that control the drag and drop 3D preview

```
	   "dropPreview":
        {
            "url": "./contentlibraries/entities/assets/defaulttree.json",
            "type": "subDriver/threejs/asset/vnd.osgjs+json+compressed",
            "transform": [
                1,
                0,
                0,
                0,
                0, -2.2112923048211997E-8,
                1,
                0,
                0, -1, -2.2112923048211997E-8,
                0,
                0,
                0,
                0,
                1
            ]
        },
```
DropPreview should contain a know asset type string (see the asset loading docs), a URL to a 3D asset file, and a transform. This transform can be used to offset the raw three.js object from it's origin to reflect what the asset might look like in the VWF node definition. 

'dropOffset' can specify an offset transform that will be applied to the object after the library identifies the drop position in 3D space. 
'snap' will cause the drag and drop behavior to restrict the creation point to multiples of the value. Should be a number, in meters.



