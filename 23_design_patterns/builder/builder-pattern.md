# Builder Pattern

![Builder Pattern](/out/23_design_patterns/builder/builder/builder.png)

The Builder Pattern is a creational design pattern that allows for the construction of complex objects step by step. It separates the construction of a product from its representation so that the same construction process can create different representations.

## Intent

The intent of the Builder pattern is to allow the creation of complex objects by separating the construction process from the object itself. It provides a way to construct an object step-by-step, where the construction logic is handled by a builder, and the client simply instructs the builder on what steps to take.

## Structure

The pattern involves the following components:

- **Builder**: Specifies an abstract interface for creating parts of a product.
- **ConcreteBuilder**: Implements the Builder interface to construct and assemble parts of the product.
- **Director**: Constructs the object using the Builder interface. It guides the builder through the construction process.
- **Product**: Represents the complex object being built.

## Bad Example

In this example, the client directly constructs a complex object, which is not flexible and tightly couples the client with the product creation logic. This violates the intent of the Builder pattern.

```csharp
// Bad Example: Client directly creates a complex object
public class Program
{
    public static void Main()
    {
        // Directly creating a complex object without using the builder
        House house = new House("Wood", 4, 3);
        Console.WriteLine($"House built with {house.Material} material, {house.NumRooms} rooms, and {house.NumFloors} floors.");
    }
}

public class House
{
    public string Material { get; set; }
    public int NumRooms { get; set; }
    public int NumFloors { get; set; }
    
    public House(string material, int numRooms, int numFloors)
    {
        Material = material;
        NumRooms = numRooms;
        NumFloors = numFloors;
    }
}
```

This approach doesn't provide flexibility in constructing complex objects. If we wanted to build a different type of house (e.g., with a garden), we would need to modify the `House` class or the constructor directly, which isn't ideal.

## Good Example

In the good example, the client uses the Builder pattern to construct a complex object step by step, providing flexibility and separation of concerns. The director uses the builder to ensure the proper construction order.

```csharp
// Product
public class House
{
    public string Material { get; set; }
    public int NumRooms { get; set; }
    public int NumFloors { get; set; }
    public bool HasGarden { get; set; }
}

// Abstract Builder
public interface IHouseBuilder
{
    void BuildMaterial();
    void BuildRooms();
    void BuildFloors();
    void BuildGarden();
    House GetResult();
}

// Concrete Builder
public class ConcreteHouseBuilder : IHouseBuilder
{
    private House _house = new House();

    public void BuildMaterial()
    {
        _house.Material = "Brick";
    }

    public void BuildRooms()
    {
        _house.NumRooms = 4;
    }

    public void BuildFloors()
    {
        _house.NumFloors = 2;
    }

    public void BuildGarden()
    {
        _house.HasGarden = true;
    }

    public House GetResult()
    {
        return _house;
    }
}

// Director
public class HouseDirector
{
    private IHouseBuilder _builder;

    public HouseDirector(IHouseBuilder builder)
    {
        _builder = builder;
    }

    public House Construct()
    {
        _builder.BuildMaterial();
        _builder.BuildRooms();
        _builder.BuildFloors();
        _builder.BuildGarden();
        return _builder.GetResult();
    }
}

// Client Code
public class Program
{
    public static void Main()
    {
        IHouseBuilder builder = new ConcreteHouseBuilder();
        HouseDirector director = new HouseDirector(builder);
        
        House house = director.Construct();
        Console.WriteLine($"House built with {house.Material} material, {house.NumRooms} rooms, {house.NumFloors} floors, and garden: {house.HasGarden}");
    }
}
```

## Benefits

- **Separation of concerns**: The builder separates the construction logic from the representation of the product, making the code easier to maintain and extend.
- **Flexibility**: You can construct different types of objects using the same construction process.
- **Complexity management**: The pattern helps manage the complexity of object construction by breaking it into simple steps.
- **Immutability**: The builder ensures that once the object is constructed, it can no longer be modified, which can be beneficial for thread safety.

## When to Use

- When you have a complex object with many optional parts or configurations.
- When the construction process of an object should be independent of the parts that make up the object.
- When you want to create different representations of an object using the same construction process.
- When you need to encapsulate the construction logic from the client code to keep the client code simple and focused on the task at hand.
