# Abstract Factory Pattern

![Abstract Factory Pattern](/out/23_design_patterns/abstract_factory/abstract-factory/abstract-factory.png)

The Abstract Factory Pattern is a creational design pattern that provides an interface for creating families of related or dependent objects without specifying their concrete classes. It allows a system to be independent of how its objects are created, composed, and represented.

## Intent

The intent of the Abstract Factory pattern is to provide an interface for creating families of related or dependent objects without specifying their concrete classes. It lets you create objects that belong to the same family, ensuring they are compatible with each other.

## Structure

The pattern involves the following components:

- **Abstract Factory**: Declares an interface for creating abstract product families.
- **Concrete Factory**: Implements the abstract factory interface and creates concrete products.
- **Abstract Product**: Declares an interface for a type of product object.
- **Concrete Product**: Defines a product object that implements the Abstract Product interface.
- **Client**: Uses only abstract interfaces to interact with the abstract factory and products.

## Bad Example

In this example, a client directly creates concrete product objects and is responsible for knowing which family to choose, which violates the intention of the Abstract Factory pattern.

```csharp
// Bad Example: Client directly creates concrete objects
public class Program
{
    public static void Main()
    {
        // Directly creating concrete product objects
        IChair chair = new ModernChair();
        chair.CreateChair();  // Outputs: Modern chair created
        
        ISofa sofa = new VictorianSofa();
        sofa.CreateSofa();  // Outputs: Victorian sofa created
    }
}
```

This approach violates the key principle of the Abstract Factory pattern, which is to abstract the creation of products. Here, the client is tightly coupled to specific product families and must explicitly choose between them, which limits flexibility and extensibility.

## Good Example

In the good example, the client uses abstract factories to create families of products without knowing about their concrete implementations.

```csharp
// Good Example: Using abstract factory to create families of products
// Abstract Product
public interface IChair
{
    void CreateChair();
}

public interface ISofa
{
    void CreateSofa();
}

// Concrete Products
public class ModernChair : IChair
{
    public void CreateChair()
    {
        Console.WriteLine("Modern chair created");
    }
}

public class VictorianChair : IChair
{
    public void CreateChair()
    {
        Console.WriteLine("Victorian chair created");
    }
}

public class ModernSofa : ISofa
{
    public void CreateSofa()
    {
        Console.WriteLine("Modern sofa created");
    }
}

public class VictorianSofa : ISofa
{
    public void CreateSofa()
    {
        Console.WriteLine("Victorian sofa created");
    }
}

// Abstract Factory
public interface IFurnitureFactory
{
    IChair CreateChair();
    ISofa CreateSofa();
}

// Concrete Factory
public class ModernFurnitureFactory : IFurnitureFactory
{
    public IChair CreateChair()
    {
        return new ModernChair();
    }

    public ISofa CreateSofa()
    {
        return new ModernSofa();
    }
}

public class VictorianFurnitureFactory : IFurnitureFactory
{
    public IChair CreateChair()
    {
        return new VictorianChair();
    }

    public ISofa CreateSofa()
    {
        return new VictorianSofa();
    }
}

// Client Code
public class Program
{
    public static void Main()
    {
        // Using Modern Furniture Factory
        IFurnitureFactory modernFactory = new ModernFurnitureFactory();
        IChair modernChair = modernFactory.CreateChair();
        modernChair.CreateChair();  // Outputs: Modern chair created
        
        ISofa modernSofa = modernFactory.CreateSofa();
        modernSofa.CreateSofa();  // Outputs: Modern sofa created
        
        // Using Victorian Furniture Factory
        IFurnitureFactory victorianFactory = new VictorianFurnitureFactory();
        IChair victorianChair = victorianFactory.CreateChair();
        victorianChair.CreateChair();  // Outputs: Victorian chair created
        
        ISofa victorianSofa = victorianFactory.CreateSofa();
        victorianSofa.CreateSofa();  // Outputs: Victorian sofa created
    }
}
```

## Benefits

- **Encapsulation**: The client code does not need to know about the concrete products. It only interacts with the abstract interfaces.
- **Consistency**: Ensures that the products from the same family are used together, which avoids incompatibility issues.
- **Extensibility**: New product families can be added easily without altering the existing client code.

## When to Use

- When the system needs to be independent of how its products are created, composed, and represented.
- When the system should work with multiple families of related products, ensuring consistency.
- When you want to provide a consistent interface to clients while allowing for future extensibility.
