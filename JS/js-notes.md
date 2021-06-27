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

// using destructuring object syntax
const { log, warn, error } = console;

log('log to browser console');
warn('log warning');
error('log error);
```
<br>

## Console Count
- count how many times a piece of code executed
```
Array.from({ length: 3}).forEach(() => { // creates array [1,2,3]
	console.count('count');
	// count: 1
	// count: 2
	// count: 3
});

console.countRest('count'); // resets count
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

## Workaround Escaping Quotes
```
// instead of
const message = 'It\'s a message';

// use template literal
const message = `It's a message`;
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

## Quick Arrow Function Return
- to quickly return an object literal in an arrow function, just wrap the object in `()`
```
// doesn't work
const formatName = (first, last) => {
  full: `${first} ${last}`,
  short: `${first.charAt(0)} ${last.charAt(0)}`.toUpperCase(),
};

// work
const formatName = (first, last) => ({
  full: ...,
  short: ...,
});

formatName('John', 'Doe');  // { full: 'John Doe', short: 'J D' }
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

const {key1, key2, key3} = obj // use the key to set the variable

// deconstruct in function
function count(object) {
	const {key1, key2, key3} = object;

	console.log(key1, key2, key3) // value1, value2, value3
}

// variable declaration rule
{ key1 } = object // Uncaught SyntaxError: Unexpected token '='

// use
let key1;
({ key1 = object});
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
- more elegant way to do promises (syntactic sugar)
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

## Spread Syntax
- denoted by three dots `...`
- commonly used to make shallow copies of objects
- easier to read and understand
```
// copy an array
const arr1 = ['h','e','l','l','o']
const copyArr = [...arr1]

console.log(copyArr) // ['h','e','l','l','o']

// insert one array into another
const list1 = ['eggs', 'bread', 'milk'];
const list2 = ['soup', 'chicken', ...list1];

console.log(list2) // ['soup', 'chicken', 'eggs', 'bread', 'milk']

// array to arguments
const multiply = (num1, num2, num3) => {
	return num1 * num2 * num3
}

let numbers = [1,2,3];

multiply(...numbers); // 6

// update properties in an object
const user = {
	'name': 'jon doe',
	'age': 28
}

const updateUser =  {...user, name: 'jim doe'};

console.log(updatedUser) // { name: 'jim doe', age: 28}
```
<br>

## Storing to Local Storage
- useful for storing data that can be used else where
- use `setItem()` to add key and value to localStorage
- use `getItem()` to retrieve item
- `removeItem()` to remove an item by key
- `clear()` to clear all localStorage
```
// save current page to localStorage
	let currentPage = window.location.pathname;
	localStorage.setItem('savePage', currentPage);

// retrieve key/value
	const prevPage = localStorage.getItem(savePage);
```
<br>

## Passing Arguements as Objects
- easier to tell what is value is being passed to which arguement
- order doesn't matter anymore
```
const createUser = ({ username, name, age, birthday }) => {
	// create user
};

createUser({
	age: 37,
	username: 'DoubleJ',
	name: 'Jim Jones',
	birthday: '1/1/1984'
});
```
<br>

## Avoid Unnecessary Variables
- don't create new variables if you don't plan on reusing later
```
// jQuery example
let user = firstName + ' ' + lastName;
$('.user-info').append(user);

// do instead
$('.user-info').append(firstName + ' ' + lastName);
```
<br>

## Object Iterations
- `Object.keys()` returns array of keys
- `Object.entries()` returns array of keys/pairs
- `Object.values()` returns array of values
```
let user = {
	name: 'Jon',
	age: 30
}

Object.keys(user); // ['name', 'age']
Object.values(user); // ['Jon', 30]
Object.entries(user); // [ ['name', 'Jon'], ['age', 30] ]
```
<br>

## Dynamic Object Keys
```
const user = {
	name: 'Jon Doe'
}

console.log(user.name) // Jon Doe
console.log(user['name']) // Jon Doe

// alternative way
obj_prop = 'name';
console.log(user[obj_prop]) // Jon Doe
```
<br>

## Filter Falsy Values
```
const arr = ['', 1, undefined, 6];
const filterArr = arr.filter(Boolean);

console.log(filterArr) // [1,6]
```
<br>

## Remove Duplicates From Array
- use built-in `Set` function to create new array without duplicates
```
const nums = [1, 2, 2, 3, 1, 2, 4, 5, 4, 2, 6];

[...new Set(nums)] // [1, 2, 3, 4, 5, 6]
```
<br>

## Selecting Elements
```
// jQuery equivalent
$('.some-class');

// JS first instance of element
document.querySelector('.some-class');

// select all elements
document.querySelectorAll('.some-class');
```
<br>

## Applying Function to Element
```
// jQuery example
$(".box").hide();

// vanilla JS hide element
document.querySelectorAll(".box").forEach((box) => {
	box.style.display = "none";
});
```
<br>

##  Traversing DOM
- selecting parent or sibling element
```
// Return the next, previous, and parent element of .box
// jQuery example
$(".box").next();
$(".box").prev();
$(".box").parent();

// vanilla JS
const box = document.querySelector(".box");

box.nextElementSibling;
box.previousElementSibling;
box.parentElement;
```
<br>

## Click Events
```
// jQuery
$('.button').on('click', function(e) {
	<!-- do something -->
});

// vanilla JS
document.querySelector('.button').addEventListener('click', (e) => {
	<!-- do something -->
});
```
<br>

## CSS Styling
```
// jQuery
$(".box").css("color", "#000");

// vanilla JS
document.querySelector(".box").style.color = "#000";

// jQuery multiple styles
$(".box").css({
  "color": "#000",
  "background-color": "red"
});

// vanilla JS
box.style.cssText = "color: #000; background-color: red";
```
<br>

## Hide/Show Element
```
// jQuery
$(".box").hide();
$(".box").show();

// vanilla JS
document.querySelector(".box").style.display = "none";
document.querySelector(".box").style.display = "block";
```
<br>

## Document Ready
```
// jQuery
$(document).ready(function() {
  /* Do something */
});

// vanilla JS
// define a callback first
const ready = (callback) => {
  if (document.readyState != "loading") {
	 callback();
	} else {
		document.addEventListener("DOMContentLoaded", callback);
	}
}

ready(() => {
  /* do something */
});
```
<br>

## Classes
- add, remove and toggle classes
```
// jQuery
$(".box").addClass("focus");
$(".box").removeClass("focus");
$(".box").toggleClass("focus");

// vanilla JS
const box = document.querySelector(".box");

box.classList.add("focus");
box.classList.remove("focus");
box.classList.toggle("focus");

// multiple classes
box.classList.add("focus", "highlighted");
box.classList.remove("focus", "highlighted");
```
<br>

## Check For Classes
```
// jQuery
if ($(".box").hasClass("focus")) {
  <!-- do something -->
}

// vanilla JS
if (document.querySelector(".box").classList.contains("focus")) {
  <!-- do something -->
}
```
<br>

## Updating DOM
```
// jQuery
$(".button").text("New text");

// vanilla JS
document.querySelector(".button").textContent = "New text";

// Return the text of the updated element
document.querySelector(".button").textContent; // Returns "New text"
```
<br>

## Add New Element to DOM
```
// jQuery
$(".container").append($("<div/>"));

// vanilla JS
const element = document.createElement("div");
document.querySelector(".container").appendChild(element);
```
<br>

## Check If an Attribute Exists
- check if an attribute with a specified name exists
- returns boolean
```
const hasAttr = element.hasAttribute(name);

console.log(hasAttr) // true or false
```
<br>

## Updating Attribute
```
// set attr
element.setAttribute(name,value);

ex:
element.setAttribute('alt','set image alt');

// remove attr
element.removeAttribute(name);

ex:
element.removeAttribute('alt');
```
<br>

## Prefix JS Naming Class
- use `js-` prefix for managing the elements in JS that don't have styles
```
<span class="js-someClass" name="userId"></span>
```
<br>

## Convert JSON To String
- use `JSON.stringify` to convert JSON to a string when exchanging data to/from a web server
```
const person = {
	firstName: 'John',
	lastName: 'Doe',
	ages: 42,
};

JSON.stringify(person);
// converts JSON object to string
{
	"firstName": "John",
	"lastName": "Doe",
	"ages": 42
}
```
<br>

## Get Current Timestamp
- either method will return in milliseconds
```
new Date().getTime();

Date.now();
```
<br>
