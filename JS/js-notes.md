# Javascript Notes

## Template Literal
```
//template string for string concatenation (backtracks are important!)

function greet(name) {
  return `Hi ${name}`;
}

//template string for objects

var data = { a: 1, b: 2, c: 3 }
console.log(`Show object: ${JSON.stringify(data)}`);
```
<br>

## Shortcut Conditionals
- AND operator (&&)
```
// instead of
if (doorOpen) {
  console.log('It's open!');
}

// use
doorOpen && console.log('It's open!);
```
<br>

- OR operator (||)
```
// instead of
if (price.data) {
  return price.data;
} else {
  return 'Getting price...';
}

// use
return (price.data || 'Getting the price')
```

## Arrow Function (ES6)
```
// instead of
function user(first_name, last_name) {
  return 'Hi ' + first_name + ' ' + last_name;
}

// use (using template string)
const user = (first_name, last_name) => {
  return `Hi ${first_name} ${last_name}`;
}
```
<br>

## Dom selector (click event)
```
$(e.currentTarget).attr('data-id'); //es6

$(this).attr('data-id'); //jquery
```
<br>

## Convert to Intergral (~~)
- more efficent way ro remove decimals
```
// instead of
math.round(math.random*50)

// use
~~(math.round.random*50)
```
<br>

## Resize or Empty an Array
```
var array = [1, 2, 3, 4, 5]
console.log(array.length) // returns 5

array.length = 0 // empty array
console.log(array.length) // returns 0
```
<br>

## Storing Classes/Ids in an Object
- easier to keep track of  classes and selectors
```
var selectors = {
  someSelector1: '.some-selector-1',
}

var classes = {
  someClass1: 'some-class-1'
}

$(selectors.someSelector1).val() // jQuery
$(div).addClass('classes.someClass1') // jQuery
```
<br>
