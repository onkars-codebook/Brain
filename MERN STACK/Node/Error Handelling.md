
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

```javascript
const express = require('express');
const app = express();
const expressError = require("./ExpressError")
const checkTocken = (req,res,next)=>{
    let {token} = req.query;
    if(token == "giveaccess"){
        next();
   }
   throw new expressError(404, "ACCESS DENIED!");
	//here the custom error message wil be thrown 
app.use("/api",checkTocken,(req,res)=>{
    res.send("Unable to access the data here !");
});
app.listen(8080, () => {
    console.log('Server running on port 3000');
});

```

```javascript
const checkTocken = (req,res,next)=>{
    let {token} = req.query;
    if(token == "giveaccess"){
    next();
   }
   throw new expressError(404, "ACCESS DENIED!");
};
app.use("/api",checkTocken,(req,res)=>{
    res.status(500).send("Unauthorized Access");
});
```



```javascript
function errorHandler (err, req, res, next) {
  if (res.headersSent) {
    return next(err)
  }
  res.status(500)
  res.render('error', { error: err })
}
```
`- The res.statusCode is set from err.status (or err.statusCode). If this value is outside the 4xx or 5xx range, it will be set to 500.`

`- the `res.statusMessage` is set according to the status code.`

`- The body will be the HTML of the status code message when in production environment`

![[Pasted image 20250116083340.png]]

## Defining Own Error Class:

```javascript
class expressError extends Error {
    constructor(status,message) {
        super();
        this.status = status;
        this.message = message;
    }
}
module.exports = expressError;
```
