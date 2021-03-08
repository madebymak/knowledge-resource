# SCSS Notes

## Extend Class
- use `@extend` to inherit properties from a defined class
- use `%` to define class
```
// set predefined class
%header-class {
	font-size: 22px;
	font-weight: bold;
}

.heading-class {
	@extend %header-class;
	// extra CSS properties
}

```
<br>

## Mixins
- allows you copy all the properties of a class to another
- use `@include` to copy to another class
- cannot add extra properties like with `@extend`
```
@mixin heading-font {
	font-family: sans-serif;
	font-weight: bold;
}

h1 {
	@include heading-font
}

h2 {
	@include heading-font
}
```
<br>

## If & If Else Statements
- can be used with mixins and functions
- checks against booleans or null values
```
@mixin avatar($size, $circle: false) {
	width: $size;
	height: $size;

	@if $circle {
		border-radius: $size / 2;
	} else {
		// do something else
	}
}

.profile-img {
	@include avatar(100px, true);
}
```
<br>
