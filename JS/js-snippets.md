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
