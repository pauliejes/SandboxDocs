# Modifiers

Modifiers alter or reshape primitives.  To use a modifier select a primitive (except an empty node) then from the drop-down menu bar choose create --> modifiers --> and choose the one you want. The modifier then shows up as a child of primitive in the Editor side panel Heirarchy heading. With the primitive selected the modifier shows up in the Editor side panel Properties heading under the specific properties for that primitive.  This opens a small panel where you may manipulate the values of the modifier to make changes to the primitive.

Let's try out the modifiers and try to explain what they do.
### Standard Properties

#### Flags
By default all modifiers have the same flags of Name, Owners, with checkboxes of visible, and inherit parent scale checked, and static, dynamic, cast shadows, receive shadows, passable, and selectable unchecked.

#### Transforms
Displays and controls the translation, rotation and scale of a primitive. Values refer to the x, y, and z axes. relatively useless on a modifier.

**Translation** Placement of the object. Default: 0, 0, 0.

**Rotation** Orientation of the object in position. Default: 0, 0, 0.

**Scale** Size of the object. Default: 1, 1, 1.

#### Specific Properties

At a modifier's specific properties panel buttons let you delete, select, or copy a modifier.

<a id='bend'></a>
## Bend

Seen easiest on a primitive with straight lines like a box. Bends the primitive.

#### Specific Properties
Properties that apply to spheres but may not apply to other types of objects. Here you may also use buttons to delete, select, or copy the given sphere.

**Enabled Checkbox** - default checked.

**Bend Amount** - default 0, range -0.050 - 0.050.

**Major Axis** - default X, choose X, Y, or Z.

**Minor Axis** - default X, choose X, Y, or Z.

(Note: you can force the value greater than the range using the up and down arrow buttons).

<a id='twist'></a>
## Twist

To bend or turn (something) in order to change its shape (Merriam-Webster). Twists the primitive.

#### Specific Properties

**Twist Amount Slider** - default 0, range -1.00 - 1.00.

<a id='taper'></a>
## Taper

Diminish or reduce or cause to diminish or reduce in thickness toward one end (Google search).

#### Specific Properties

**Taper Amount Slider** - default 0, range -1.00 - 1.00.

<a id='perlinNoise'></a>
## Perlin Noise

Noise refers to a computer-generated pseudo-random texture to better simulate real surfaces. 

You can think of Perlin noise a bit like a wave - a 2D or 3D wave - the noise scale is the frequency, and the different amounts are the amplitude. Instead of a smooth sine wave, it's all "noisy" because it's actually made of the interference of many sine waves in many "octaves." The 'size' of the noise is just the base wavelength, off which the octaves are based.

Perlin noise has a slightly different look than Simplex noise, but is hugely complex computationally, so Simplex noise is preferred.

[Perlin noise - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Perlin_noise "Wikipedia - Perlin Noise") 

#### Specific Properties

**Compute Normals Checkbox** - default unchecked.

**Use World Positions Checkbox** - default unchecked.

**Noise Amount Slider** - default 0, range 0.00 - 5.00.

**Effect X Checkbox** - default unchecked.

**Effect Y Checkbox** - default unchecked.

**Effect Z Checkbox** - default unchecked.

**Iterations Slider** - default 2, range 2 - 5.

**Noise Scale Slider** - default 1, range 0.00 - 1.00.

**Octaves Slider** - default 256, range 8 - 256.

**Phase Slider** - default 0, range 0.000 - 1.000.

**Random Seed Slider** - default 1, range 1 - 512.

<a id='simplexNoise'></a>
## Simplex Noise

Noise refers to a computer-generated pseudo-random texture to better simulate real surfaces. 

Simplex noise is a method for constructing an n-dimensional noise function comparable to Perlin noise ("classic" noise) but with fewer directional artifacts and, in higher dimensions, a lower computational overhead.

You can think of Simplex noise a bit like a wave - a 2D or 3D wave - the noise scale is the frequency, and the different amounts are the amplitude. Instead of a smooth sine wave, it's all "noisy" because it's actually made of the interference of many sine waves. The "size" of the noise is just the base wavelength.
![Simplex Noise Demonstration](/images/SimplexNoiseDemo.png)
Simplex noise has a slightly different look than Perlin noise, and is much simpler computationally, so Simplex noise is preferred.

[Simplex noise - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Simplex_noise "Wikipedia - Simplex Noise")

#### Specific Properties

**Compute Normals Checkbox** - default unchecked.

