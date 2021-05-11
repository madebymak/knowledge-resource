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
