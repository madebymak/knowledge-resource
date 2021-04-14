# jQuery Notes

## Toggle
- use `toggleClass()` to add/remove classes
- use `toggle()` to show/hide elements
```
// HTML
<div class="some-class"> Example text </div>

// CSS
.add-red {
	color: red;
}

// JS
$('some-class').on('click', function() {
	$(this).toggleClass('add-red); // add/removes red on click
}
```
<br>

## Show/Hide
```
<div class="class">
	// some content
</div>

// CSS
.class {
	display: none;
}

// jQuery
$('.class').show();
```
<br>

## Ajax Call
```
// POST
$.post('url', {
	// data
})
.done(function () {
	console.log("success");
})
.fail(function () {
	console.log("error");
});
```
<br>

## Combine Click & Touch Events
- bind touch and click events together
```
var clickEvent = (function() {
	if ('ontouchstart' in document.documentElement === true) {
		return 'touchstart';
	} else {
		return 'click';
	}
})();

$('.some-element).on(clickEvent, function() {
	// do something
});
```
<br>

## Using Arrow Function Syntax
```
// normal jQuery
$button.on('click', function (e) {
    console.log($(this));
});

// using arrow function
$button.on('click', (e) => {
    var $this = $(e.currentTarget);
    console.log($this);
});
```
<br>

## Get Siblings
- return all sibling elements of a selector
```
// HTML
	<ul>
		<li class="start">1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
	</ul>

// jQuery
	const siblingVal = $("start").siblings().val();

	console.log(siblingVal) // 2,3,4
```
