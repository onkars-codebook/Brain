Regular expression is the sequence of characters that forms the search pattern.
syntax :
```javascript 
/pattern/modifiers
```

```
Modifiers :
g - perform  global match 
i - case insensitive match 
m - Perform muliline match 
```

**test( )**
`The test  method tesst for the match in the string string, Returns true of findmatch, else false `

```javascript
RegExObject.test(String)
```

**Match( )**
This method of regular expression that returns an array containing all matches 'null' if no matches.
`String.match()` 

```javascript 
String.match(RegExpressionObj);
```

```javascript 
var p = /onkar sathe/i;
function testMatch(){
	var str = "Hello this is the onkar sathe ";
	if(p.test(str)){
		alert("str contains pattern ");
	}else{
		alert("str not conatins patttern")
	}
}
```
