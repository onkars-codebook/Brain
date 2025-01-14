`It is intermidiatary`

`some works we have to do after getting an request and before sending an response that is known as 'Middlewares'`

![[MERN-Middlewares]]

Middleware functions :

`1. Method_override`
`2. body Parser`
`3. express.static`
`4. express.urlEncoded`

Example :
```javascript
	app.use(express.urlEncoded({extended : true}));
```

`First of all the request is recieved from the client, then above Middleware Enocoded the data. Request->middleware(above line)->Response `

```javascript
app.use(express.static(path.join(__dirname,"/Public")));
```

	- Execute any code.
	- Middle wares are able to access the req and res object.
	- Middlewares call the next middlware function in stack. eg :mid1->mid2->mid3. 
	- Middlewares can able to send the response them selves. 
	- They can end the req and res cycle. 

Defining an Middlewares

```javascript
	app.use(()=>{
		console.log("This is the response from middlewares");
	});
```

`This middleware will send the same response to each request.`

```javascript
//this middlware is able to access the queries 
// localhost:8080/?query=abcd
app.use((req,res)=>{
	let data = req.query;
	console.log(data);
	res.send("Middleware finished !");
})
```

## next
`the next middleware function is is donoted by the car`

```javascript 
app.use((req,res,next)=>{
	console.log("Time :",Date.now());
	next();
	//console.log("This is after the root");
	//return next();   --if we do like this then it will return an 'next' line         after line will not be executed.
});
```

`If the given middleWare function does not end the request-response cycle, then It must call the next() middleware function to pass the controll of the function to the another function`
## Types of middlewares
	1)Built-in Middlewares i.e: url-enconded, express.static
	2)Third party Middleared i.e : cookie-parser, morgan etc(we need to install it through the npm to Use it)
	read DOOCS :
	 
	> https://blog.bitsrc.io/5-express-middleware-libraries-every-developer-should-know-94e2728f7503

### Middleware Chaining :

```javascript
app.use((req, res,next) => {
    console.log("This is 1st middleware function!");
    next();
});
app.use((req,res,next)=>{
    console.log("This is 2nd middleware ")
    next();
})
```

`first line it will print 'This is 1st middleware function.`
`This is 2nd middleware function.`
`then it will print the remaining requests`

```javascript
	app.use((req,res,next)=>{
		console.log(req.method,req.hostname);
		next();
		console.log(req.path,req.method,req.path)
	})
```

`Output:`  ``

##### `Visit the site for more info :`

                  `https://expressjs.com/en/5x/api.html#req` 


```javascript
app.listen(port,(req,res)=>{
    console.log("Listening Request on",port)
});
app.get("/",(req,res)=>{
    res.send("I am root");
});
app.get("/random",(req,res)=>{
    res.send("This is Random page");
});
//This will do nothing !! Because the request and response cycle is now ended.
//logger - (logs the related information)
app.use((req,res,next)=>{
    console.log(req.method,req.path,req,app.protocol,app.route);
});
```

`Generally we write the middlewares before the request`

```
Middleware should be only work for the "/random" route.
```
```javascript
app.use("/random",(req,res,next)=>{
    console.log("I am only for random")
});
```


`Log in System :`
```lua
api/listings/login
api/listings/signup 
api/listings/index
```
`User can directly go to the index.js without the login, We can create that routes inside the middlewares to stop this Unusual functionality.`

---

`Note : We can use the middlewares at the end of the page, to create the 404 error page, If the we are not able to sent the request to any route then at last the req will be sent to the Last Middlewares`.

---

### API token as Query string ;

`Our API will send the response, only if the API KEY is passed .

```r
/api?token = give access
```

`e.g:`
```javascript
app.use("/api",(req,res,next)=>{
	let {token} = req.query;
	if(token === "give access"){
	next();
	//now the next request and response cycle continues.
   }
   res.send("ACCESS DENIED!");
});
```

`http://localhost:8080/api?token=giveaccess`


### Multiple Middlewares

```javascript
const checkTocken = (req,res,next)=>{
	let {token} = req.query;
	if(token === "give access"){
	next();
	//now the next request and response cycle continues.
   }
   res.send("ACCESS DENIED!");
};
//when we sent the request to the '/api' then the 'checkToken' Middleware will be  executed.
app.use("/api",checkToken,(req,res)=>{
	res.send("Data");
})
```


### Error Handelling 
`Express Default Error Handeller.`

`development stage--------> Production Stage`

- `Syntax Error :`
	 `This type of error getting fixed during an development stage.`
- `Errors During Production :`
	 `Suppose the project is using an Google map API's, If error is occured there  then the there will be an error.`
