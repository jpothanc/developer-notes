# Solid Principles

Solid principles refer to a set of guidelines for object-oriented programming (OOP) and software design. The acronym SOLID was introduced by Robert C. Martin and stands for:

1. S - Single Responsibility Principle (SRP): A class should have only one reason to change, meaning it should have only one responsibility or single purpose.

```C#
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

2. O - Open/Closed Principle (OCP): A class should be open for extension but closed for modification, allowing for new functionality without modifying existing code.

```C#
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

3. L - Liskov Substitution Principle (LSP): Derived classes should be substitutable for their base classes, ensuring that inheritance maintains the correctness of the program.

4. I - Interface Segregation Principle (ISP): A client should not be forced to depend on interfaces it does not use, promoting smaller, more focused interfaces.

5. D - Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules, but both should depend on abstractions, reducing coupling and increasing flexibility.

These principles aim to promote maintainable, flexible, and scalable software design. Do you have any specific questions about these principles or how to apply them?
