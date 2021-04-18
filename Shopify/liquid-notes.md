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

## Increase Pagnination Limit
- Shopify limits pagination to 50 items by default
- we can increase the number by adding using the `pagination` syntax
```
// increases pagination to 100 from 50
{% paginate collection.products by 100 %}
	{% for product in collection.products %}
		{{ product.handle }}
	{% endfor %}
{% endpaginate %}
```
<br>

## Upcase/Downcase String
- quicker to transform case in liquid than with CSS or JS
- useful for theme customization header text settings
```
<p>UPPERCASE THIS TEXT</p>

// better way
{% 'uppercase this text' | upcase %}

{% assign lowercaseString = 'AbCdEfG' | downcase %}
{{ lowercaseString }} // abcdefg
```
<br>

## Section Settings Iteration
- use bracket selection to loop through section/block settings
```
{% for index in (1..4)%}
	{% assign colImg = "column_img_" | append: index %}
	{% assign colText = "column_text_" | append: index %}

	<div>
		<img src="{{ section.settings[colImg] | img_url }}">
		<div>
			{{ section.settings[colText] }}
		</div>
	</div>
{% endfor %}
```
<br>

## Remove Map From Order Status Page
- you can use either CSS or jQuery to remove the map from the order status page
```
// CSS
  .map {display:none }

// jQuery
if(Checkout && Checkout.$ && Checkout.$.fn) {
	Checkout.$('.map[data-mapbox]').parent().remove();
}
```
<br>

## Video Thumb
- use youtube url as thumb
```
{% assign video_url = "https://www.youtube.com/watch?v=r_CPx8qHHu0" %}
{% assign video_id = video_url | split: "v=" | last %}
{% assign thumbnail_url = 'http://img.youtube.com/vi/' | append: video_id | append: '/maxresdefault.jpg' %}

<a class="popupVideo" href="{{ video_url }}">
	<img class="tying-thumb" src="{{ thumbnail_url }}" alt="" />
</a>
```
<br>

## Get Product By Handle
- get product object by handle using `all_products`
```
{% assign handle = "product-handle" %}
{% assign product = all_products[handle] %}

{{ product.title }} // Product Handle
{{ product.id }} // Product ID
{{ product.url }} // /products/product-handle
```
<br>

## Color Modif
```
{% style %}

.some-class {
	background: {{ '#7ab55c' | color_modify: 'alpha', 0.85 }} // rgba(122, 181, 92, 0.85)
}

{% endstyle %}
```
<br>
