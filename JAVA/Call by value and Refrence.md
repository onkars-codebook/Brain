`By default the java is always uses a 'call by value', meanse the copy of the original variable is stored in the stack not the original variable.`
`meanse that fucntion execution is getting completed then the copy of the variable is cleared`

```java
// This program simply illustrate about the call by value and call by ref

public class CallByVal {
    public static void main(String[] args) {
        int a = 10;
        int b = 20;
        swap(a, b); //passing the actual paramters 
        System.out.println("Outside the function :");
        System.out.println("Value of A :"+ a );
        System.out.println("Value of B :"+b);
    }
    public static void swap(int a,int b){  //fomal parameters
        int temp;
        temp = a;
        a = b ;
        b = temp;
        System.out.println("inside the function :");
        System.out.println("Value of A :"+a)
        System.out.println("Value of B :"+b);
    }
}
```

```outpt 
inside the function :
Value of A :20
Value of B :10
Outside the function :
Value of A :10
Value of B :20
```

one thining that we've noticed here is that, that changes are only inside the function itself only not the global changes are there,as we already dicussed about the call stack,
					In the call stack, when the swap function is executed its values are 
in the stack space only, its not accesable for the other function (stack) so outside the stack its simply printing the its Original values not its swapped values.
