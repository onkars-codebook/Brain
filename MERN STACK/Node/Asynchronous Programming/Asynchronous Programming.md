`Asynchronous programming is a technique that enables your program to start a potentially long-running task and still be able to be responsive to other events while that task runs, rather than having to wait until that task has finished. Once that task has finished, your program is presented with the result.`

## synchronous Programming
`This code will be executed line by line.`

```javascript
const name = "Miriam";
const greeting = `Hello, my name is ${name}!`;
console.log(greeting);
// "Hello, my name is Miriam!"
```

`The reason for this is that this JavaScript program is _single-threaded_. A thread is a sequence of instructions that a program follows. Because the program consists of a single thread, it can only do one thing at a time: so if it is waiting for our long-running synchronous call to return, it can't do anything else.`

[[callbacks]]
[[promises]]
[[async and await]]
[[DealwithAPI'S]]