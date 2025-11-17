### Path Parameters

- Part of the URL path itself
- Identify specific resources
- Required for the route to work
- Format: `/users/{id}/posts/{postId}` or `/users/:id`

**Example:**

```javascript
// Route definition
app.get('/users/:id', handler)
app.get('/products/:category/:id', handler)

// Actual URL
GET /users/123
GET /products/electronics/456

// Access in Express
req.params.id        // "123"
req.params.category  // "electronics"
```


We treat path params as params also. 
So we can Destructure --  let's say user is sending the data of book id 
```js
function filterBookById( req , res ) {
	const {bookId} = req.params; //this is params -- path parameter 
	//rest of the code .... 
}
```

