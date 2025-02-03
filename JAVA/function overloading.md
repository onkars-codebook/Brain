function overloading using an datatype 
```java
public class File {

    // function overloading using number of parameters

    public static void sum(int num1, int num2) {
        System.out.println("Sum of " + num1 + " and " + num2 + " is " + (num1 + num2));
    }
    public static void sum(int num1, int num2, int num3) {

        System.out.println("Sum of " + num1 + "," + num2 + " and " + num3 + " is " + (num1 + num2 + num3));

    }
    public static void main(String[] args) {
        sum(10, 12);
        sum(10, 20, 30);
    }
}
```

`Function overloadin using an datatypes :`
```java
class File{
	public static void sum(int a, float b){
		return a + b;
	}
	public static void sum(float a, int b ){
		return a + b; 
	}
	public static void main(String[] args){
		Scanner sc = new Scanner(System.in);
		int num = sc.nextInt();
		System.out.println(sum(10,12.3));
	}
}
```