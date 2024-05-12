# Visitor

The Visitor pattern is a behavioral design pattern that allows adding new behaviors or operations to a group of related objects without modifying their classes. It separates the logic for performing operations on objects from the objects themselves. The pattern is useful when the objects have different types and structures, and the behavior needs to vary based on those types.

The visitor pattern can be used to implement a variety of operations on object structures, such as:

- Serialization: The visitor can be used to serialize the object structure to a stream of data.
- Logging: The visitor can be used to log information about the object structure.
- Validation: The visitor can be used to validate the object structure.

```csharp
// Element interface
public interface Element {

  void accept(Visitor visitor);

}

// Concrete element classes
public class Book implements Element {

  @Override
  public void accept(Visitor visitor) {
    visitor.visitBook(this);
  }

}

public class Movie implements Element {

  @Override
  public void accept(Visitor visitor) {
    visitor.visitMovie(this);
  }

}
```

```csharp
// Visitor interface
public interface Visitor {

  void visitBook(Book book);

  void visitMovie(Movie movie);

}
```

````csharp
// Visitor interface
// Concrete visitor classes
public class SerializeVisitor implements Visitor {

  @Override
  public void visitBook(Book book) {
    System.out.println("Serializing book: " + book.getName());
  }

  @Override
  public void visitMovie(Movie movie) {
    System.out.println("Serializing movie: " + movie.getName());
  }

}

public class LogVisitor implements Visitor {

  @Override
  public void visitBook(Book book) {
    System.out.println("Logging book: " + book.getName());
  }

  @Override
  public void visitMovie(Movie movie) {
    System.out.println("Logging movie: " + movie.getName());
  }

}
```cshharp
// Main class
public class Main {

  public static void main(String[] args) {

    // Create element objects
    Book book = new Book("The Lord of the Rings");
    Movie movie = new Movie("The Shawshank Redemption");

    // Create visitor objects
    SerializeVisitor serializeVisitor = new SerializeVisitor();
    LogVisitor logVisitor = new LogVisitor();

    // Visit element objects
    book.accept(serializeVisitor);
    book.accept(logVisitor);
    movie.accept(serializeVisitor);
    movie.accept(logVisitor);

  }
}

```csharp
````
