# GraphQL

## Query Product Data
- returns products and variants
- an edge is a relationship between two nodes
```
{
  products (first: 50 ) { // returns first 50 prodcts
    edges {
      node {
				id
        title
        variants (first: 50) { // returns first 50 variants
          edges {
            node {
							id
              title
            }
          }
        }
      }
    }
  }
}
```
<br>

## Pagination (Cursor Based)
- use `first` to return the first number of results
- save the last result cursor to `after`
- use `after` to display results after the saved cursor
- save the first result cursor to `before`
- use `before` to return any results from where the before cursor is set (used for previous page view)
- use `sortKey` to organize results based on condition
- you can also use `pageInfo` to check for pages
```
query	($limit: Int, $lastLimit: Int, $beforeCursor: String,	$afterCursor:	String) {
	products(first:	$limit, last: $lastLimit, before: $beforeCursor, after:	$afterCursor, sortKey:TITLE)	{
		pageInfo	{
				hasNextPage
				hasPreviousPage
		}
		edges	{
			cursor
			node	{
				id
				title
				descriptionHtml
				images (first: 1) {
					edges {
						node {
							originalSrc
							altText
						}
					}
				}
			}
		}
	}
}
```