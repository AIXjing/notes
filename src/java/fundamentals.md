# Java fundamentals

## Exceptions

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

In Java, *Exception* and *Runtime Exception* are classes defined in *java.lang*. Other exceptions are subclasses of these two exceptions. For example, in the above snippet, `ArithmetricException e` can be replaced by `Exception e` since *ArithmetricException* is a subclass of the *Exception* class. 

When throwing an expcetion, Java automatically prints a <u>stack trace</u>, which is showing the <u>call stack</u>. Each <u>thread</u> of execution has its own call stack, and the thread is shown in the first line of the stack call.

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
    } catch (ArithmetricException | NoSuchElementException e) {
        System.out.println(e.toString);
        System.out.println("Unable to excute, the computer shutting down");
    }
}
```