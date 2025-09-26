---
layout: default
title: Examples
permalink: /inheritance/examples/
---

Now that you've seen the concepts, lets look at some examples of how **Inheritance**, **Composition**, and **Aggregation**.

## 1. Inheritance (Is-A) Example

The `Car` **is a** kind of `Vehicle`. The `Car` automatically gets the `m_speed` attribute from `Vehicle`.

```C++
// Base Class (Superclass)
class Vehicle {
public:
    Vehicle(int speed) : m_speed{ speed } {}
    void accelerate() { m_speed += 10; }
protected:
    int m_speed{};
};

// Derived Class (Subclass) - IS-A relationship
class Car : public Vehicle {
public:
    t  // Car calls the Vehicle constructor
    Car(int speed) : Vehicle(speed) {}

    void honk() {
        std::cout << "Beep beep! Current speed: " << m_speed << "\n";
    }
};

/* Use:
*  Car myCar{50}; // myCar IS-A Vehicle
*  myCar.accelerate();
*/
```

## 2. Composition (Strong Has-A) Example

A `Car` **has an** `Engine`. The `Engine` cannot exist without the `Car`. The `Engine` object is created as a member inside the `Car` class.

```C++
// Part Class
class Engine {
public:
    Engine() {
        std::cout << "Engine created.\n";
    }
    ~Engine() {
        std::cout << "Engine destroyed.\n";
    }
};

// Whole Class - Composition relationship
class Car {
    public:
        // When Car is created, m_engine is automatically created first.
        Car(std::string model) : m_model{ model }, m_engine{} {}

        // When Car goes out of scope, m_engine is automatically destroyed.
private:
    // This Engine object lives *inside* the Car.
    Engine m_engine;
    std::string m_model;
};

/* * Use:
* {
* Car myCar{"Mustang"}; // Prints "Engine created."
* } // myCar goes out of scope. Prints "Engine destroyed."
*/
```

## 3. Aggregation Mechanism (Weak Has-A)

To achieve **Aggregation** in C++, where the `Department` **has a** `Teacher` but doesn't own them, you typically store the independent object using a **pointer or reference**. If you want a collection (like a `std::vector`) of independent objects, C++ provides a `std::reference_wrapper`.

This mechanism allows the `Department` object to hold a link to a `Teacher` without being responsible for the `Teacher`'s lifetime. When the `Department` object is destroyed, the `Teacher` object remains, just like in the real world.
