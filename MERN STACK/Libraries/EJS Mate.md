## Introduction
`ejs-mate` is a layout and partials manager for the `EJS` (Embedded JavaScript) templating engine. It simplifies working with layouts, partials, and reusable components in your `EJS` templates when building Node.js applications.

---

## Installation

Before using `ejs-mate`, ensure you have Node.js installed on your system.

1. **Install EJS** (if not already installed):
   ```bash
   npm install ejs
   ```

2. **Install ejs-mate**:
   ```bash
   npm install ejs-mate
   ```

---

## Basic Usage

### Step 1: Set up `ejs-mate` with Express
To use `ejs-mate` as the rendering engine for EJS:

```javascript
const express = require('express');
const path = require('path');
const engine = require('ejs-mate');

const app = express();

// Set ejs-mate as the rendering engine
app.engine('ejs', engine);
app.set('view engine', 'ejs');

// Set the views directory
app.set('views', path.join(__dirname, 'views'));

// Example route
app.get('/', (req, res) => {
    res.render('home');
});

app.listen(3000, () => {
    console.log('Server is running on http://localhost:3000');
});
```

### Step 2: Create a Layout File
Layouts allow you to define a structure for your pages (e.g., a common header, footer, etc.).

Create a `layout.ejs` file inside your `views` folder:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><%- title || 'My App' %></title>
</head>
<body>
    <header>
        <h1>My Website</h1>
    </header>

    <!-- Content injected here -->
    <%- body %>

    <footer>
        <p>&copy; 2025 My Website</p>
    </footer>
</body>
</html>
```

### Step 3: Create a Page Using the Layout
Now, create a page `home.ejs` inside the `views` folder:

```html
<% layout('layout') %>

<h2>Welcome to My Website</h2>
<p>This is the homepage.</p>
```

---

## Adding Partials
Partials are reusable components (e.g., a navigation bar).

1. **Create a Partial**
   Create a file called `navbar.ejs` inside a `partials` folder:
   
   ```html
   <nav>
       <ul>
           <li><a href="/">Home</a></li>
           <li><a href="/about">About</a></li>
           <li><a href="/contact">Contact</a></li>
       </ul>
   </nav>
   ```

2. **Include the Partial in the Layout**
   Update the `layout.ejs` file to include the partial:

   ```html
   <body>
       <%- include('partials/navbar') %>
       <%- body %>
   </body>
   ```

---

## Passing Data to Templates
You can pass variables to your templates using the `res.render` method:

### Example:

```javascript
app.get('/about', (req, res) => {
    res.render('about', { title: 'About Us', description: 'This is the about page.' });
});
```

Create an `about.ejs` file:

```html
<% layout('layout') %>

<h2><%= title %></h2>
<p><%= description %></p>
```

---

## Folder Structure Example

```
project-root/
├── views/
│   ├── layout.ejs
│   ├── home.ejs
│   ├── about.ejs
│   └── partials/
│       └── navbar.ejs
├── package.json
└── app.js
```

---

## Key Points
1. Use `<%- include('path/to/partial') %>` for including partials.
2. Use `<% layout('layout') %>` to specify the layout for a page.
3. Pass data using `res.render('template', { key: value })`.
4. Always set the `views` directory correctly.

---

## Resources
- [EJS Documentation](https://ejs.co/)
- [ejs-mate GitHub Repository](https://github.com/JacksonTian/ejs-mate)

---

