#EditorView Driver
## Overview

The entire editing interface is implemented as a single large VWF View driver ([Architecture Overview](Architecture Overview)). This driver is located in `/support/client/lib/vwf/views/Editorview/` see ([File Organization](File Organization)).

The EditorView is mostly a shell that loads up several modules as required. This depends on the metadata about the state which is retrieved from the Service API at world load. 

The modules loaded by the EditorView to provide functionality are either Managers or Editors (though there is currently little difference between these). Generally, Editors expose more of a UI, and Managers are used by other modules for services. Most editors and managers are loaded into global variables with the file name prefixed with an underscore. For instance, the Editor component is implemented in `Editor.js` and is available at runtime as `window._Editor`. 

### Major components
1. [UndoManager](UndoManager)
1. [MaterialEditor](MaterialEditor)
1. [PrimitiveEditor](PrimitiveEditor)
1. [ScriptEditor](ScriptEditor)
1. [SelectionEditor](SelectionEditor)
1. [InventoryManager](InventoryManager)
1. [_3DRIntegration](_3DRIntegration)
1. [Mapbrowser](Mapbrowser)
1. [Publisher](Publisher)
1. [UserManager](UserManager)
1. [DataManager](DataManager)
1. [PhysicsEditor](PhysicsEditor)

## How To ...
1. [Add a new menu item](Add a new menu item)
1. [Add a new editor in the side panel](Add a new editor in the side panel)
1. [Add a new camera mode](Add a new camera mode)
1. [Show or hide GUI components](Show or hide GUI components)
