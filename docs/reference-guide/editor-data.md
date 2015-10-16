<h1>Editor Data</h1>

[TOC]

# Overview

The VW Sandbox provides the Scripting API, which is accessible through the ScriptEditor and is attached to each simulation object to define and manipulate simulation logic.

#Common Properties

#### displayname
A human-readable description of the property. Defaults to `""` if not specified.

#### property


#### type
`slider` (Required)

#Types
This section describes the different types of input fields supported by Editor Data. It is assumed that

## slider
Properties of type `slider` are represented as

### Properties

#### min
The lower bound of the slider. (Required)

#### max
The upper bound of the slider. (Required)

#### step
Minimum increment value for both the slider and the number input field. Defaults to `1` if not specified.

#### type
`slider` (Required)

## color

The `Scene` provides properties and methods accessible to all simulation objects.

### Properties

No additional properties.

## check
Equivalent to [HTML checkbox](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox) input fields.

### Properties

No additional properties.

## button
Buttons are used to call methods on a VWF node. The presentation of these buttons is equivalent to [HTML button](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button) elements. Buttons do not use the `displayname` property.

### Properties

#### label
Virtually equivalent to `displayname`. Use `label` in the exact same way. If label is omitted, `method` is displayed in its place.

#### method
This name of the method to call. (Required)

## rangeslider

### Properties

#### min
#### max
#### step
#### property


## vector
### Properties
#### step

## rangevector
### Properties
#### step

## text
### Properties
No additional properties.

## choice
The `choice` property type is used to make a selection from a list of choices. The presentation of `choice` is identical to [HTML select](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) elements.

### Properties
#### values
An array of selectable items intended to appear within the generated drop-down menu.

#### labels
An array of human-readable names that correspond to each value in the `values` array.

## map

### Properties
No additional properties.

## nodeid
### Properties
No additional properties.

## sectionTitle
### Properties
No additional properties.

## label
### Properties
No additional properties.

## prompt
### Properties
No additional properties.
