Postman allows you to add automation and dynamic behaviors to your collections with [scripting](https://learning.postman.com/docs/writing-scripts/intro-to-scripts/)

There are two options are availble are there first one is the `Pre-request script`
and the second one is the `Post request script `

### The `pm` object
Postman has a [helper object named](https://learning.postman.com/docs/writing-scripts/script-references/postman-sandbox-api-reference/#the-pm-object) [pm](https://learning.postman.com/docs/writing-scripts/script-references/postman-sandbox-api-reference/#the-pm-object) that gives you access to data about your Postman environment, requests, responses, variables and testing utilities.
```javascript
		pm.response.json();
		pm.collectionVariables.get(“baseUrl”)
		pm.collectionVariables.set("variableName", "variableValue")
```

### Steps to write down you scripts :

1. In your "**add a book**" request, change the book data in your **Body** to a new book you like.  
      
2. From the **Scripts** tab of your request, open the **Post-res** tab (short for Post-response)  
    
3. Inside the Script editor, **add this JavaScript code** to log the JSON response from the API:  
    
    ```javascript
    console.log(pm.response.json())
    ```

1. **Save** your request  
      
2. **Send** your request. This will trigger the script in the Post-response script tab to run after the response comes back from the API  
    
3. **Open** the **Postman Console** in the lower left of the window.  
    
4.  Scroll to the bottom of the logs in the console. You will see your most recent request `POST https://library-api.postmanlabs.com/books`



![[Pasted image 20250118164035.png]]
`This is how you can able to use the script section to write down your script's`

### Setting and getting collection variables :

To **set** a collection variable, use the `.set()` method with two parameters: the variable name and the variable value

```javascript
	pm.collectionVariables.set("variableName",value);
	
```

To **get** a collection variable use the `.get()` method and specify the name of the variable you want to retrieve:

```javascript
pm.collectionVariables.get("variableName")
```

`There are two ways to define a variable in JavaScript: using the `const` or `let` keywords. `const` is for variables that won't change value, whereas `let` allows you to reassign the value later`

![[Pasted image 20250118171427.png]]
This is the `body` that is to be sent to the POST request.
![[Pasted image 20250118171500.png]]