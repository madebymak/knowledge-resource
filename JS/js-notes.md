# Javascript Notes

## Template Literal
```
// template string for string concatenation (backticks are important!)

function greet(name) {
  return `Hi ${name}`;
}

// template string for objects

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
<br>

## Arrow Function (ES6)
```
// ES5
function user(first_name, last_name) {
  return 'Hi ' + first_name + ' ' + last_name;
}

// ES6 w/ template string
const user = (first_name, last_name) => {
  return `Hi ${first_name} ${last_name}`;
}
```
Note: works differently with jQuery

```
// jQuery click event
$button.on('click', function (e) {
    console.log($(this));
});

// ES6 click event
$button.on('click', (e) => {
    var $this = $(e.currentTarget);
    console.log($this);
});
```
<br>

## Dom selector (click event)
```
$(e.currentTarget).attr('data-id'); //es6

$(this).attr('data-id'); //jquery
```
<br>

## Convert to Intergral (~~)
- more efficient way to remove decimals
```
// instead of
math.round(math.random*50)

// use
~~(math.round.random*50)
```
<br>

## Quickly Resize or Empty an Array
```
var array = [1, 2, 3, 4, 5]
console.log(array.length) // returns 5

array.length = 0 // empty array
console.log(array.length) // returns 0
```
<br>

## Storing Classes/Ids in an Object (OOP-style)
- easier to keep track of classes and selectors
```
var selectors = {
  someSelector1: '.some-selector-1',
  ...
}

var classes = {
  someClass1: 'some-class-1',
  ...
}

$(selectors.someSelector1).val() // jQuery
$(div).addClass('classes.someClass1') // jQuery
```
<br>

## Array Map
- can be used instead of the classic `For...In` or `For...Of` loops
- use `forEach` if you're not returning something
```
const someArray = [2, 3, 4, 5, 35]
const someNewArray = someArray.map(someItem => {
    return someItem * 2
})

console.log(someNewArray) // [4, 6, 8, 10, 70]
```
<br>

## Array forEach
```
const numbers = [1, 2, 3, 4, 5];

numbers.forEach(number => console.log(number));

```
<br>

## for..of Loop (ES6)
- easier than using a for..in loop
```
let list = ['a', 'b', 'c', 'd'];

// old
for (var item in list) {
  console.log(item) // 0, 1, 2, 3
  console.log(list[item]) // a, b, c, d
}

// new
for (var item of list) {
  console.log(item) // a, b, c, d
}
```
<br>

## Conditional (ternary) Operator
```
var age = 26;

//old
if (age >= 21) {
  return 'Beer'
} else {
  return 'Juice'
}

// new
var beverage = (age >= 21) ? "Beer" : "Juice";
console.log(beverage); // "Beer"
```
<br>

## Debugger
- chrome browser will automatically stop at the point where the syntax shows up

```
if(something) {
  debugger;
}
```
<br>

## Getting Value From Object
```
const object1 = {
  a: 1,
  b: 2,
  c: 3
}

// old
const a = object1.a;
const b = object1.b;

// new
const {a , b, c} = object1
```
<br>
