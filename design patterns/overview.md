# Design Patterns

Design patterns are reusable solutions to commonly occurring problems in software design. They provide a structured approach to coding, making applications more flexible, modular, and maintainable. Originally popularized by the "Gang of Four" (GoF) in their book _Design Patterns: Elements of Reusable Object-Oriented Software_, these patterns fall into three main categories: Creational, Structural, and Behavioral.

## Gang of Four (GoF)

The "Gang of Four" refers to the four authors of the book _Design Patterns: Elements of Reusable Object-Oriented Software_:

- **Erich Gamma** (Swiss computer scientist)
- **Richard Helm** (Australian computer scientist)
- **Ralph Johnson** (American computer scientist)
- **John Vlissides** (American software engineer)

Their work became foundational in software engineering, influencing modern design pattern usage.

## Pattern Categories

### Creational Patterns

Creational patterns provide mechanisms to create objects in a controlled manner, preventing direct instantiation.

| **#** | **Pattern Name**     | **Description**                                                           |
| ----- | -------------------- | ------------------------------------------------------------------------- |
| 1     | **Abstract Factory** | Provides an interface for creating families of related objects.           |
| 2     | **Builder**          | Separates object construction from its representation.                    |
| 3     | **Factory Method**   | Creates objects without specifying the exact class to instantiate.        |
| 4     | **Prototype**        | Creates objects by cloning an existing instance.                          |
| 5     | **Singleton**        | Ensures a class has only one instance and provides a global access point. |

---

---

---

### Structural Patterns

Structural patterns focus on composing classes and objects into larger structures while keeping these structures flexible and efficient.

| **#** | **Pattern Name** | **Description**                                                              |
| ----- | ---------------- | ---------------------------------------------------------------------------- |
| 1     | **Adapter**      | Allows incompatible interfaces to work together.                             |
| 2     | **Bridge**       | Decouples an abstraction from its implementation.                            |
| 3     | **Composite**    | Composes objects into tree structures to represent part-whole hierarchies.   |
| 4     | **Decorator**    | Adds new behavior to objects dynamically.                                    |
| 5     | **Facade**       | Provides a unified interface to a set of interfaces in a subsystem.          |
| 6     | **Flyweight**    | Shares objects to support large numbers of fine-grained objects efficiently. |
| 7     | **Proxy**        | Provides a surrogate or placeholder for another object.                      |

---

---

---

### Behavioral Patterns

Behavioral patterns identify common communication patterns between objects to increase flexibility in performing complex tasks.

| **#** | **Pattern Name**            | **Description**                                                                        |
| ----- | --------------------------- | -------------------------------------------------------------------------------------- |
| 1     | **Chain of Responsibility** | Passes a request along a chain of handlers.                                            |
| 2     | **Command**                 | Encapsulates a request as an object.                                                   |
| 3     | **Interpreter**             | Implements a specialized language interpreter for a particular domain.                 |
| 4     | **Iterator**                | Provides a way to sequentially access elements in a collection.                        |
| 5     | **Mediator**                | Defines an object to encapsulate interaction between objects.                          |
| 6     | **Memento**                 | Captures and restores an object's internal state.                                      |
| 7     | **Observer**                | Establishes a one-to-many relationship between objects.                                |
| 8     | **State**                   | Allows an object to change its behavior when its state changes.                        |
| 9     | **Strategy**                | Defines a family of algorithms, encapsulates each one, and makes them interchangeable. |
| 10    | **Template Method**         | Defines the skeleton of an algorithm, deferring some steps to subclasses.              |
| 11    | **Visitor**                 | Separates an algorithm from an object structure on which it operates.                  |
