# Chain of Responsibility

## Overview
The Chain of Responsibility pattern allows a request to be processed by multiple handlers, one after another. Each handler decides whether to process the request or pass it to the next handler in the chain.

 A Chain of Responsibility can be used to route and process messages through different nodes or components in the system. Each component in the chain can perform specific tasks like validation, transformation, enrichment, etc., before passing the message to the next component.


## Example in C#

```csharp
// Abstract Handler
abstract class FilterBase
{
    protected FilterBase _nextFilter;

    public void SetNext(FilterBase nextFilter)
    {
        _nextFilter = nextFilter;
    }

    public abstract void HandleMsg(DataMsg msg);
}

// Concrete Handlers
class DatabaseQueryFilter : FilterBase
{
    public override void HandleMsg(DataMsg msg)
    {
        //Query database and assign the results to msg
        msg.data = dbresults;
        _nextFilter?.HandleMsg(msg);
    }
}

class DataEnrichmentFilter : FilterBase
{
    public override void HandleMsg(DataMsg msg)
    {
         //Enrich the data received from database.
        _nextFilter?.HandleMsg(msg);
    }
}

class DataValidateFilter : FilterBase
{
    public override void HandleMsg(DataMsg msg)
    {
         //Validate the enriched data
        _nextFilter?.HandleMsg(msg);
    }
}

// Client Code
class Program
{
    static void Main()
    {
        // Set up the chain of handlers
        var dbQueryFilter = new DatabaseQueryFilter();
        var dataEnrichmentFilter = new DataEnrichmentFilter();
        var dataValidateFilter = new DataValidateFilter();
        
        dbQueryFilter.SetNext(dataEnrichmentFilter)
        dataEnrichmentFilter.SetNext(dataValidateFilter);
        
        DataMsg msg = null;
        dbQueryFilter.HandleMsg(msg);l
       
    }
}
```