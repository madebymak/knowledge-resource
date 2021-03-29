# Shopify Snippets

## Create Array
- you can create an array in liquid by joining string and then splitting
```
{% assign variantIdList = "" %}

// loop through object and add to list
{% for variant in product.variants %}
		{% assign variantIdList = variantIdList | append: variant.id | append: "," %}
{% endfor %}

// split list into an array
{% assign variantIdList = variantIdList | split: "," %}

// loop through variant id list
{% for id in variantIdList %}
	{{ id }}
{% endfor %}
```

## Cart AJAX
- use `/cart.js` to get cart JSON
```
// jQuery
jQuery.ajax({
	url: '/cart.js',
	dataType: 'json'
});

// fetch api
fetch('/cart.js', {
        method: 'get'
    })
    .then(response => response.json())
    .then(jsonData => console.log(jsonData))
    .catch(err => {
            //error block
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
			// NOTE: changing properties (will OVERWRITE ALL line item properties)
		}
	}
})
```
<br>