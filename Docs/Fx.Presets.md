Class: Fx.Elements.Preset {#FxElementsPreset}
===============================================

<big>Allows you to apply style transitions to a collection of elements, or to multiple collections of elements, using pre-defined 'presets' that choose which transitions to apply to which element of each collection.</big>

### Extends:

Fx.Elements




Fx.Elements.Preset Method: constructor {#FxElementsPreset:constructor}
------------------------------------------------------------------------

### Syntax:

	var myFx = new Fx.Elements.Preset(elements, options);

### Arguments:

1. elements - (`array`) A collection of elements or an array of collections of elements
2. options - (`object`: optional) Same options as to Fx.Elements


Fx.Elements.Preset Method: start {#FxElementsPreset:start}
------------------------------------------------------------

<big>Applies a transition.</big>

### Syntax:

myFx.start(preset, parameters)

### Arguments:

1. preset - (`mixed`) An initialised member of Fx.Presets, or an array of initialised members of Fx.Presets
2. parameters - (`mixed`: optional) Parameters as defined by the signature of the member of Fx.Preset.

### Examples: 

#### JavaScript

// Single collection of 'title' elements
var fxSingle = new Fx.Elements.Preset($$('.title'));
var highlight = new Fx.Preset(Fx.Presets.Unique,
  [{'background-color': '#eeeeee'},{'background-color': '#ffffff'}]);

// Highlight 3rd title, lowlight other titles
fxSingle.start(myHighlight, 3);

// Multiple collections of 'title' and 'content' elements
var fxMultiple = new Fx.Elements.Preset([$$('.title'), $$('.content')]);
var show = new Fx.Preset(Fx.Presets.Unique, [{opacity: 1},{opacity: 0}]);

// Highlight 3rd title, reveal 3rd contents, lowlight/hide other elements
fxMultiple.start([highlight, show], 3);


### Notes:

* If the Fx.Elements.Presets object was constructed with an array of collections of elements, the "preset" parameter must be an array, and it must be of the same length as the array passed to the constructor. In this case each preset is applied to exactly one collection.
* The parameter argument is typically an integer that identifies the element(s) of array(s) passed to the Fx.Element.Preset constructor.


Constructor: Fx.Preset {#FxPreset}
===================================

<big>Used to initialise members of the Fx.Presets hash with styles, in order to be passed to the start method of Fx.Elements.Presets.</big>


### Syntax:

var myPreset = new Fx.Preset(preset, styles);


### Arguments:

1. preset - (`object`) A member of Fx.Presets
2. styles - (`mixed`)  style object, or an array of style objects as required by member of Fx.Presets.

### Returns:

Returns: An initialised preset, ready to be passed to the start method of Fx.Elements.Preset

### Example:

#### JavaScript

// To transition font colour of elements: selected element is red, others are black
var highlight = new Fx.Preset(Fx.Presets.Unique, [{color: "#ff0000"}, {color: "#000000"}]);


Hash: Fx.Presets {#FxPresets}
==============================

<big>Used to define style transitions on a collection of elements. In the following descriptions the "selected" element is chosen by the "parameters" argument to the Fx.Elements.Preset start method: it is an integer i identifying the index of the selected element in the collection.</big>


Fx.Presets Member: All {#FxPresets:All}
----------------------------------------

<big>All elements of the collection are transitioned identically.</big>

### Syntax for initialisation:

var myPreset = new Fx.Preset(Fx.Presets.All, styles);

### Arguments:

1. styles (`object`) A style object


Fx.Presets Member: Unique {#FxPresets:Unique}
----------------------------------------------

<big>The selected element is uniquely transitioned, while all the others have the same transition applied.</big>

### Syntax for initialisation:

var myPreset = new Fx.Preset(Fx.Presets.Unique, [styleSelected, stylesDefault]);

### Arguments:

1. stylesSelected (`object`) A style object for the selected element
2. stylesDefault (`object`) A style object for the other elements


Fx.Presets Member: Solo {#FxPresets:Solo}
------------------------------------------

<big>The selected element is transitioned, while the others are not transitioned.</big>


### Syntax for initialisation:

var myPreset = new Fx.Preset(Fx.Presets.Solo, styles);


### Arguments:

1. styles (object) A style object for the selected element


Fx.Presets Member: Nothing {#FxPresets:Nothing}
------------------------------------------------

<big>Define a null transition: none of the members of the collection are transitioned</big>

### Syntax for initialisation:

Does not need to be initialised: Fx.Presets.Nothing can be used wherever an initialised preset is required


Fx.Presets Member: Arbitrary {#FxPresets:Arbitrary}
----------------------------------------------------

<big>All elements of the collection are transitioned identically, but the style is the ith style object from an array.</big>


### Syntax for initialisation:

var myPreset = new Fx.Preset(Fx.Presets.Arbitrary, styles);


### Arguments:

1. styles (`array`) An array of style objects



Fx.Presets Member: ArbitraryUnique {#FxPresets:ArbitraryUnique}
----------------------------------------------------------------

<big>The selected element is transitioned using the ith style object from an array, while the others do not transition.</big>

### Syntax for initialisation:

var myPreset = new Fx.Preset(Fx.Presets.ArbitraryUnique, styles);


### Arguments:

1. styles (`array`) An array of style objects


Fx.Presets Member: ArbitrarySolo {#FxPresets:ArbitrarySolo}
------------------------------------------------------------

<big>The selected element is transitioned using the ith style object from an array, while all the others have the same transition applied.</big>

### Syntax for initialisation:

var myPreset = new Fx.Preset(Fx.Presets.ArbitrarySolo, [stylesSelected, styleDefault]);


### Arguments:

1. stylesSelected (`array`) An array of style objects for the selected element
2. stylesDefault (`object`) A style object for the other elements


Fx.Presets Member: Grid {#FxPresets:Grid}
------------------------------------------

<big>The selected element defines a selected column and row in a grid of elements (in row major order). Selected and unselected rows and columns are transitioned by merging the supplied style objects.</big>

### Syntax for initialisation:

var myPreset = new Fx.Preset(Fx.Presets.Grid, 
  [[columnSelected, rowSelected], [columnDefault, rowDefault], [x,y]]);


### Arguments:

1. columnSelected (`object`) Style object for the selected column.
2. rowSelected (`object`) Style object for the selected row.
3. columnDefault (`object`) Style object for the other columns.
4. rowDefault (`object`) Style object for the other rows.
5. x (`number`) Number of columns.
6. y (`number`) Number of rows.