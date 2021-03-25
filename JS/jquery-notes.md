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
