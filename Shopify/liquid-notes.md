# Shopify Liquid

## Render
- renders a snippet from the snippets folder of a theme.
- replaces deprecated `include` tag
```
{% render 'snippet-name' %}

// you can pass data to the snippet via a variable
{% render 'snippet-name', variable: data %}å
```
<br>

## Request Object
- `request.host` to check the current domain
```
{% if request.host == 'myshop.com' %}
  Welcome USA!
{% elsif request.host == 'myshop.ca' %}
 Welcome Canada!
{% else %}
  Welcome!
{% endif %}
```
<br>

- `request.path` returns current path
```
{{ request.path }} // /collections/classics/products/chambray-shirt
```
<br>

- `request.page_type` returns current page type (pages, collection, blog, index, etc)
```
{{ request.page_type }} // index
```
<br>

## Cart AJAX
- use `/cart.js` to get cart JSON
```
jQuery.ajax({
	url: '/cart.js',
	dataType: 'json'
});
```
<br>

- use `/cart/change.js` to update cart line item properties
```
jQuery.ajax({
	url: '/cart/change.js',
	dataType: 'json',
	type: 'POST',
	data: {
		'line': item.key, // use cart line item key
		'quantity: item.quantity, // defaults to 1 if not set
		'properties': {
			// change properties (will OVERWRITE ALL line item properties)
		}

	}
})
```