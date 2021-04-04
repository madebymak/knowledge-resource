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
