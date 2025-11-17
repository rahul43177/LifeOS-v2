- Added after `?` in URL
- Optional filters, sorting, pagination
- Key-value pairs separated by `&`
- Format: `/users?age=25&city=NYC`

**Example:**

```javascript
// Route definition
app.get('/users', handler)

// Actual URL
GET /users?age=25&city=NYC&sort=name

// Access in Express
req.query.age   // "25"
req.query.city  // "NYC"
req.query.sort  // "name"
```
