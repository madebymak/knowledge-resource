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