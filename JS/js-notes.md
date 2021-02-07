# Javascript Notes

## Shortcut console.log()
- use curly braces to return name values
```
let x = 1
let y = 2
let z = 3

// old
console.log('x:', x, 'y:', y, 'z:', z);

// new
console.log({x, y, z}) // x:1, y:2, z:3

// won't work with nested variables
let x = {
	a: 1,
	b: 2
}

console.log({ x.a }) // error
```
<br>

## Template Literal
- use template string for string concatenation (backticks are important!)

```
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

// short hand single argument
const user = first_name => console.log(`Hi ${first_name}`);
```
Note: keyword (`this`) works differently with jQuery

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

numbers.forEach(number => console.log(number)); // 1,2,3,4,5

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

## Array/Object Destructing
```
// old
let array = [1,2,3];
let value1 = array[0]
let value2 = array[1]
let value3 = array[2]

// new
const { value1, value2, value3 } = array

// you can do the same with objects
let object = {
	key1: value1,
	key2: value2,
	key3: value3
}

const {key1, key2, key3} = obj

// deconstruct in function
function count(object) {
	const {key1, key2, key3} = object;

	console.log(key1, key2, key3) // value1, value2, value3
}
```
<br>

## Access Nested Objects
```
const user = {
  firstName: "John",
  lastName: "Doe",
  family: {
    sister: {
      firstName: "Jane",
    },
  },
};

const { firstName } = user.family.sister;

console.log(firstName); // Jane
```
<br>

## Get First Element of an Array
```
const arr = [1,2,3,4,5]
const firstElement = arr.shift();

console.log(firstElement) // 1
```
<br>

## Find in Array
- use to find/return a single value
- returns `undefined` if not found
```
const data = {
	'name': 'Jon',
	'name': 'Bob',
	'name': 'Dave'
}

const findBob = data.find(item => item.name == 'Bob');
console.log(findBob) // true

const findJim = data.find(item => item.name == 'Jim')'
console.log(findBob) // undefined
```


## Filter Array
- use when you need to find/return multiple values
```
const numberArr = [1,2,3,4,5,6,7,8,9,10];

const under6 = numberArr.filter((val, index, array) => {
	return val < 6;
});

console.log(under6); // 1,2,3,4,5
```
<br>

## Includes
- checks if a value already exists in an array
```
const groceryList = ['eggs', 'milk', 'bread', 'mushrooms', 'pasta'];
const alreadyAdded = groceryList.includes('bread');

console.log(alreadyAdded) // true
```
<br>

## Asynchronous AJAX calls
- use `.done()` to pause code until AJAX call is finished
- use `.catch()` for error handling
```
const getData = () => {
	// AJAX call
};

getData()
	.done((response) => {
		// do something
	})
	.catch(()) => console.log(error));
```
<br>

## Async/Await
- more elegant way to do API calls
- `async` always returns a promise
- `await` makes code wait until promise is finished (can only be used with
`async`)
- use `try...catch` for error handling

```
const apiUrl = '' // api url

const fetchData = async () => {
	try {
		const resp = await fetch(apiUrl);
		const data = resp.json();
	} catch (error) {
		console.log({error});
	}
}

console.log(fetchData());

// can use with .then() method
fetchData().then((response) => {console.log({response})})
```
<br>