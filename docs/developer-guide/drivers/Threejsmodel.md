
# Three.js Model Driver

###SubDrivers
In order to make our code more modular, graphics engine functions are divided into sub-components we call subdrivers. Must of the real workload of the THREE.js driver is creating the sub drivers and sending messages into them. Subdrivers can inherit other subdrivers, and can also be specified by a user node definition. This last option allows a node to load custom graphics code into the simulation at runtime, even from another domain. 

###Important SubDrivers
1. [Transformable SubDriver](Transformable SubDriver) - manages setting and getting the position / orientation / scale of objects
1. [Asset SubDriver](Asset SubDriver) - is an entity in the simulation that loads a resource file, like a 3D model
1. [MaterialDef SubDriver](MaterialDef SubDriver) - manages materials
1. [Terrain](http://sandboxdocs.readthedocs.org/en/latest/User%20Guide/Working%20with%20Terrain/ "Terrain") - implements the terrain system
1. [ParticleSystem SubDriver](ParticleSystem SubDriver) - implements particle systems
1. [Prim SubDriver](Prim SubDriver) - master class for all primitive objects. Implements the modifier stack.
1. [Modifier SubDriver](Modifier SubDriver) - allow for transformation of parent geometry
1. [Spline SubDriver](Spline SubDriver) - implements a 2D shape as a list of points

###Other SubDrivers
1. *Visible* - hides or shows objects
1. All modifiers and prims have their own, like `sphere.js` or `bend.js`
1. *Selectable* - enables/disables raycast functionality for an object. See [Scene Manager](../SceneManager)
1. *Static* - set objects as static or dynamic. See [Scene Manager](../SceneManager)

###Custom Subdrivers
Nodes may request that they be associated with a subdriver via the `source` field of their [VWF](../VWF) definition. 
    extends:"node3.vwf.yaml",
    type: "subDriver/threejs"
    source: "url to driver code"
A subdriver should implement the [VWF](../VWF) model driver API, and additionally expose a `getRoot` method that returns a three.js object. They may inherit the properties of other subdrivers by specifying an `inherit` property.

The format of a subdriver file should be a function that return a new function, which when called returns an object which implements the above described interface. The function returned by the SubDriver file is the SubDriverFactory for the given subdriver type. SetProperty, callMethod, and other VWF API calls are passed to this driver, and all the associated functions in the drivers it inherits. The inheritance is accomplished by merging together the JavaScript objects of the entire inheritance tree of subdriver. 
```
(function(){ //boilerplate
		function text(childID, childSource, childName)  //the actual driver code
		{
			this.text = "hi";
			this.inherits = ['vwf/model/threejs/prim.js']; // other subdrivers to be merged into this
			this.setProperty ...
                        this.calledMethod ...
			this.getRoot = function()
			{
				return this.rootnode;
			}
			this.rootnode = new THREE.Object3D(); //all subdrivers must have a GetRoot function
		}
		//default factory code
        return function(childID, childSource, childName) {  //the factory function
			//name of the node constructor
            return new text(childID, childSource, childName); //returns a new subdriver
        }
})();
```