**Use World Positions Checkbox** - default unchecked.

**Noise Amount Slider** - default 0, range 0.00 - 5.00.

**Effect X Checkbox** - default unchecked.

**Effect Y Checkbox** - default unchecked.

**Effect Z Checkbox** - default unchecked.

**Iterations Slider** - default 2, range 2 - 5.

**Noise Scale Slider** - default 0.1, range 0.00 - 0.30.

**Phase Slider** - default 0, range 0.000 - 1.000.

**Random Seed Slider** - default 1, range 1 - 512.

<a id='offset'></a>
## Offset

The amount or distance by which something is out of line (Google search). Distance in meters out of line with the glyph or centering pin that an object is.

#### Specific Properties

**Offset X Slider** - default 0, range -10.00 - 10.00.

**Offset Y Slider** - default 0, range -10.00 - 10.00.

**Offset Z Slider** - default 0, range -10.00 - 10.00.

<a id='stretch'></a>
## Stretch

To make (something) wider or longer by pulling it (Merriam-Webster). 

#### Specific Properties

**Offset Y Slider** - default 0, range -10.00 - 10.00.

**Offset X Slider** - default 0, range -10.00 - 10.00.

**Effect Axis** - default X, chose X, Y, or Z.

<a id='push'></a>
## Push

In geometry, a torus (plural tori) is a surface of revolution generated by revolving a circle in three-dimensional space about an axis coplanar with the circle. (Wikipedia) An (ordinary) torus is a surface having genus one, and therefore possessing a single "hole". (Wolfram MathWorld) Or a ring, a hula hoop, or a doughnut shape. Properties that apply to tori but may not apply to other types of objects. Here you may also use buttons to delete, select, or copy the given torus.

**Active Checkbox** - default checked.

**Amount Slider** - default 0, range -1.00 - 1.00.

<a id='uvmap'></a>
## UV Map

UV mapping stands for the technique used to "wrap" a 2D image texture onto a 3D mesh. "U" and "V" are the name of the axes of a plane, since "X", "Y" and "Z" are used for the coordinates in the 3D space (https://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/UV_Map_Basics[https://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/UV_Map_Basics](https://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/UV_Map_Basics "https://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/UV_Map_Basics")).

For more information see [Materials Tutorial - Textures](http://sandboxdocs.readthedocs.org/en/latest/User%20Guide/Lights%20and%20Materials/#textures "Materials - Textures (see Note)")

#### Specific Properties

**Active Checkbox** - default checked.

**Length Slider** - default 1, range -10.00 - 10.00.

**Height Slider** - default 1, range -10.00 - 10.00.

**Mode** - default Sphere, chose Plane, Box, or Sphere.

**U Offset Slider** - default 0, range -1.00 - 1.00.

**V Offset Slider** - default 0, range -1.00 - 1.00.

**Plane Axis** - default Z, chose X, Y, or Z.

**Rotate Slider** - default 1, range -3.14159 - 3.13841.

**Tile X Slider** - default 2, range -10.00 - 10.00.

**Tile Y Slider** - default 2, range -10.00 - 10.00.

**Width Slider** - default 1, range -10.00 - 10.00.

<a id='extrude'></a>
## Extrude

Thrust or force out.

or

Shape (a material such as metal or plastic) by forcing it through a die.

**Amount Slider** - default 1, range -1.00 - 1.00.

**Axis** - default Z, chose X, Y, or Z.

**Hide Parent Line Checkbox** - default unchecked.

**Steps Slider** - default 1, range 1 - 20.

<a id='pathExtrude'></a>
## Path Extrude

Thrust or force out.

or

Shape (a material such as metal or plastic) by forcing it through a die.

#### Specific Properties

**Hide Parent Line Checkbox** - default unchecked.

**Choose Path Textbox and Choose Node Button** - a place to enter node id, default empty. You can enter the node id of a node, copy and paste a node id (i.e. from the Show ID Tool), or press the Choose Node button which turns the mouse cursor into crosshair for selecting a node in the world.

**Text Size Slider** - default 1, range 0.00 - 10.00.

<a id='lathe'></a>
## Lathe

To cut, shape, or otherwise treat on a machine for use in working wood, metal, etc., that holds the material and rotates it about a horizontal axis against a tool that shapes it (dictionary.com).

**Active Checkbox** - default checked.

**Amount Slider** - default 1, range -1.00 - 1.00.

**Steps Slider** - default 10, range 1 - 20.
