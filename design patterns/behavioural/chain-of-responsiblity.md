# Chain of Responsibility

## Overview
he Chain of Responsibility pattern allows a request to be processed by multiple handlers, one after another. Each handler decides whether to process the request or pass it to the next handler in the chain.

A example of the Chain of Responsibility pattern can be seen in handling different number formats. For instance, consider the requirement to format a number based on different conditions like percentages, currency, or plain numeric format.

### Key Points
- **Multiple Formatters** handle the number based on their specific format type.
- **Sequential Handling** allows each formatter to pass unhandled requests to the next formatter.

## Example in C#

```csharp
// Abstract Handler
abstract class NumberFormatter
{
    protected NumberFormatter _nextFormatter;

    public void SetNext(NumberFormatter nextFormatter)
    {
        _nextFormatter = nextFormatter;
    }

    public abstract void FormatNumber(double number, string formatType);
}

// Concrete Handlers
class PercentageFormatter : NumberFormatter
{
    public override void FormatNumber(double number, string formatType)
    {
        if (formatType == "Percentage")
            Console.WriteLine($"{number:P}");
        else
            _nextFormatter?.FormatNumber(number, formatType);
    }
}

class CurrencyFormatter : NumberFormatter
{
    public override void FormatNumber(double number, string formatType)
    {
        if (formatType == "Currency")
            Console.WriteLine($"{number:C}");
        else
            _nextFormatter?.FormatNumber(number, formatType);
    }
}

class PlainNumberFormatter : NumberFormatter
{
    public override void FormatNumber(double number, string formatType)
    {
        if (formatType == "Plain")
            Console.WriteLine($"{number:F}");
        else
            _nextFormatter?.FormatNumber(number, formatType);
    }
}

// Client Code
class Program
{
    static void Main()
    {
        // Set up the chain of handlers
        var percentageFormatter = new PercentageFormatter();
        var currencyFormatter = new CurrencyFormatter();
        var plainNumberFormatter = new PlainNumberFormatter();

        percentageFormatter.SetNext(currencyFormatter);
        currencyFormatter.SetNext(plainNumberFormatter);

        // Use the chain to format numbers
        double value = 12345.6789;
        percentageFormatter.FormatNumber(value, "Currency");  // Output: $12,345.68
        percentageFormatter.FormatNumber(value, "Percentage"); // Output: 1,234,567.89%
        percentageFormatter.FormatNumber(value, "Plain");      // Output: 12345.68
        percentageFormatter.FormatNumber(value, "Unknown");    // No output, as no handler could process the request
    }
}
