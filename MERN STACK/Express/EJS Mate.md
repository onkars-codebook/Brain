
```javascript
const ejsMate = require("ejs-mate");
```

`We need to set the default engine for the ejs`

```javascript
`app.engine("ejs",ejsMate)`
```

`Example : `

Folder : ***includes***

- Footer.ejs
```html
<footer>
	//Defining the footer inside this 
</footer>
```
- main.ejs
```html
<main>
	   //this will contain the main content.
</main>
```
- nav.ejs
```html
<nav-bar>
	//Naviation Bar 
</nav-bar>
```

Folder : ***Layout***
- boilerplate.ejs

```javascript 
<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="/css/style.css">
    <link rel="icon" href="/img/logo.png" type="image/png">>
    <title>AirHoster</title>
</head>
<body>
    <%-include("../includes/navbar.ejs")%>
    <div class="container">
        <%-body%>
    </div>
    <%- include("../includes/footer.ejs") %>
</body>
</html>
```


***Listings***
- edit.ejs
```html
<% layout('./layouts/boilerplate') %>
    <body>
			// this will contain the body of the views 
	</body>
```

- index.ejs
```html
<% layout('./layouts/boilerplate') %>
    <body>
			// this will contain the body of the views 
	</body>
```
