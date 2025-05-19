# CSharp Design Patterns and Examples Learning Guide

## Overview

### What is this?

This training guide is designed to help you master the fundamental concepts and patterns that will make you a more proficient software developer, particularly in C#. We will begin by covering the basics of **Object-Oriented Programming (OOP)**, providing you with a strong foundation to understand and implement the most common design patterns used in modern software development.

### Object-Oriented Programming Basics

Before diving into design patterns, it is essential to have a strong grasp of **Object-Oriented Programming (OOP)**. OOP is a programming paradigm that revolves around the concept of "objects," which are instances of classes. It is essential to understand the building blocks of OOP, including:

- **Classes and Objects**: Learn how to define and instantiate classes, which act as blueprints for creating objects.
- **Interfaces**: Understand how interfaces define contracts for classes to implement.
- **Methods and Properties**: Gain familiarity with how methods and properties enable data manipulation and behavior within objects.
- **Access Modifiers**: Learn about encapsulation through modifiers such as `public`, `private`, `protected`, and `internal`, which control access to different parts of your program.
- **Instantiating Classes and Interfaces**: Understand how to create objects from classes and how to implement interfaces.

Once you have a strong understanding of these fundamentals, you’ll be well-equipped to learn and apply design patterns.

You can find a starter guide to OOP basics [here](/oop_basics/oop-basics.md).

### Introduction to Design Patterns

**Design patterns** are proven solutions to common problems encountered in software design. They represent best practices that help developers create scalable, maintainable, and flexible software systems. The design patterns we’ll be covering come from the **Gang of Four (GOF)** book, *Design Patterns: Elements of Reusable Object-Oriented Software*, first published in 1994. These patterns are grouped into three categories based on their purpose:

1. **Creational Patterns**: These patterns deal with object creation mechanisms, trying to create objects in a manner suitable to the situation. They abstract the instantiation process, making it more flexible and reusable.
   
2. **Structural Patterns**: These patterns focus on the composition of classes and objects. They help to ensure that complex systems are easier to manage by defining how objects should be organized and related to each other.

3. **Behavioral Patterns**: These patterns are concerned with algorithms and the communication between objects. They help manage complex control flow and object interaction in a system.

In addition to the **Gang of Four** design patterns, we will also explore the **SOLID Principles** of object-oriented design. These principles serve as guidelines for writing clean, maintainable, and scalable code. 

### SOLID Principles

The SOLID principles are a set of five design principles that help improve the structure and readability of code. They are:

1. **Single Responsibility Principle (SRP)**: A class should have only one reason to change, meaning it should have only one job or responsibility.
2. **Open/Closed Principle (OCP)**: Software entities (classes, modules, functions) should be open for extension but closed for modification.
3. **Liskov Substitution Principle (LSP)**: Objects of a superclass should be replaceable with objects of its subclasses without affecting the functionality of the program.
4. **Interface Segregation Principle (ISP)**: Clients should not be forced to depend on interfaces they do not use. This principle advocates for using smaller, specific interfaces rather than large, general ones.
5. **Dependency Inversion Principle (DIP)**: High-level modules should not depend on low-level modules. Both should depend on abstractions. Also, abstractions should not depend on details, but details should depend on abstractions.

These principles, when applied together with design patterns, will help ensure that your C# applications are more maintainable, extensible, and easier to test.

### Learning Path

This guide will take you through the 23 essential design patterns categorized as **Creational**, **Structural**, and **Behavioral**. Each pattern will be explained with real-world examples to demonstrate how it can be applied in C#. By the end of this guide, you will:

- Be able to recognize common software design problems and apply the appropriate design pattern.
- Understand how to create flexible and reusable code using design patterns.
- Apply the SOLID principles to improve the structure of your object-oriented designs.

### 23 Design Patterns

Here are the 23 design patterns grouped into three categories that we will be covering:

#### **Creational Patterns**

- [Abstract Factory](/23_design_patterns/abstract_factory/abstract-factory-pattern.md)
- [Builder](/23_design_patterns/builder/builder-pattern.md)
- [Factory Method](#creational-patterns)
- [Prototype](#creational-patterns)
- [Singleton](#creational-patterns)

#### **Structural Patterns**

- [Adaptor](#structural-patterns)
- [Bridge](#structural-patterns)
- [Composite](#structural-patterns)
- [Decorator](#structural-patterns)
- [Facade](#structural-patterns)
- [Flyweight](#structural-patterns)
- [Proxy](#structural-patterns)

#### **Behavioral Patterns**

- [Chain of Responsibility](#behavioral-patterns)
- [Command](#behavioral-patterns)
- [Interpreter](#behavioral-patterns)
- [Iterator](#behavioral-patterns)
- [Mediator](#behavioral-patterns)
- [Memento](#behavioral-patterns)
- [Observer](#behavioral-patterns)
- [State](#behavioral-patterns)
- [Strategy](#behavioral-patterns)
- [Template Method](#behavioral-patterns)
- [Visitor](#behavioral-patterns)

