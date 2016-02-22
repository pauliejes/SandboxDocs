<h1>GUI Elements Reference</h1>

A reference for the properties and events of GUI Element object types.

[TOC]

## Dialog

A dialog with a close button. Note that closing the dialog sets its `visible` property to false - the object still exists in the scene. The dialog can be re-sized or moved at run-time. The properties will be updated accordingly.

Properties

* `title` - the title of the dialog
* `visible` - whether or not the dialog is closed
* `height` - the height in real pixels of the inner content
* `width` - the width in real pixels of the inner content

Events

* none

## Button

A button. Importantly, this node fires the `pointerClick` event when the user clicks it.

Properties

* `text` - the text on the button
* `height` - the height in real pixels of the inner content
* `width` - the width in real pixels of the inner content

Events

* `pointerClick` - fired when the user clicks on the button

## Slider

A slider. The user can set a value by dragging a handle along a track. The slider exposes a `change` event, and a `value` property.

Properties

* `value` - the currently selected value of the slider
* `height` - the height in real pixels of the inner content
* `width` - the width in real pixels of the inner content
* `max` - the value at the maximum extent
* `min` - the value at the minimum extent
* `step` - the size of each movement of the handle

Events

* `change` - fired when the value has been changed. Value will change before the event fires.

## Label

A simple text label. Can have several font properties set. The text will wrap at the end of the width, and will overflow if it cannot wrap.

Properties

* `text` - the text of the label
* `height` - the height in real pixels of the inner content
* `width` - the width in real pixels of the inner content
* `fontColor` - the color of the font
* `fontSize` - the size in pixels of the font
* `textAlign` - center, left or right align the text

Events

* none

## Checkbox

A simple checkbox. The box will extend to fill the size of the node specified by `height` and `width`.

Properties

* `height` - the height in real pixels of the inner content
* `width` - the width in real pixels of the inner content
* `isChecked` - whether or not the box is checked

Events

* `checked` - fired when `isChecked` transitioned from false to true
* `unChecked` - fired when `isChecked` transitioned from true to false

## Image

A simple image element. Can be set with the texture chooser, or by URL. 

Properties

* `src` - the url of the image to load
* `height` - the height in real pixels of the inner content
* `width` - the width in real pixels of the inner content

Events

* none

## Panel

The panel is intended to function as a group or container for other GUI Elements. It can have a background color and a border. It fires no events.

Properties

* `height` - the height in real pixels of the inner content
* `width` - the width in real pixels of the inner content
* `backgroundColor` - the color of the background
* `backgroundVisible` - whether or not the background is drawn
* `borderColor` - the color of the border
* `borderRadius` - the rounding of the panel edges
* `borderWidth` - the width in pixels of the border

Events

* none