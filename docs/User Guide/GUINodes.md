# GUI Nodes 

The Sandbox contains a set of entities that can be used to add graphical interfaces to a world. These interfaces are actual simulation objects, and as such can have scripts and properties, persist to the database, can be saved to inventory, and otherwise be treated exactly as a 3D asset. We currently support buttons, panels, sliders, labels, checkboxes, and dialogs. You can create a GUI element from the top level Create menu. 

When in edit mode, while the simulation is stopped, you can select a GUI Node by clicking on it. You should see a dark blue border around it. Double clicking will allow you to drag and place it, and single clicking will stop dragging. When a GUI node is created, it becomes a child of the selected entity. However, since it is not part of the 3D scene, properties like the parent transform or visible will not effect it. 

GUI Nodes can have child GUI Nodes - this will work just as nested DOM elements do.

## Positioning GUI Nodes

GUI Nodes can be positioned using the transform property, just like 3D nodes. However, this value is interpereted differently. Only the translation portion of the transform matrix is used. The X and Y components are uses a percent offsets from the Node's parent div - either the root of the page or the parent GUI Node. Scale and rotation are ignored. Most GUI nodes have a length and width property - these are abolute pixel sizes.

## Type of GUI Nodes

### Dialog

A dialog with a close button. Note that closing the dialog sets its *visible* property to false - the object still exists in the scene. The dialog can be resized or moved at run-time. The properties will be updated accordingly

Properties

* title - the title of the dialog
* visible - whether or not the dialog is closed
* height - the height in real pixels of the dialog inner content
* width - the width of the inner content in real pixels

Events

* none

### Button

A button. Importantly, this node fires the *pointerClick* event when the user clicks it

Properties

* text - the text on the button
* height - the height in real pixels of the dialog inner content
* width - the width of the inner content in real pixels

Events

* pointerClick - fired when the user clicks on the button

### Slider

A slider. The user can set a value by dragging a handle along a track. The slider exposes a *change* event, and a *value* property

Properties

* value - the currently selected value of the slider
* height - the height in real pixels of the dialog inner content
* width - the width of the inner content in real pixels
* max - the value at the maximum extent
* min - the value at the minimum extent
* step - the size of each movement of the handle

Events

* change - fired when the value changes. Value will change before the event fires.

### Label

A simple text label. Can have several font properties set. The text will wrap at the end of the width, and will overflow if it cannot wrap.

Properties

* text - the text of the label
* height - the height in real pixels of the inner content
* width - the width of the inner content in real pixels
* fontColor - the color of the font
* fontSize - the size in pixels of the font
* textAlign - center, left or right align the text

Events

* none

### Checkbox

A simple checkbox. The box will extend to fill the size of the node specified by *height* and *width*

Properties

* height - the height in real pixels of the inner content
* width - the width of the inner content in real pixels
* isChecked - whether or not the box is checked

Events

* checked - *isChecked* transitioned from false to true
* unChecked - *isChecked* transitioned from true to false

### Image

A simple image element. Can be set with the texture chooser, or by URL. 

Properties

* src - the url of the image to load
* height - the height in real pixels of the inner content
* width - the width of the inner content in real pixels

Events

* none

### Panel

The panel is intended to function as a group for other GUI Nodes. It can have a background color and a border. It fires no events.
* height - the height in real pixels of the inner content
* width - the width of the inner content in real pixels
* backgroundColor - the color of the background
* backgroundVisible - whether or not the background is drawn
* borderColor - the color of the border
* borderRadius - the rounding of the panel edges
* borderWidth - the width in pixels of the border