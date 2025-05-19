# Object Oriented Programming Basics

Object Oriented Programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data (attributes or properties) and code (methods or functions). It allows for modular and reusable code, making it easier to manage and update large software systems.

## What Are Classes

Classes are the fundamental building blocks of OOP in C#. They are blueprint templates that define the properties and behaviors (methods) of objects. In simpler terms, a class is like a blueprint from which objects are created.

```csharp
// Example of a class in C#
public class Car
{
    // Properties
    public string Make { get; set; }
    public string Model { get; set; }
    public int Year { get; set; }
    
    // Constructor
    public Car(string make, string model, int year)
    {
        Make = make;
        Model = model;
        Year = year;
    }
    
    // Method
    public void Start()
    {
        Console.WriteLine($"Starting {Year} {Make} {Model}");
    }
}
```

## What are Access Modifiers, details of each and examples

Access modifiers control the visibility and accessibility of classes, methods, and properties in C#. There are four main access modifiers:

- **public**: Accessible from anywhere, both within the same assembly and from other assemblies.
- **private**: Accessible only from within the same class or struct.
- **protected**: Accessible only from within the same class or from derived classes.
- **internal**: Accessible only from within the same assembly (project).

```csharp
public class ExampleClass
{
    public int PublicProperty { get; set; } // Accessible from anywhere
    
    private string PrivateField; // Accessible only within this class
    
    protected void ProtectedMethod() // Accessible within this class and derived classes
    {
        // Method implementation
    }
    
    internal void InternalMethod() // Accessible within the same assembly
    {
        // Method implementation
    }
}
```

### What is `virtual` in C# and how does it relate to Access Modifiers?

The `virtual` keyword in C# is used to declare a method, property, or event that can be overridden in a derived class. It is used in conjunction with access modifiers like `public`, `protected`, or `private` to control the visibility and behavior of the member.

- A `virtual` method or property has a default implementation that can be overridden in subclasses using the `override` keyword.
- The access modifier determines the visibility of the method or property, while `virtual` enables polymorphism, allowing derived classes to change the behavior.

### Example:
```csharp
public class BaseClass
{
    public virtual void Greet()
    {
        Console.WriteLine("Hello from the base class!");
    }
}

public class DerivedClass : BaseClass
{
    public override void Greet()
    {
        Console.WriteLine("Hello from the derived class!");
    }
}

public class Program
{
    public static void Main()
    {
        BaseClass obj = new DerivedClass();
        obj.Greet();  // Outputs: Hello from the derived class!
    }
}
```

The `virtual` keyword can be used with other access modifiers like `protected` or `internal` to control accessibility, while still allowing derived classes to override the method:

```csharp
public class BaseClass
{
    // Virtual method with protected access modifier
    protected virtual void Display()
    {
        Console.WriteLine("Base class display");
    }
}

public class DerivedClass : BaseClass
{
    // Override the virtual method in the derived class
    public override void Display()
    {
        Console.WriteLine("Derived class display");
    }
}

public class Program
{
    public static void Main()
    {
        BaseClass obj = new DerivedClass();
        obj.Display();  // Outputs: Derived class display
    }
}
```

## What are Class Properties and examples

Class properties are variables defined within a class that store data related to objects of the class. They are typically accessed using getters and setters (also known as accessors and mutators) to read from and write to the private fields.

```csharp
public class Person
{
    private string name;
    public string Name
    {
        get { return name; }
        set { name = value; }
    }
    
    private int age;
    public int Age
    {
        get { return age; }
        set { age = value; }
    }
    
    // Constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}
```

## What are Class Methods and Examples

Class methods are functions defined within a class that perform operations on class data. They encapsulate behaviors that objects of the class can perform.

```csharp
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
    
    public double Divide(double a, double b)
    {
        if (b != 0)
            return a / b;
        else
            throw new DivideByZeroException("Cannot divide by zero.");
    }
}
```

## How to create Objects from Classes and examples

Objects are instances of classes created using the `new` keyword followed by the class constructor. Objects hold their own copy of properties defined in the class.

```csharp
public class Program
{
    public static void Main()
    {
        // Creating objects from classes
        Car myCar = new Car("Toyota", "Camry", 2023);
        myCar.Start(); // Outputs: Starting 2023 Toyota Camry
        
        Person person = new Person("Alice", 30);
        Console.WriteLine($"Name: {person.Name}, Age: {person.Age}"); // Outputs: Name: Alice, Age: 30
        
        Calculator calc = new Calculator();
        int sum = calc.Add(5, 3); // sum = 8
        double result = calc.Divide(10.0, 2.0); // result = 5.0
    }
}
```
