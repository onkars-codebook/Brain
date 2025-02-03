[[Call by value and Refrence]]
[[function overloading]]
Reusable part of the of teh code.
function is the block of the code that can be executed again and again one its written.

```java
returnType name(para1,para2){
//body 
return statement;
}
```

`Main method : `

```java
public class File {
	//main functions
	public static void main(String[] args) {
    }
}
```


Example :

```java
public class File {
    public static void main(String[] args) {
    }
    public void PrintHello(){
        System.out.println("Called from PritnHello");
    }
}
```

`What is the difference between the arguments and the parameters :`
```java
import java.util.Scanner;
public class File {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter Two Number's : :");  
        // This are arguments or actual parameters(on the function call)
        System.out.print("Sum of the two numbers is the "+sum(10,20));
  }
    public static int sum(int a, int b){   //Passing the formal paramters
        return a +b;
    }
}
```

`Call Stack :`
[[JAVA/Memory allocation]]