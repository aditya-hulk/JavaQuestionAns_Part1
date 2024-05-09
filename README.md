# Exception Handling via Code Decode
# 1.1 What is an Exception?
![alt text](image.png)
#### An unexpected event that disturb normal flow of the program is called as Exception.
#### Eg of exception:  
![alt text](image-1.png)
# 1.2 How do we handle exceptions in Java?
![alt text](image-2.png)
### try block
- jisme exception aa sakta hia usse try block mein likhte hai
### catch block
- catch block exception ko catch karta
### finally block
- yaha cleanup code likha jata hai.
- clean up code 
    - humne file open kari hai, ya connection open kiya hai...
    - to usse close karna hi honga 
    - chahe exeption aaye ya nhi.. 
### eg
![alt text](image-3.png)
# 1.3 Hierarchy of Exception Handling?
![alt text](image-4.png)
### Most of the time errors are  not caused by our program and this are occurs due to lack of system resources. Error are non recoverables.
    - jaise outOfmemory error aaya to system Admin ko Heap memory badhana honga.
# 1.4 Difference between Exception and Errors?
![alt text](image-5.png)
- U can throw an error also using java.lang.Error.StackOverflowError
# 1.5 Can we write try block without catch and finally block?
![alt text](image-6.png)
### Question - yadi aapne try block likh kar code run kiya tab kya honga?
![alt text](image-7.png)
- compile time error aavenga ki insert finally to complete try statement.
# 1.6 Can we write other statements between try catch or finally block?
![alt text](image-8.png)
# 1.7 Does remaining statements in try block executes after exception occurs?
![alt text](image-9.png)
- try me exception aaya to catch mein javenga ya aapne thorws kiya ho to waha javenga..aur pgm terminate honga..
# 1.8 Diff bet throw and throws keyword in java?
![alt text](image-10.png)
# 1.9 What happen when an Exception is thrown by the main method?
![alt text](image-11.png)
- main() mehtod mein hi execption aaya to Java runtime Jre ye responsibility leti hai usko handle karni ki.
- since uske pass handling code nhi hai.. 
    - to wo pgm terminate karti
    - aur pura execption print kar deti along with it stack trace.

## by Durga
### Concept of Runtime Stack Mechanism
```java
package com.adi.Excpetions;

public class Test {

	public static void main(String args[]) {

		doStuff();
	}

	public static void doStuff() {

		doMoreStuff();
	}

	public static void doMoreStuff() {
		
		System.out.println("Hello");
	}
}
Output:
Hello
```

![alt text](image-12.png)
1. For Every thread Jvm will create a runtime stack.
2. Each and every method call performed by that thread will be stored in the corresponding stack.
3. Each entry in stack is called stack frame/Activation record.
4. After completing every method call the corresponding entry from the stack will be removed.
5. After completing all method calls the stack will become and empty.
6. And that empty stack will be destroyed by the Jvm just before terminiting the thread.

### Concept of Default Exception Handling in java
```java
package com.adi.Excpetions;

public class Test {

	public static void main(String args[]) {

		doStuff();
	}

	public static void doStuff() {

		doMoreStuff();
	}

	public static void doMoreStuff() {
		
		System.out.println(10/0);
	}
}
Output:
Exception in thread "main" java.lang.ArithmeticException: / by zero  
	at PracDemo/com.adi.Excpetions.Test.doMoreStuff(Test.java:17)
	at PracDemo/com.adi.Excpetions.Test.doStuff(Test.java:12)
	at PracDemo/com.adi.Excpetions.Test.main(Test.java:7)

```
1. Inside a method,  if any execption occurs then the method in which the exception arise is responsible to create exception object by including following information.
    - a) Name of Exception
    - b) Description of Exception
    - c) Location at which exception occurs i.e stack trace.
2. After creating the exception object, method handover it to the Jvm.
3. Jvm will check whether the method contain any execption handling code or not. 


    