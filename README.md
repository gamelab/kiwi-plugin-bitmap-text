# BitmapText Plugin

> Version: 1.2.0
> Type: GameObject Plugin
> Author: Kiwi.js Team
> Website: www.kiwijs.org
> Kiwi.js Version Last Tested: 1.4.0

## Versions

### 1.2
	- Updated for KiwiJS series 1.x
	- WebGL and Canvas both support full game object transformation
	- Added sharp text rendering for proper retro crispness
	- Added `smooth` property to remove sharpness
	- Leading spaces are removed from lines to preserve left-alignment

### 1.1
	- Refactored some of the code.
	- A more optimised rendering in WebGL.
	- Implemented basic text alignment. Some updates are needed.
	- Updated WebGL portion for 0.7.0 of Kiwi.JS. Note will not work in WebGL for previous version of Kiwi.JS.

### 1.0.2
	- Updated to work with Kiwi 0.6.0. Note: that this means it won't work with 0.5.3 of Kiwi.js
	- A READ ONLY `width` property has been added to return the "width" of the bitmap text.
	- Now renders in WEBGL using the TextureAtlasRenderer.
	- New 'remap' methods have been added allowing an easy way to map cells to characters.

### 1.0.1
	- Text no longer 'breaks'/wrap's mid word anymore.
	- More Documentation added to the plugin and to the README.md.
	- Text parameter no longer required to be passed upon instatiation.
	- A 'defaultCell' now exists. This cell is the 'default' cell that will be used when one could not be found.
	- Words which would be longer than a single line now 'break/wrap' when a maxWidth is set.

### 1.0
	- Initial GameObject created
	- Single line text support
	- Multiline text supported in a basic sense
	- Renders to Canvas

## Description

This [KiwiJS](http://www.kiwijs.org) plugin creates bitmap text objects. Bitmap text uses sprites to represent letters, instead of vector font information. This is useful for retro text styles.

## How to Include

Copy either `bitmap-text-x.x.x.js` or `bitmap-text-x.x.x.min.js` from `src/` to your project directory. We advise you create a `plugins/` folder for better filekeeping, but this is not required.

Link this file in your HTML after loading the KiwiJS library. For example:

```html
<script src="js/lib/kiwi.js"></script>
<script src="js/plugins/bitmap-text-x.x.x.js"></script>
<script src="js/my-game.js"></script>
```

## How to use

### Creating a new Object

The process is similar to any other game object:

```js
// Where `this` scope is the current state

var myTextField = new Kiwi.Plugins.GameObjects.BitmapText(
	this,								// State
	this.textures.textureAtlas,			// Texture atlas
	"Hello World",						// Initial text
	0, 0 );								// Position coordinates

this.addChild( myTextField );
```

Note that, unlike default `TextField` objects, you can have multiple lines of BitmapText. Just set the `maxWidth` property.

### Changing Character/Cell References

The plugin gets characters from individual cells in a texture atlas. The default index of the cell is determined by the `alphabeticalCells` property.

You can change the values of `alphabeticalCells` to remap the sequence of characters. This is useful if you have a bitmap font that is not in the expected order.

## TO DO

* Some method of kerning serifs, perhaps via hitboxes
* Maximum height
* Spacing between lines, and a better method of defining line height than just using the height of the current cell
* Parse escape characters such as `\n` and `\t`
* Different sizes of font, without scaling?
* Handle end-of-line spaces as well as leading spaces
* Get texture atlas working with WebGL; currently, only SpriteSheet seems to work as a base texture
