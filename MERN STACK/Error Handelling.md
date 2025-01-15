
```javascript
javascript
function errorHandler (err, req, res, next) {
  if (res.headersSent) {
    return next(err)
  }
  res.status(500)
  res.render('error', { error: err })
}
```


`Error Handelling : `

```javascript
app.get('/error', (req, res, next) => {
    try {
        abcd = abcd; 
        res.send('Error occurred'); 
    } catch (err) {
        next(err); // Pass the error to the error-handling middleware
    }
});
app.use((err, req, res, next) => {
    console.error(err.stack); // Log the error stack
    res.status(500).send('Something went wrong!');
});
```
