# Collection of JS Snippets

## Make Carsousel Cards Same Height
- useful for making carousel cards the same height
```
// using jQuery
var $slickSlide = $('.slick-slide');
var maxHeight = 0;

// loop through and find the tallest slide
$slickSlide.each(function(e) {
	if (maxHeight < $(this).outerHeight()) {
		maxHeight = $(this).outerHeight();
	}
});

// set all slides to same height
$slickSlide.each(function (e) {
	$(this).height(maxHeight);
})
```
<br>

## Decapitalize String
```
const decapitalize = str => `${str.charAt(0).toLowerCase()}${str.slice(1)}`;

decapitalize('HeLLo WorlD');    // 'hello world'
```
<br>

## Get Path From URL
```
const urlPath = url => url.substring(url.lastIndexOf('/') + 1);

urlPath('http://domain.com/path/to/document');     // 'document'
```
<br>

## Truncate Long String
```
const truncateString = (str, maxLimit, suffix) => {
	return (
		str.length < maxLimit ? str : `${str.substr(0, str.substr(0, maxLimit - suffix.length).lastIndexOf(' '))}${suffix}`
	)
}

console.log(truncateString('This is a long message', 20, '...')); // This is a long...
```
<br>

## Scroll To Top
- usually attach to click event
```
const goToTop = () => window.scrollTo(0, 0);

goToTop();
```
<br>

## Emulate Dice Throw
- randomly selects a number between 1 and 6
```
const throwdice = () => ~~(Math.random() * 6) + 1;

throwdice();    // 4
```
<br>

## Check If Date With Min and Max
```
// `min`, `max` and `date` are `Date` instances
const isBetween = (date, min, max) => (date.getTime() >= min.getTime() && date.getTime() <= max.getTime());
```
<br>

## Toggle Password Visibility
```
<input type="password" id="password" />

<!-- button to show/hide password -->
<button id="toggle">Toggle</button>

<script>
	const passwordEle = document.getElementById('password');
	const toggleEle = document.getElementById('toggle');

	toggleEle.addEventListener('click', function() {
		const type = passwordEle.getAttribute('type');

		passwordEle.setAttribute(
				'type',
				// Switch it to a text field if it's a password field
				// currently, and vice versa
				type === 'password' ? 'text' : 'password'
		);
	});
</script>
```
<br>

## Character Counter
```
<textarea maxlength="200" id="message"></textarea>
<div id="counter"></div>

<script>
const messageEle = document.getElementById('message');
const counterEle = document.getElementById('counter');

messageEle.addEventListener('input', function(e) {
	const target = e.target;
	const maxLength = target.getAttribute('maxlength');

	// Count the current number of characters
	const currentLength = target.value.length;

	counterEle.innerHTML = `${currentLength}/${maxLength}`;
});
</script>
```
<br>

## Replace Broken Images
```
// find all image tags on page
const images = document.querySelectorAll('img');

// loop over them and replace with custom image
[].forEach.call(images, function(ele) {
	ele.addEventListener('error', function(e) {
		e.target.src = '/path/to/404/image.png';
	});
});
```
<br>

## Detect Mobile Browsers
- better than checking screen width
```
// check if the browser supports the pointer:coarse media query
const isMobile = function() {
	const match = window.matchMedia('(pointer:coarse)');
	return (match && match.matches);
};
```
<br>

## Disable Body Scrolling on Modal
```
// disable scrolling on the `body` element when opening a modal
document.body.style.overflow = 'hidden';

// allow to scroll when closing the modal
document.body.style.removeProperty('overflow')
```
<br>

## Detect Click Event Outside Element
```
document.addEventListener('click', function(evt) {
	const isClickedOutside = !ele.contains(evt.target);

	console.log(isClickedOutside) // is true if the clicked target is outside of element
});
```
<br>

## Edit Input Field
- clicking the edit button will focus on the text field and move the cursor to the end of it
```
<input type="text" id="fullName" />

<button id="edit">Edit</button>

<script>
	const fullNameEle = document.getElementById('fullName');
	const editEle = document.getElementById('edit');

	editEle.addEventListener('click', function(e) {
		// focus on the full name element
		fullNameEle.focus();

		// move the cursor to the end
		const length = fullNameEle.value.length;
		fullNameEle.setSelectionRange(length, length);
	});
</script>
```
<br>

## Detect MacOS
- edge case if you ever need to check for Mac related bugs
```
const isMacBrowser = /Mac|iPod|iPhone|iPad/.test(navigator.platform);

console.log(isMacBrowser);
```
<br>

## Detect Internet Explorer Browser
```
const isIe = function() {
    const ua = window.navigator.userAgent;
    return ua.indexOf('MSIE') > -1 || ua.indexOf('Trident') > -1;
};

console.log(isIe);
```
<br>

## Clear Cookies
```
const clearCookies = document.cookie.split(';').forEach(c => document.cookie = c.replace(/^ +/, '').replace(/=.*/, `=;expires=${new Date().toUTCString()};path=/`));
```
<br>

## Sort Object By Properties
```
const sort = (obj) => {
	Object.keys(obj).sort().reduce((p,c) => (p[c] = obj[c], p), {});
}

// ex:
const colors = {
	white: '#ffffff',
	black: '#000000',
	red: '#ff0000',
	green: '#008000',
	blue: '#0000ff',
};

sort(colors);

// output
{
	black: '#000000',
	blue: '#0000ff',
	green: '#008000',
	red: '#ff0000',
	white: '#ffffff'
}
*/
```
<br>
