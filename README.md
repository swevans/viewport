# ViewportConfig #

ViewportConfig is a simple, easy-to-use JavaScript and TypeScript library for accessing and manipulating HTML [viewport meta tags](http://www.w3schools.com/css/css_rwd_viewport.asp) using JavaScript. The goal is to allow you to read and write these properties on the fly without writing cumbersome logic to find the tag and access it's internals. 

## Why access this tag? ##
For starters, there are a sizeable of people on the internet [looking for javascript functionality surrounding the viewport](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=get+viewport+scale). There are also instances were you might need to scale elements or assets based on the viewport scale. 

This project was prompted by the need for [high definition canvas rendering](http://www.html5rocks.com/en/tutorials/canvas/hidpi/) when css pixels do not match device pixels. To achieve HD rendering when the html is scaled up, the canvas element must rendered in at a larger size relative to the html scale factor. If HTML is scaled up by 2, the canvas should render contents at twice the size to prevent blurring when the browser presents the scaled canvas raster.

An example:
- Device: iPad3
- Device Resolution: 2048x1536
- Viewport Scale: 1
- Pixel Ratio: 2
- Logical Resolution: 1024x768

In this instance, the device resolution is much higher than the logical resolution that the webpage is being rendered with. The webpage will effectively be rendered at half resolution and the scaled up to fit the full screen. Any canvas element within the page will be scaled up post render, which causes normally sharp graphics to blur. To compensate, we should create the canvas at twice the size and then scale it down to fit within smaller page. If the viewport was 0.5 instead of 1, the effective page resolution would be 2048x1536 (matching the device). In this case, we do not want to create an oversized canvas and thus need to know what the viewport scale is.

Don't worry if this is over your head. It is just one use case.

## Usage ##
Include viewport-config-vX.X.js in your JavaScript bundle or add it to your HTML page like this.

```html
<script type='application/javascript' src='/path/to/viewport-config-1.0.js'></script>
```
The script must be loaded prior to using it within your code. ViewportConfig follows a static interface and exists in a the "swevans" namespace, and thus does not need to be instantiated. Use the class directly to get / set viewport tag content properties:

```js
// Getting the initial-scale value
var theInitialViewportScale = swevans.ViewportConfig.initialScale;

// Setting the initial-scale value to some value
// note this will change the scale on all supporting browsers
swevans.ViewportConfig.initialScale = 5.1;

// Clearing a property by setting to null
swevans.ViewportConfig.initialScale = null;
```

Note that if no viewport tag is included in the page, one will be created when a property is set via ViewportConfig. If multiple viewport meta tags exist, the one appearing last in the document will be used by ViewportConfig.

### The API ###
ViewportConfig provides getters and setters for the following viewport tag content properties:
```js
// NOTE: all numerical values are rounded to 4 decimal places
// NOTE: setting any property to null will remove it from the tag

// gets and sets the initial-scale property as a number
swevans.ViewportConfig.initialScale;

// gets and sets the minimum-scale property as a number
swevans.ViewportConfig.minimumScale;

// gets and sets the maximum-scale property as a number
swevans.ViewportConfig.maximumScale;

// gets and sets the user-scalable property as a boolean
// false=no, true=yes
swevans.ViewportConfig.userScalable;

// gets and sets the width property as a string
swevans.ViewportConfig.width;

// gets and sets the height property as a string
swevans.ViewportConfig.height;

// gets and sets the target-densitydpi property as a string
swevans.ViewportConfig.targetDensityDPI;

// gets the current device pixel ratio, 1 if undefined
swevans.ViewportConfig.pixelRatioScale;

// a bool indicating if the ViewportConfig tag is supported
// false means that the tag is ignored or not required
swevans.ViewportConfig.isSupported;

// A helper function to update the viewport initial scale such 
// that css pixels will match hardward pixels in 1:1 ratio.
swevans.ViewportConfig.matchDevice();
```





NAUT Games - Demos
=====

This repository contains source files for technical demonstrations published by NAUT games. 

##About the Demos
You can find information about the demos detailed in the github project wiki @ https://github.com/naut-games/demos/wiki. A brief overview of the demos is listed below.

### Camera for 2D Scenes with Parallax
_Location: Demos/Camera2D_<br/>
_Language: AS3_<br/>
_Project Types: FlashDevelop, Flash IDE_<br/>
_Live Demo: [Camera2D Demo](http://tech.nautgames.com/demos/camera2d/)_<br/>
This demonstration shows off a simple camera class for easily transforming 2 dimensional scenes. The camera class features position, rotation, zoom, and parallax capabilities. The class is relatively efficient and suitable for real time games. We've used it in side on and top down scrolling games.

### Weak Referencing Objects
_Location: Demos/WeakReference_<br/>
_Language: AS3_<br/>
_Project Types: FlashDevelop, Flash IDE_<br/>
This demonstration contains a utility class for creating weak references to objects. The weak reference instance itself is a lightweight wrapper for the built in Dictionary class. When the flash player mark and sweep garbage collector runs, the object being weakly referenced will be marked and collected if only weak references are pointing to it. WeakReferences should be used sparingly. We've effectively used them in caching and object pooling.

### Random Number Generator
_Location: Demos/Random_<br/>
_Language: AS3_<br/>
_Project Types: FlashDevelop, Flash IDE_<br/>
This demonstration contains a seedable psuedo Random Number Generator (RNG) implemented using a Linear Congruential Generator (LCG) algorithm. This RNG is not suitable for encryption / security or generating large volumes of noise in real time. This generator does have many practical applications listed in the Random.as class header.

### Neural Network
_Location: Demos/NeuralNet_<br/>
_Language: AS3_<br/>
_Project Types: FlashDevelop, Flash IDE_<br/>
This demonstration contains a basic 3 layer feed-forward neural network that is trained via sigmoid function based back-propagation. A neural network of this type is suitable for most simple applications and specifically for games.

## Questions, Comments, Feature Requests...
Please email spencer@nautgames.com!

## Changelog
#### Updated: 2014-12-22
 * Added parallax capabilities to the Camera2D demo
 * Added the Camera2D tech demo

#### Updated: 2014-12-18
 * Added the WeakReference tech demo

#### Updated: 2014-08-09
 * Added the Random tech demo

#### Updated: 2014-08-08
 * Added the NeuralNet tech demo
