# CSS notes

## CSS Naming Guide
```
<container description name>__<parent group name>--<descriptive name>

ex:
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

## Avoid !importany Tag
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
