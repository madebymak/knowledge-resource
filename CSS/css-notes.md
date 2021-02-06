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

## Avoid !important Tag
- the tag has the highest specificity of all CSS selectors
- only way to override an important tag is to use another important tag

<br>

## Use Shorthands
```
// bad
.article-container {
  padding-top: 10px;
  padding-bottom: 20px;
  padding-left: 15px;
  padding-right: 15px;
  margin-top: 10px;
  margin-bottom: 10px;
  margin-left: 15px;
  margin-right: 15px;
  border-width: 1px;
  border-style: solid:
  border-color: black;
}

// good
.article-container {
  padding: 10px 15px 20px 15px;
  margin: 10px 15px;
  border: 1px solid black;
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
class1 {
	display: none;
}

// element is hidden but will still take up space
class2 {
	visibility: hidden
}

```
<br>

## Box-Sizing
- changes the way width gets calculated
```
// adds padding and border to width of the child element
class1 {
	padding: 25px;
	width: 100%;
	border: 5px solid #FFF;
	box-sizing: content-box;
}

// padding and width are included in the width of the child element
class2 {
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
