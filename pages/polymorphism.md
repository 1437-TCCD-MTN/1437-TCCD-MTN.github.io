---
layout: default
title: Polymorphism
permalink: /polymorphism/
---

# Polymorphism

This week, we reach the final and most powerful concept in object-oriented programming: **Polymorphism.** The word comes from Greek: **"Poly"** means many, and **"morph"** means form. Therefor, Polymorphism literally means **"many forms."**

In OOP, polymorphism allows us to treat objects of different classes in a uniform way, often by using a common base class or interface. It enables your program to perform an action on an object, and have the program automatically select the appropriate, specific behavior for that object's actual type.

---

## Static vs. Dynamic Polymorphism

Polymorphism comes in two main forms in most object-oriented languages:

### Static Polymorphism (Method Overloading)

**Static Polymorphism** (also known as Compile-time Polymorphism) is the simplest form. It is achieved when a class has multiple functions or methods with the **same name,** but a **different list of parameters** (either in the number of parameters or their data types).

The compiler figures out which function to call based on the arguments you provide. This decision happens statically, before the program even runs.

#### Pseudocode Example: Overloading the `Add` Method

```bash
CLASS Calculator
    METHOD Add(num1: Integer, num2: Integer) RETURNS Integer
        RETURN num1 + num2
    END METHOD

    METHOD Add(num1: Decimal, num2: Decimal) RETURNS Decimal
        RETURN num1 + num2
    END METHOD

    METHOD Add(num1: Integer, num2: Integer, num3: Integer) RETURNS Integer
        RETURN num1 + num2 + num3
    END METHOD
END CLASS
```

---

### Dynamic Polymorphism (Method Overriding)

**Dynamic Polymorphism** (or Run-Time Polymorphism) is the more powerful and central concept of OOP. It occurs when a subclass provides a specific implementation for a method that is already defined in its superclass.

This relies entirely on the **"Is-A"** relationship (Inheritance) you learned about last week.

* **Scenario:** You have an `Animal` Superclass with a method called `speak()`.
* The `Dog` Subclass **overrides** `speak()` to say "Woof!"
* The `Cat` Subclass **overrides** `speak()` to say "Meow."

The magic of dynamic polymorphism is that the program doesn't care what kind of animal you have, it just knows it has an `Animal`. When you tell the `Animal` object to `speak()`, the program looks at the object's actual type (`Dog` or `Cat`) at the moment the code runs and executes the correct, specialized version. This decision is made dynamically.

#### Example

```bash
CLASS Animal
    METHOD Speak()
        DISPLAY "I am an animal sound."
    END METHOD
END CLASS

// Dog IS-A Animal
CLASS Dog INHERITS Animal
    METHOD Speak()
        DISPLAY "Woof! Woof!"
    END METHOD
END CLASS

// Cat IS-A Animal
CLASS Cat INHERITS Animal
    Method Speak()
        DISPLAY "Meow."
    END METHOD
END CLASS
```
