# Shopify Liquid

## Render
- renders a snippet from the snippets folder of a theme.
- replaces deprecated `include` tag
```
{% render 'snippet-name' %}

// you can pass data to the snippet via a variable
{% render 'snippet-name', variable: data %}

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
