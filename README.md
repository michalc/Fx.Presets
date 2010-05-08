Fx.Presets
==========

Fx.Presets can be used to clearly define and use groups of related animations on multiple elements. For those familiar with MooTools, they can be seen as a way to manage (or preset) properties passed to the Fx.Elements::start method.

Using Fx.Presets offers two main advantages over other methods. It results in smoother animations then using multiple Fx.* instances simultaneously. It also results in nicer code than when using a single Fx.Elements instance to transition styles across different elements from multiple groups at the same time.


How to use
----------

### Basic Example

Say we have a collection of divs, 'divs'. On click of each one, we want its background to change to white, and the background of all other divs to black. Fx.Presets.Unique allows all elements in an array to be animated in the same way, with the exception of one:

	var highlight = new Fx.Preset(Fx.Presets.Unique, [
	  {'background-color': '#ffffff'},
	  {'background-color': '#000000'}
	];
	 
	var fx = new Fx.Elements.Preset(divs);
	divs.each(function(el, i) {
	  el.addEvent('click', function() {
	    fx.start(highlight,i);
	  });
	});


### More Complex Example: Combining Presets

As above, we have a collection of divs, 'divs'. On click of each one, we want its background to change to white, and the background of all other divs to black, a typical 'highlight' situation. Also, say we know there is a single 'p' element in each div, and we also want the opacity of the 'p' block in the clicked div to be 1, and 0 otherwise. The following code handles it all:

	var highlight = new Fx.Preset(Fx.Presets.Unique, [
	  {'background-color': '#ffffff'},
	  {'background-color': '#000000'}
	];
	 
	var reveal = new Fx.Preset(Fx.Presets.Unique, [
	  {opacity: 1},
	  {opacity: 0}
	];
 
	var texts = divs.getElements('p');
	var fx = new Fx.Elements.Preset([divs, texts]);
	divs.each(function(el, i) {
	  el.addEvent('click', function() {
	    fx.start([highlight, reveal],i);
	  });
	});
	

### Acting on all elements: Fx.Presets.All

We can use Fx.Presets.All to act on all elements in the same way. Continuing from the above example, say we have a link 'reset', that upon clicking we wish to fade all text to opacity 0, and all divs to black. The following code does this:

	var lowlightAll = new Fx.Preset(Fx.Presets.All, {'background-color': '#000000'});
	var fadeAll = new Fx.Preset(Fx.Presets.All, {opacity: 0});
	 
	reset.addEvent('click', function() {
	    fx.start([lowlightAll, fadeAll]);
	});



Demos
-----

[Basic and more complex demos](http://yetagain.net/plugins/fxpresets/demos/) are available.