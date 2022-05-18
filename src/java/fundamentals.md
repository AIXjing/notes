# Java fundamentals

## Exceptions

In Java, an exception is an event that disrupts the normal flow of the program [^1]. 

Many methods in Java to read and write files require that exceptions are handled. There are two main approaches: *lbyl (look at before you leap)* and *eafp (easy to ask for forgiveness than permission)*. 

1.  **Look at before you leap**

    In the following code, we check if the arguements are valid before operation.

    ```java
    private static int divideLBYL(int x, int y) {
        if (y != 0) return x / y;
        else return 0;
    }
    ```

2. **Easy to ask forgiveness than permission**

    In this approach, we run the method first and catch the exception if any exception (exception handler).

    ```java
    private static int divideEAFP(int x, int y) {
        try {
            return x / y;
        } catch(ArithmetricException e) {
            return 0;
        }
    }
    ```

### Checked Exception vs. Unchecked Exception

The *Exception Handling in Java* is one of the powerful mechanism to handle the runtime errors so that the normal flow of the application can be maintained. The Exception class family in Java is depicted below:

![image](https://user-images.githubusercontent.com/41487483/169143928-35f36c13-4a82-424d-84e3-dd8d2ac3780f.png)


There are basically three types of exceptions: *Checked Exception*, *Unchecked Exception*, and *Error*. Sometimes, Error can be considered as Unchecked Exception. 

- **Checked Exceptions**: All the subclasses of Exception class except for RuntimeException and its subclasses are checked exceptions. That is, if there is an checked exception in the code, the program won't be compiled if no exception handling.

    ```java
    public class CheckedVsUnchecked {
        public static void main (String[] args) {
            readFile("myFile.txt");
        }

        private static void readFile (String fileName) {
            // will throw a FileNotFoundException, that is checked exception
            FileReader file = new FileReader(fileName);
        }
    }
    ```

    The above code would not compile because fileName may not exist, which will throw a *FileNotFoundException* (unchecked expcetion). To handle unchecked exception, we can use either *try-catch* method or `throws` exception in the function signature [^2]. The difference between `throw` within a method and `throws` in a method signature can be found in this [article](https://www.javatpoint.com/difference-between-throw-and-throws-in-java).

    ```java
    public class CheckedVsUnchecked {
        // it is important to throw an exception in main method as well
        // in order to catch the exception thrown by readFile method
        public static void main (String[] args) throws FileNotFoundException {
            readFile("myFile.txt");
        }

        private static void readFile (String fileName) throws FileNotFoundException {
            FileReader file = new FileReader(fileName);
        }
    }
    ```

- **Unchekced Exception**: The RuntimeException subclass of the Exception class and all its subclasses are unchecked exception. Runtime will not check this type of exception and the program will be compile but may fail. For example,

    ```java
    public class CheckedVsUnchecked {
        public static void main (String[] args) {
            String name = null;
            printLength(name);  // will throw NullPointerException even compiled.
        }

        private static void printLength (String myString) {
            System.out.println(myString.length());
        }
    }
    ```

In this case, it is better to use try-catch method to handle this exception. 

### Call stack

When throwing an expcetion, Java automatically prints a <u>stack trace</u>, which is showing the <u>call stack</u>. Each <u>thread</u> of execution has its own call stack, and the thread is shown in the first line of the stack call.

### try-catch(-finally)

A common way to handle exception is to throw a new exception with some information to indicate where might go wrong. For example,

```java
private static int divide() {
    int x, y;
    try {
        x = getInt(); // a self-defined method that can get input from typing the keyboard.
        y = getInt();
        return x / y;   
    } catch (NoSuchElementException e) {
        throw new NoSuchElementException("no suitable input");
    } catch (ArithmetricException e) {
        throw new ArithmetricException("attempt to divide by zero");
    }   
}
```

Alternatively, we could catch multiple exception in the main methods, such as 

```java
private static void main (String[] args) {
    try {
        int result = divide();
    } catch (ArithmetricException | NoSuchElementException e) {  // it is not logical symbol or
        System.out.println(e.toString);
        System.out.println("Unable to excute, the computer shutting down");
    }
}
```

When Java code throws an exception, the runtime looks up the stack for a method that has a handler (like `catch`) that can process it. If it finds one, it passes the exception to it. If it doesn't, the program exists. 

No matter whether an exception occur in try-block or not, `finally` will ALWAYS be excuted. For example,

```java
// Java program to demonstrate control flow of try-catch-finally clause
// when exception occur in try block but not handled in catch block
class GFG {
    public static void main (String[] args) {  
        // array of size 4.
        int[] arr = new int[4];
         
        try {
            int i = arr[4];
            // this statement will never execute
            // as exception is raised by above statement
            System.out.println("Inside try block");
        }
        // not a appropriate handler so the following statement will also not execute
        catch(NullPointerException ex) {
            System.out.println("Exception has been caught");
        }
         
        finally { // will execute
            System.out.println("finally block executed");
        } 
        // rest program will not execute
        System.out.println("Outside try-catch-finally clause");
    }
}
```

However, if `NullPointerException` was replaced by `ArrayIndexOutOfBoundsException`, the correct exception, the statement in the `catch` will execute.

Even if there is a `return` in `try` block, the `finally` statement will also be excuted.  

```java
private static int printAnumber () {
    try {
        return 3;
    } 
    catch (Exception e) {
        return 4;
    }
    finally {
        return 5;
    }
    // output: 5, becauase the finally statement will override the above statement.
}
```

## Read and Write File

If we want to make object persist, we need to write object into a file. See an example as below. Remember to close the file after writing. Failing to close streams can really cause problems such as *resouce link leak* and *lcoked file*.


-------
reference

[^1]: https://www.javatpoint.com/exception-handling-in-java

[^2]: https://www.youtube.com/watch?v=bCPClyGsVhc