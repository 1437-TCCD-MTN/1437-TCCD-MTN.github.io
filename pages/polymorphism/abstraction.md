---
layout: default
title: Abstraction and the Use of Polymorphism
permalink: /polymorphism/abstraction/
---

# Abstraction and the Use of Polymorphism

Dynamic polymorphism is often achieved through **Abstraction.** When the Superclass defines a method that must be implemented by all subclasses, but the Superclass itself has no useful implementation for it, we often refer to that Superclass method as an **Abstract Method.**

This leads to two important design tools:

## Abstract Classes

An **Abstract Class** is a class that is designed only to be a base class (Superclass) and cannot be instantiated on its own. Its purpose is to define a common interface for its subclasses.

* **Example:** The `Shape` class. You can't draw a generic "Shape", but you can draw a `Circle` or `Square`. The `Shape` class can define an abstract method like `calculate_area()`, forcing every subclass (Circle, Square, Triangle) to provide its own specialized way of calculating the area.

## Interfaces

An **Interface** is a pure contract that defines a set of behaviors (methods) that any class can agree to implement. Unlike a class, it contains no implementation and no data (attributes).

* **Example:** An `IPrintable` interface (The 'I' often stands for Interface). Any class that implements `IPrintable` must provide a method called `print_to_screen()`. A `Document` class, a `Photo` class, and a `Report` class can all implement `IPrintable`.

Using an interface, a single function can print any object, regardless of its class, as long as it adheres to the contract:

```bash
FUNCTION print_item(IPrintable item) {
    item.print_to_screen();
}
```

This single function can now take a `Document`, a `Photo`, or a `Report` - because all of them are guaranteed to have a `print_to_screen()` method.
