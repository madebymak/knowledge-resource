# GraphQL

## Query Product Data
- returns products and variants
- an edge is a relationship between two nodes
```
{
  products (first: 50) { // returns first 50 prodcts
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