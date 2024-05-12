# Strategy
The Strategy pattern is a design pattern that allows for dynamic behavior selection at runtime. It defines a family of algorithms, encapsulates each one, and makes them interchangeable within that family.

One common real-world example of the Strategy pattern is sorting algorithms. A Context class might use a different sorting algorithm depending on the size or complexity of the data being sorted. The different sorting algorithms would be implemented as separate Strategy objects that conform to the same interface, and the Context class would switch between them as needed. This allows the Context class to be more flexible and adaptable to different situations, without having to change its implementation.

Suppose you have a program that needs to perform some calculations on a set of numbers. You want to be able to switch between different calculation algorithms (strategies) depending on the user's preference.

First, you'll define an interface that defines the contract for the different calculation strategies:
```csharp
public interface ICalculationStrategy
{
    double Calculate(double[] numbers);
}
````
Next, you'll implement some concrete calculation strategies:
```csharp
public class SumCalculationStrategy : ICalculationStrategy
{
    public double Calculate(double[] numbers)
    {
        double sum = 0;
        foreach (double number in numbers)
        {
            sum += number;
        }
        return sum;
    }
}

public class AverageCalculationStrategy : ICalculationStrategy
{
    public double Calculate(double[] numbers)
    {
        double sum = 0;
        foreach (double number in numbers)
        {
            sum += number;
        }
        return sum / numbers.Length;
    }
}
````
Finally, you'll create a Context class that uses the selected calculation strategy:
```csharp
public class Calculator
{
    private ICalculationStrategy _strategy;

    public Calculator(ICalculationStrategy strategy)
    {
        _strategy = strategy;
    }

    public double Calculate(double[] numbers)
    {
        return _strategy.Calculate(numbers);
    }
}
````
Now you can use the Calculator class to perform calculations using different strategies:
```csharp
double[] numbers = { 1, 2, 3, 4, 5 };
Calculator calculator = new Calculator(new SumCalculationStrategy());
double sum = calculator.Calculate(numbers); // sum = 15

calculator = new Calculator(new AverageCalculationStrategy());
double average = calculator.Calculate(numbers); // average = 3
````