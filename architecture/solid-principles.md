# Solid Principles

As a junior developer, I often questioned the value of design patterns and was likely naive about writing scalable and flexible code. Over time, as I worked on larger projects, my perspective evolved. I discovered Robert C. Martin's (Uncle Bob) insightful and valuable speeches on YouTube, covering a wide range of topics such as Clean Code, Architecture, Agile Software Development, Ethics in Software Development, and SOLID Principles. He is a humorous and relatable orator who truly connects with his audience. If you haven't read or listened to him, I highly recommend doing so.

The _SOLID principles_ are five design guidelines in object-oriented programming intended to make software designs more maintainable, scalable, reusable, testable, and flexible. These principles not only promote high-quality code but also facilitate a more adaptive and efficient development process, accommodating changes and growth with less friction.

This article is motivated by the observation that many senior programmers still routinely flout these principles, often resulting in duplicated and inflexible code.

I believe, every software developer should strive to incorporate this into their daily practice.

Let's dive in...

1. **S - Single Responsibility Principle (SRP)**: A class should have only one reason to change, meaning it should have only one responsibility or single purpose.

```csharp
// Bad example: A class responsible for both data access and validation

internal class OrderService
{
    public void SaveOrder(Order order)
    {
        //Code to validate
        //Code to Save
    }
}

//Good Example
internal class OrderRepository
{
    private readonly IOrderValidator validator;

    public OrderRepository(IOrderValidator validator)
    {
        this.validator = validator;
    }
    public void SaveOrder(Order order)
    {
        if (validator.ValidateOrder(order))
        {
            //Code to Save
        }
    }
}

internal interface IOrderValidator
{
    bool ValidateOrder(Order order);
}
internal class OrderValidator
{
    public bool ValidateOrder(Order order)
    {
        //Code to validate
        return true;
    }
}

```

2. **O - Open/Closed Principle (OCP)**: A class should be open for extension but closed for modification, allowing for new functionality without modifying existing code.

```csharp
// Bad example: Modifying existing code to add a new payment method
public class PaymentProcessor
{
    public void ProcessPayment(Order order, PaymentMethod paymentMethod)
    {
        if (paymentMethod == PaymentMethod.CreditCard)
        {
            // Code for credit card payment
        }
        else if (paymentMethod == PaymentMethod.PayPal)
        {
            // Code for PayPal payment
        }
        // Code for other payment methods
    }
}

// Good example: Extending functionality through abstraction and inheritance
public abstract class PaymentProcessor
{
    public abstract void ProcessPayment(Order order);
}

public class CreditCardPaymentProcessor : PaymentProcessor
{
    public override void ProcessPayment(Order order)
    {
        // Code for credit card payment
    }
}

public class PayPalPaymentProcessor : PaymentProcessor
{
    public override void ProcessPayment(Order order)
    {
        // Code for PayPal payment
    }
}

```

3. **L - Liskov Substitution Principle (LSP)**: Derived classes should be substitutable for their base classes, ensuring that inheritance maintains the correctness of the program.

4. **I - Interface Segregation Principle (ISP)**: A client should not be forced to depend on interfaces it does not use, promoting smaller, more focused interfaces.

5. **D - Dependency Inversion Principle (DIP)**: High-level modules should not depend on low-level modules, but both should depend on abstractions, reducing coupling and increasing flexibility.

Happy Coding....
