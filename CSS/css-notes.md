# CSS notes

## CSS Naming Guide
```
<container description name>__<parent group name>--<descriptive name>
```
<br>

Example:
```
<div class='box'>
  <div class='box__header'>
    <label class='box__header--title'></label>
    <label class='box__header--subtitle'></label>
  </div>
  <div class='box__content'>
    <label class='box__content--title'></label>
    <label class='box__content--subtitle'></label>
  </div>
</div>
```
<br>

## Avoid Using !important Tag
- the tag has the highest specificity of all CSS selectors
- only way to override an important tag is to use another important tag
```
.some-class {
	color: white;
}

// will make color red always
.some-class {
	color: red !important;
}
```
<br>

## Use Shorthands
```
// bad
.article-container {
  padding-top: 10px;
  padding-bottom: 20px;
  padding-left: 15px;
  padding-right: 15px;
}

// good
.article-container {
  padding: 10px 15px 20px 15px;
}

```
<br>

## CSS Variables (Non-Preprocessors)
- set variables by giving them a name preceded by two dashes
- global variables are defined in the `:root` element
- use variables with `var()`
```
:root {
  --main-bg-color: coral;
  --main-txt-color: #fff;
  --main-padding: 15px;
}

#div1 {
  background-color: var(--main-bg-color);
  color: var(--main-txt-color);
  padding: var(--main-padding);
}
```
<br>

## CSS Spinner
- pure CSS spinner
- easier to use icon (ex: font awesome) if possible
```
// html
<div class="spinner"></div>

// CSS
.spinner {
    animation: spin 1.5s linear infinite;
    border: 5px solid #EEE;
    border-left-color: #00BCD4;
    border-radius: 50%;
    display: inline-block;
    height: 30px;
    width: 30px;
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
```
<br>

## Font Face Browser Support
- custom fonts support across different browsers
- be sure to include WOFF or WOFF2 version (TTF or OTF are not webfont file types)

```
@font-face {
  font-family: 'MyWebFont';
  src: url('webfont.eot'); /* IE9 Compat Modes */
  src: url('webfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
       url('webfont.woff2') format('woff2'), /* Super Modern Browsers */
       url('webfont.woff') format('woff'), /* Pretty Modern Browsers */
       url('webfont.ttf')  format('truetype'), /* Safari, Android, iOS */
       url('webfont.svg#svgFontName') format('svg'); /* Legacy iOS */
}
```
<br>

## Hiding Elements
```
// element is hidden and won't take up space
.class1 {
	display: none;
}

// element is hidden but will still take up space
.class2 {
	visibility: hidden
}

```
<br>

## Box-Sizing
- changes the way width gets calculated
```
// adds padding and border to width of the child element
.class1 {
	padding: 25px;
	width: 100%;
	border: 5px solid #FFF;
	box-sizing: content-box;
}

// padding and width are included in the width of the child element
.class2 {
	box-sizing: border-box;
}
```
<br>

## Combinator Selectors

```
// elements that have both classes (chained classes)
.nav-item.selected {
	color: #fff;
}

// select matching elements inside parent (descendant selector)
.container img {
	border: 2px solid;
}

// only direct descendant of parent
.nav > li {
	padding: 10px;
}

// select first element next to former element (adjacent sibling selector)
.list-item + .list-item {
	color: #FFF;
}
```
<br>

## Centering Using Flexbox
```
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```
<br>

## CSS Arrows
```
.arrow {
  border: solid black;
  border-width: 0 3px 3px 0;
  display: inline-block;
  padding: 3px;
}

.right {
  transform: rotate(-45deg);
  -webkit-transform: rotate(-45deg);
}

.left {
  transform: rotate(135deg);
  -webkit-transform: rotate(135deg);
}

.up {
  transform: rotate(-135deg);
  -webkit-transform: rotate(-135deg);
}

.down {
  transform: rotate(45deg);
  -webkit-transform: rotate(45deg);
}
```
<br>

## Flexbox Wrap
- useful for getting child elements to stack nicely on mobile view
```
<div class="parent">
	<button class="child">Button 1</button>
	<button class="child">Button 2</button>
	<button class="child">Button 3</div>
</div>

// CSS
.parent {
	display: flex;
	flex-wrap: wrap;
	width: 300px;
}
```
<br>

## Disable Hover on Touch Devices
- use JS to check
```
	<script>
		var isTouch = 'ontouchstart' in window;

		// adds class to HTML container
		document.documentElement.className += isTouch?' touch ':' no-touch ';
	</script>

	<style>
		.no-touch .hover-class {
			// hover effect on non touch devices
		}
	</style>
```
<br>

## REM Sizing
- can be used for any type of size measurements (font, width, height, etc)
- uses the root HTML element as the relative size
- best to use percentage when setting the root size
- ex: default font size is usually 16px so if we set the body font-size to 62.5% then 1rem will equal 10px

```
Ex: default font size is usually 16px so if we set the body font-size to 62.5% then 1rem will equal 10px

body {
	font-size: 62.5%; // 10px
}

p {
	font-size: 1.2rem // sets p tag size to 12px
}
```
<br>

## Text Shortening w/ Dots
- cut off text with 3 dots if to wide for parent div
```
.text-box {
	max-width: 150px;
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;
}
```
<br>

## Position Sticky
- `postion: sticky` won't work if parent/ancestor has `overflow` properties

<br>

## Soft Background Color
- consistent colors on any background
- use rgba with opacity and a pseudo class
```
.circle {
	position: relative;
	color: #8F44FD;
	background: rgba(143, 68, 253, 0.1);
	width: 100px;
	text-align: center;
	border: 1px solid;
	padding: 10px 0;
	border-radius: 10px;
}

// pseudo class
.circle:before {
	content: '';
	position: absolute;
	z-index: -1;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}
```
<br>

## Stop Image From Stretching
- use `object-fit: cover` to stop image stretching
```
img {
	width: 100%;
	height: 100%;
	object-fit: cover
}
```
<br>

## Media Queries
```
@media screen and (min-width: 300px) {
	// do something
}

// min and max range
@media screen and (min-width: 300px) and (max-width: 1400px) {
	// do something
}