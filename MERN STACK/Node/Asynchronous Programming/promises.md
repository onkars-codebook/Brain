# Promises in JavaScript
 Note : Codes are simply generated by GPT 4.0 for the better understanding about the concepts.
## What are Promises?
A **Promise** in JavaScript is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises provide a clean and more manageable way to work with asynchronous code.

Promises have three states:
1. **Pending**: The initial state, neither fulfilled nor rejected.
2. **Fulfilled**: The operation completed successfully.
3. **Rejected**: The operation failed.

A promise lets you attach callbacks for handling the success or failure of the operation using `.then()`, `.catch()`, and `.finally()` methods.

---

## Callback Hell
Before promises, developers used nested callback functions for handling asynchronous code. This often led to **callback hell**, a situation where the code becomes unreadable and difficult to maintain due to deeply nested callbacks.

### Example of Callback Hell:
```javascript
getData(function (result1) {
  processResult(result1, function (result2) {
    validateResult(result2, function (result3) {
      saveResult(result3, function () {
        console.log("Data saved successfully!");
      }, function (error) {
        console.error("Error saving result:", error);
      });
    }, function (error) {
      console.error("Error validating result:", error);
    });
  }, function (error) {
    console.error("Error processing result:", error);
  });
}, function (error) {
  console.error("Error getting data:", error);
});
```

---

## How Promises Solve Callback Hell
Promises simplify the handling of asynchronous tasks by chaining methods instead of nesting callbacks. This makes the code more readable and easier to debug.

### Example Using Promises:
```javascript
getData()
  .then((result1) => processResult(result1))
  .then((result2) => validateResult(result2))
  .then((result3) => saveResult(result3))
  .then(() => {
    console.log("Data saved successfully!");
  })
  .catch((error) => {
    console.error("Error occurred:", error);
  });
```

---

### Breaking Down the Example:
1. **getData()**: Returns a promise.
2. **.then()**: Used to handle the success of each operation.
3. **.catch()**: Handles any error that occurs in the chain.
4. No deep nesting: Each `.then()` handles the next step in a flat manner.

---

## Example Code:

Here is a full example with a simulated asynchronous operation using `setTimeout`:

### Simulated Callback Hell:
```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback(null, "Data fetched");
  }, 1000);
}

function processData(data, callback) {
  setTimeout(() => {
    callback(null, data + " -> Processed");
  }, 1000);
}

function saveData(data, callback) {
  setTimeout(() => {
    callback(null, data + " -> Saved");
  }, 1000);
}

fetchData((err, data) => {
  if (err) {
    console.error("Error fetching data");
    return;
  }
  processData(data, (err, processedData) => {
    if (err) {
      console.error("Error processing data");
      return;
    }
    saveData(processedData, (err, savedData) => {
      if (err) {
        console.error("Error saving data");
        return;
      }
      console.log(savedData);
    });
  });
});
```

### Using Promises:
```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Data fetched");
    }, 1000);
  });
}

function processData(data) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(data + " -> Processed");
    }, 1000);
  });
}

function saveData(data) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(data + " -> Saved");
    }, 1000);
  });
}

fetchData()
  .then((data) => processData(data))
  .then((processedData) => saveData(processedData))
  .then((savedData) => {
    console.log(savedData);
  })
  .catch((error) => {
    console.error("Error:", error);
  });
```

---

## Key Benefits of Promises:

1. **Readability**: Code is easier to understand and maintain.
2. **Error Handling**: Centralized error handling using `.catch()`.
3. **Chaining**: Methods can be chained in a flat structure.

---

By using promises, you can manage asynchronous operations more effectively and avoid the pitfalls of callback hell. Promises are now a fundamental part of modern JavaScript and are widely used in combination with `async/await` for even cleaner asynchronous code.


---
---

### Fundamental Example :

```javascript
// Mock function simulating a database query
function insertIntoDatabase(userData) {
    return new Promise((resolve, reject) => {
        // Simulated delay to mimic async database operation
        setTimeout(() => {
            // Mock SQL error check
            if (!userData.name || !userData.age) {
                reject("SQL Error: Missing 'name' or 'age' in the input data");
            } else {
                resolve(`Data inserted successfully for user: ${userData.name}`);
            }
        }, 1000); // Simulated 1 second delay
    });
}
// Example usage
const user = { name: "Onkar", age: 19 }; // Valid data
const invalidUser = { name: "Onkar" }; // Missing age field

// Handling promise with valid data
insertIntoDatabase(user)
    .then((result) => {
        console.log("Success:", result);
    })
    .catch((error) => {
        console.log("Error:", error);
    });

// Handling promise with invalid data
insertIntoDatabase(invalidUser)
    .then((result) => {
        console.log("Success:", result);
    })
    .catch((error) => {
        console.log("Error:", error);
    });

```

If Successfull :

`User added successfully with ID: 1`

If an error occurs (e.g., SQL syntax error or missing data):

`SQL Error: Column 'age' cannot be null`

