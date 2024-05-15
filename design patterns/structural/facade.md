# Facade

The Facade Pattern is a structural design pattern that provides a simplified interface to a complex subsystem. It acts as a high-level interface that makes the subsystem easier to use by hiding its
complexities and providing a simple, unified interface.

## Subsystem Components

Inventory System

```csharp
public class InventorySystem
{
    public void CheckInventory(string productId)
    {
        //Check inventory for product
    }

    public void UpdateInventory(string productId, int quantity)
    {
        //Update inventory for product
    }
}

```

Shipping System

```csharp
public class ShippingSystem
{
    public void ShipProduct(string productId, string address)
    {
        // Shipping logic
    }
}

```

Facade

```csharp
public class OrderFacade
{
    private readonly InventorySystem _inventorySystem;
    private readonly ShippingSystem _shippingSystem;

    public OrderFacade(InventorySystem inventorySystem, ShippingSystem shippingSystem)
    {
        _inventorySystem = inventorySystem;
        _shippingSystem = shippingSystem;
    }

    public void PlaceOrder(string productId, int quantity, string address)
    {
        Console.WriteLine("Placing order...");

        _inventorySystem.CheckInventory(productId);
        _inventorySystem.UpdateInventory(productId, quantity);
        _shippingSystem.ShipProduct(productId, address);

        Console.WriteLine("Order placed successfully!");
    }
}

```

Client

```csharp
 static void Main(string[] args)
    {
        InventorySystem inventorySystem = new InventorySystem();
        ShippingSystem shippingSystem = new ShippingSystem();

        OrderFacade orderFacade = new OrderFacade(inventorySystem, shippingSystem);

        string productId = "prd:1234";
        int quantity = 10;
        string address = "123 Main St, Anytown, USA";

        orderFacade.PlaceOrder(productId, quantity, address);
    }

```
