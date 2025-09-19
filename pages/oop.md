---
layout: default
title: Object-Oriented Programming
permalink: /oop/
---
# Everything is an object

Welcome to the world of Object-Oriented Programming, or OOP! As we dive into
using objects, we're shifting from telling a computer exactly what to do, step
by step, and moving to a more intuitive way of thinking about programming:
modeling the world around us. Instead of focusing on lists of instructions,
we'll focus on creating "things" that can hold information and do actions.

## Thinking in Objects

Imagine you're building a video game. You need characters, enemies, items, and
more. In the old way of thinking (procedural programming), you might have a long
list of variables to store a character's health, mana, and name, and then a
separate list of functions to handle their movement and attacks. This can get
messy quickly.

Object-Oriented Programming offers a different solution: we'll create
**objects.** An object is a single, self-contained entity that combines two
things:

- **State (Attributes):** What the object is. This is the data that describes
it. For a `Character` object, it might be `health`, `strength`, `mana`, and
`name`.
- **Behavior (Methods):** What the object does. These are the functions or
actions that the object can perform. For our `Character`, this might be
`attack()`, `run()`, or `heal()`.

Think of an object as a digital version of a real-world object. A car has a
state (color, brand, speed) and behavior (drive, brake, turn). The beauty of
objects is that the data and the functions that operate on that data are bundled
together, making it easier to manage and understand your code.

## The Blueprints: Classess and Structs

While an object is a single "thing", how do we create lots of them without
starting from scratch every time? This is where a **class** comes in.

A **class** is a blueprint for creating objects. It defines the structure of an
object, specifying what attributes and methods all objects of a class will have.
For example, the `Car` class doesn't represent any single car. It defines what
all cars should look like. Once you have the `Car` class, you can create a
specific red `Ford Mustang` and a blue `Toyota Corolla` from it. Each one is a
unique **instance** of the `Car` class, but they all share the same blueprint.

## Hiding the Messy Details: Abstraction

This is where the real power of OOP begins. **Abstraction** is the principle of
hiding the complex inner workings of an object and only showing the essential,
relevant parts.

Going back to our example of a car. When you drive the car you don't need to
know all the details about how the car is working, how the engine uses fuel to
propel the car forward, or how it all responds to the brake or accelerator
pedals being pressed. These mechanics are **abstracted** away from the driver.
All you need to know is that you press the accelerator to move the car, the
brake to stop it, and turn the steering wheel to navigate.

In programming, we apply the same idea. When you create a class, you can choose
which attributes and methods are exposed to the outside world and which are
hidden. This serves two important purposes:

1. **Simplification:** It makes your code easier to use. Other programmers
(or ever your future self) don't have to worry about the complex implementation
details of your object, they only need to know how to use the public methods.
2. **Protection:** It prevents other parts of the program from directly
manipulating the object's data in unintended ways. This makes your code more
robust and less prone to errors.

Now that we've covered the basics of the Object-Oriented Programming paradigm,
let's dig into how these features work in practice.

[Dive into Classes](/classes/)
