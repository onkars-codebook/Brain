### What is the callback hell ?

Callback hell refers to a situation in JavaScript where you have many nested callback functions, making the code difficult to read, debug, and maintain. It often happens when you perform asynchronous operations in sequence, and `each step depends on the result of the previous step.`It looks like a "pyramid of doom" because of the increasing levels of indentation

```javascript 
function changeColor(color, delay, nextColor) { 
  setTimeout(() => {              //the nextColor is function argument.
    h1.style.color = color; 
    // Call the nextColor callback, if provided
    if (nextColor) {
      nextColor();
    }
  }, delay);
}
// Example Usage
const h1 = document.querySelector("h1");

changeColor("red", 1000, () => {
  changeColor("blue", 1000, () => {
    changeColor("green", 1000);
  });
});
```

we all know that Javascript is the synchronous but the above function shows the asynchronous behaviour of the javascript, By using the asynchrouns behaviour that is the provided by the browser. Browser provides the aynchronous API lile  setTimeOut( ) , fetch() and etc .
