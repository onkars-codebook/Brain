# What is JSON?

**JSON (JavaScript Object Notation)** is a lightweight, text-based format for storing and exchanging data. It is commonly used to transmit data between a server and a web application.
## JSON Structure

JSON data is represented as key-value pairs. The structure looks like this:

```json
{
  "key": "value",
  "key2": "value2"
}
```

Example :

```JSON
{
  "name": "John",
  "age": 30,
  "isStudent": false,
  "address": {
    "street": "123 Main St",
    "city": "New York"
  },
  "courses": ["Math", "Science"]
}
```


# What is AJAX?

**AJAX (Asynchronous JavaScript and XML)** is a technique used in web development to create dynamic, interactive web pages. It allows web pages to update data asynchronously (in the background) without reloading the entire page. AJAX is used to retrieve data from a server and update parts of a web page without having to refresh the whole page.

## How Does AJAX Work?

AJAX uses a combination of:
- **JavaScript** to make the request and handle the response.
- **XMLHttpRequest** or **Fetch API** to communicate with the server asynchronously.
- **DOM manipulation** to update the page with new data.

### Key Concepts:
- **Asynchronous**: The request and response happen in the background, allowing the rest of the page to function without interruption.
- **XML or JSON**: The data returned from the server is often in XML or JSON format.
- **No Page Reload**: Only the necessary parts of the page are updated, providing a smoother user experience.

## Sending an API req by using `fetch`

```javascript
let url = 'https://catfact.ninja/fact'; 
 //'fetch' will returns promise
 fetch(url) // Make a request to the given URL
 .then((res) => {       // Once the request is successful, the response (res) is available here
     console.log(res); // Print the whole response to the console
     return res.json(); // Convert the response into JSON format
 })
 .then((data) => { // Once the JSON is ready, it will be available here as 'data'
     console.log(data.fact); // Print the 'fact' property from the data object to the console
 })
 .catch((error) => { // If something goes wrong in any step, handle the error here
     console.log("error : ", error); // Print the error message to the console
 });
```

## Sending an API request using an AXIO'S 

**Axios** is a popular JavaScript library used to make HTTP requests (such as GET, POST, PUT, DELETE) from the browser or Node.js environment. It is often used in web development to interact with APIs, fetch data from servers, or send data to servers. Axios is promise-based, meaning it allows you to handle asynchronous requests more easily compared to the traditional callback-based methods.

```javascript 
//we have alredy a fetch method why axios?
//------------------------------------------------------------------------------
//1. fetch(url) // Make a request to the given URL
//2. .then((res) => {       // The response (res) is available here
//3.     console.log(res);  // Print the whole response to the console
//4.     return res.json();  // Convert the response into JSON format
//5.  });
//6. .then((data) => {       //JSON is ready, it will be available here as 'data'
//7.     console.log(data.fact); // Print the 'fact' property
//8. })
//------------------------------------------------------------------------------
// fetch response will in redableStream 
// line No 3 will print the :
// body: ReadableStream then convert into the json file 
// using axios we can directly get the data

// axios is responsible for sending the http request direcly.

let url ="https://catfact.ninja/fact";
let para = document.querySelector("p");
let btn = document.querySelector("button");
btn.addEventListener("click",getFacts);
async function getFacts(){
    try {
        let res = await axios.get(url);
        para.textContent = res.data.fact;
        console.log(res.data.fact);
    } catch (e) {
        console.log("ERROR - ",e);
    }
}
```

```javascript 
 const config ={headers:{Accept :"application/json"}};  // by adding this header we can make it into an application/json form   
```

Example 2 :

```javascript 
let url = "https://dog.ceo/api/breeds/image/random";

let btn = document.querySelector("button");
let img = document.querySelector("img");
btn.addEventListener("click",async ()=>{
   let image  = await getImage();//till the getting image source img.src will not be set
   img.src = image;
});

async function getImage(){
    try{
        let res = await axios.get(url);   
        //The axios.get(url) method will return a Promise that resolves to an 
        // Axios Response Object if the request is successful, or rejects with 
        // an error if the request fails.
        console.log(res);
        let img = res.data.message;
        return img; 
    }
    catch(e){
        return "ERROR TO FETCH AN IMAGE";
    }
}
```