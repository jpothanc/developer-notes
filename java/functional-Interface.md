# Java Functional Interfaces Cheat Sheet

Java functional interfaces are interfaces with a single abstract method, which can be implemented using lambda expressions, method references, or anonymous classes. They are the backbone of functional programming in Java.

| Functional Interface | Description                                 | Method Signature     |
| -------------------- | ------------------------------------------- | -------------------- |
| Predicate            | Takes one input and returns a boolean.      | `boolean test(T t);` |
| Consumer             | Takes one input and returns nothing (void). | `void accept(T t);`  |
| Function             | Takes one input and returns a result.       | `R apply(T t);`      |
| Supplier             | Takes no input and returns a result.        | `T get();`           |

## Predicate

A `Predicate` is a functional interface that represents a boolean-valued function of one argument.

```java
@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);
}
Predicate<Integer> isEven = x -> x % 2 == 0;
System.out.println(isEven.test(4)); // Output: true
System.out.println(isEven.test(5)); // Output: false
```

## Consumer

A Consumer is a functional interface that represents an operation that takes a single input argument and returns no result.

```java
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}
Consumer<String> printConsumer = s -> System.out.println(s);
printConsumer.accept("Hello, World!"); // Output: Hello, World!

//Using Anonymous Class
Consumer<String> printConsumer = new Consumer<String>() {
    @Override
    public void accept(String s) {
        System.out.println(s);
    }
};
printConsumer.accept("Hello, Anonymous Class!"); // Output: Hello, Anonymous Class!


//Passing Consumer as a Parameter
public static void processString(String input, Consumer<String> consumer) {
    consumer.accept(input);
}
Consumer<String> printConsumer = s -> System.out.println(s);
processString("Hello, Passing Consumer!", printConsumer); // Output: Hello, Passing Consumer!

```

## Function

A Function is a functional interface that represents a function that takes one argument and produces a result.

```java
@FunctionalInterface
public interface Function<T, R> {
    R apply(T t);
}


Function<Integer, String> intToString = x -> "Number: " + x;
System.out.println(intToString.apply(5)); // Output: Number: 5

```

## Supplier

A Supplier is a functional interface that represents a supplier of results. It has no input arguments and provides a single output.

```java
@FunctionalInterface
public interface Supplier<T> {
    T get();
}

Supplier<String> supplier = () -> "Hello, Supplier!";
System.out.println(supplier.get()); // Output: Hello, Supplier!


Supplier<Double> randomValue = () -> Math.random();
System.out.println(randomValue.get()); // Output: Random value (e.g., 0.123456789)
```
