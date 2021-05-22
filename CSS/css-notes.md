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

## Centering Using Absolute Position
```
.parent {
	position: relative;
}

.child {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
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

## Fit Image in Container
- use `object-fit: contain` to fit the entire image within the container
- use `object-fit: cover` to fill the container with the image
- use `object-position: center` to position the image at the center of the container
```
.image-contain {
  object-fit: contain;
  object-position: center;
}

.image-cover {
  object-fit: cover;
  object-position: right top;
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
```
<br>

## Grayscale Filter
- converts image to grayscale
```
img {
	filter: grayscale(100%);
	transition: filter 0.5
}

// show full color on hover
img:hover {
	filter: grayscale(0;
}
```
<br>

## Nth-Child Selectors
- used to target specfic child elements within the same parent element
```
// change color of 2nd p element
p:nth-child(2) {
	color: red;
}

// change color of all odd child elements
p:nth-child(odd) {
	color: red;
}

// change color of all even child elements
p:nth-child(even) {
	color: red;
}

// change color of first child
p:last-child {
	color: red;
}

// change color of last child
p:last-child {
	color: red;
}

// change color if there's only one child
p:only-child {
	color: red;
}
```
<br>


## Pure CSS Checkbox
- custom styled checkbox
```
// HTML
<div class="checkbox">
    <input type="checkbox" id="checkbox_1">
    <label for="checkbox_1">Pure CSS Checkbox</label>
</div>

<style>
	body {
			line-height: 24px;
			font-size: 16px;
			box-sizing: border-box;
	}

	.checkbox input[type="checkbox"] {
			opacity: 0;
	}

	.checkbox label {
			position: relative;
			display: inline-block;

			/*16px width of fake checkbox + 6px distance between fake checkbox and text*/
			padding-left: 22px;
	}

	.checkbox label::before,
	.checkbox label::after {
			position: absolute;
			content: "";

			/*Needed for the line-height to take effect*/
			display: inline-block;
	}

	/*Outer box of the fake checkbox*/
	.checkbox label::before{
			height: 16px;
			width: 16px;

			border: 1px solid;
			left: 0px;

			/*(24px line-height - 16px height of fake checkbox) / 2 - 1px for the border
			*to vertically center it.
			*/
			top: 3px;
	}

	/*Checkmark of the fake checkbox*/
	.checkbox label::after {
			height: 5px;
			width: 9px;
			border-left: 2px solid;
			border-bottom: 2px solid;

			transform: rotate(-45deg);

			left: 4px;
			top: 7px;
	}

	/*Hide the checkmark by default*/
	.checkbox input[type="checkbox"] + label::after {
			content: none;
	}

	/*Unhide on the checked state*/
	.checkbox input[type="checkbox"]:checked + label::after {
			content: "";
	}

	/*Adding focus styles on the outer-box of the fake checkbox*/
	.checkbox input[type="checkbox"]:focus + label::before {
			outline: rgb(59, 153, 252) auto 5px;
	}
</style>
```
<br>

## Evenly Spacing Children in Parent
- use flexbox to spread out children in parent div
```
// HTML
<div class="parent">
  <p>Item1</p>
  <p>Item2</p>
  <p>Item3</p>
</div>

<style>
	.parent{
		display: flex;
		justify-content: space-between;
	}
</style>
```
<br>

## CSS Triangles
```
.triangle-up {
	width: 0;
	height: 0;
	border-left: 5px solid transparent;
	border-right: 5px solid transparent;
	border-bottom: 5px solid #000;
}
```
<br>

## Clamp
- used to set value between an upper and lower limit
```
 // clamp(MIN, VAL, MAX)

.some-class {
	font-size: clamp(14px, 1.8vw, 24px);
	line-height: clamp(14px, 1.8vw, 29px);
}
 ```
 <br>

## Lazy Loading
- most browsers will now wait to load images until they are visible in the view point with lazy loading
- note: this will affect layout so set the size of the image box using height and width
```
<img loading="lazy" style="height: 200px; width: 300px;">
```
<br>

## Same Height Columns
- create column layout with the same height
```
// HTML
<div class="container">
	<div class="column">
		<div class="content">
			// content
		</div>
	</div>

	<div class="column">
		<div class="content">
			// content
		</div>
	</div>
</div>

<style>
	.container {
		display: flex;
	}

	.column {
		flex: 1;
		margin: 0 10px //space between columns

		// layout of each column
		display: flex;
		flex-direction: column
	}

	.content {
		flex: 1; // matches height with sibling
	}
</style>
```
<br>

## Full Background Container
- use image as background in div element
```
<div class="container">
	// content
</div>

<style>
	.container {
		background: url('<image path');
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;

		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;

		height: 100vh;
		width: auto;
	}
</style>
```
<br>

## Cookie Banner
- bottom popup for cookie notfication
```
<div class="banner">
	<div class="banner__content">
		// content
	</div>
</div>

<style>
	.banner {
		display: flex;
		align-items: center;
		justify-content: center;

		position: fixed;
		bottom: 0;
		left: 0;
		width: 100%;
	}

	.banner__content {
		flex: 1;
	}
</style>
```
<br>


## Play Button Overlay
```
<div class="container">
	<!-- The video element -->
	<video src="..." />

	<!-- The overlay area -->
	<div class="container__overlay">
			<!-- The player button -->
			...
	</div>
</div>

<style>
	.container {
		position: relative;
	}

	.container__overlay {
		display: flex;
		align-items: center;
		justify-content: center;

		position: absolute;
		left: 0;
		top: 0;

		height: 100%;
		width: 100%;

		background-color: rgba(0, 0, 0, 0.25);
	}
</style>
```
<br>

## FAQ Accordian
```
<div class="container">
	<div class="container__heading">
		<!-- Question -->
		...
		<!-- The toggle icon sticks to the right -->
		...
	</div>

	<!-- Answer -->
</div>

<style>
	.container {
			border-bottom: 1px solid rgba(0, 0, 0, 0.3);
	}

	.container__heading {
			display: flex;
			justify-content: space-between;
			align-items: center;
	}
</style>
```
<br>

## Rating Stars
```
// uses font awesome icons
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">

<div class="rating">
  <span class="fa fa-star checked"></span>
  <span class="fa fa-star checked"></span>
  <span class="fa fa-star"></span>
  <span class="fa fa-star"></span>
  <span class="fa fa-star"></span>
</div>

<style>
	.rating {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: row-reverse;
		font-size: 20px;
	}

	.fa-star {
		color: yellow;
		margin: 0 5px;
	}

	.checked {
		color: gray;
	}
</style>
```
<br>

## Qty Stepper
```
<div class="stepper">
	<button class="stepper__button">-</button>
	<div class="stepper__content">
		<input type="text" class="stepper__input" />
	</div>
	<button class="stepper__button">+</button>
</div>

<style>
	.stepper {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 128px;
	}

	.stepper__button {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 32px;
	}

	.stepper__content {
		flex: 1;
	}

	.stepper__input {
		height: 100%;
		width: 100%;
		text-align: center;
	}
</style>

<script>
	// use JS to change input qty value
</script>
```
<br>

## Sticky Header
```
<div>
	<header class="header">
		// header content
	</header>
	<body>
		// body content
	</body>
</div>

<style>
	.header {
		position: sticky;
		top: 0;
	}
</style>
```
<br>

## Pricing Table
```
<div class="container">
	<div class="container__column">
		<div class="title">Option 1</div>
		<div class="price">$99.99</div>
		<div class="description">Option Package</div>
		<button>Add To Cart</button>
	</div>
	<!-- Repeat columns as needed -->
</div>

<style>
	.container {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.container__column {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		flex: 1;
		margin: 0 8px;
		border: 1px solid rgba(0, 0, 0, 0.3);
		border-radius: 4px;
		max-width: 300px;
	}
</style>
```
<br>

## Faded Long Text
```
<div class="container"
    <div class="container__content">
      <!-- insert long text -->
    </div>

    <!-- The faded overlay at bottom -->
    <div class="container__fading"></div>
</div>

<style>
	.container {
		position: relative;
	}

	.container__content {
		height: 200px;
		width: 330px;
		overflow-y: scroll;
	}

	.container__fading {
		position: absolute;
		bottom: 0;
		left: 0;
		height: 30px;
		width: 100%;
		background: linear-gradient(rgba(255, 255, 255, 0.01), #fff);
	}
</style>
```
<br>

## Avatar Circle
```
<div class="avatar">
	<img class="avatar__image" src="" />
</div>

<style>
	.avatar {
		border-radius: 50%;
		height: 64px;
		width: 64px;
	}

	.avatar__image {
		border-radius: 50%;
		height: 100%;
		width: 100%;
	}
</style>
```
<br>

## Step Wizard
- useful to step progress
```
<div class="wizard">
  <div class="wizard__step">
		<div class="wizard__dot">
			<div class="wizard__connector"></div
			<div class="wizard__number">1</div>
		</div>
	</div>

	<div class="wizard__step">
		<div class="wizard__dot">
			<div class="wizard__connector"></div>
				<div class="wizard__number">2</div>
				<div class="wizard__connector"></div>
		</div>
	</div>

	<div class="wizard__step">
		<div class="wizard__dot">
			<div class="wizard__number">3</div>
			<div class="wizard__connector"></div>
		</div>
	</div>
</div>

<style>
	.wizard {
		display: flex;
	}

	.wizard__step {
		flex: 1;
	}

	.wizard__dot {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.wizard__connector {
		flex: 1;
		height: 1px;
		background-color: rgba(0, 0, 0, .3);
	}

	.wizard__step:first-child .wizard__connector,
	.wizard__step:last-child .wizard__connector {
		background-color: transparent;
	}

	.wizard__number {
		display: flex;
		justify-content: center;
		align-items: center;

		background-color: rgba(0, 0, 0, .3);
		border-radius: 9999px;
		height: 32px;
		width: 32px;

		margin-left: 4px;
		margin-right: 4px;
	}
</style>
```
<br>
