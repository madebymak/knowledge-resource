# Express (Node.js) Notes

## Return Response
- always  return something from the endpoint to keeps it from looping
```
// return JSON
app.post('/', (req, res) => {
	res.json()
});

// return something to the frontend
app.get('/', (req, res) => {
	res.send('Hello World');
});

// use end if not returning any data (ex: 404 page)
app.get('/', (req, res) => {
	res.status(404).end();
});
```
<br>
