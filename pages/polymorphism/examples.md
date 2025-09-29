---
layout: default
title: C++ Examples
permalink: /polymorphism/examples/
---

# C++ Examples

In C++, dynamic polymorphism is enabled using the `virtual` keyword and is often implemented using **pointers** or **references** to the base class.

## C++ Example: Dynamic Polymorphism with `virtual`

To enable dynamic polymorphism, a function in the base class must be declared as `virtual`. This tells the C++ compiler to defer the decision about which function to call until run-time, using a special mechanism called a "virtual table" (v-table).

### C++ Code

```C++
#include <iostream>
#include <vector>
#include <memory>

// Superclass
class Animal {
public:
    // The 'virtual' keyword enables dynamic polymorphism
    virtual void speak() const {
        std::cout << "I am an animal sound.\n";
    }
    // A virtual destructor is crucial for proper cleanup in an inheritance hierarchy
    virtual ~Animal() = default;
};

// Subclass
class Dog : public Animal {
public:
    // Overriding the virtual function
    void speak() const override {
        std::cout << "Woof! Woof!\n";
    }
};

// Subclass
class Cat : public Animal {
public:
    // Overriding the virtual function
    void speak() const override {
        std::cout << "Meow.\n";
    }
};

int main() {
    // A vector designed to hold smart pointers to Animal objects
    // This vector can hold Dog and Cat objects because they IS-A Animal
    std::vector<std::unique_ptr<Animal>> shelter;

    shelter.push_back(std::make_unique<Dog>());
    shelter.push_back(std::make_unique<Cat>());
    shelter.push_back(std::make_unique<Dog>());

    std::cout << "--- Shelter Sounds ---\n";

    // Loop through the collection
    for (const auto& creature : shelter) {
        // Calling speak() on a pointer to the base class (Animal)
        // Dynamic polymorphism ensures the correct (Dog or Cat) speak() is called.
        creature->speak();
    }

    return 0;
}
```

### Output

```bash
--- Shelter Sounds ---
Woof! Woof!
Meow.
Woof! Woof!
```

## Crucial C++ Concepts:

1. `virtual` **Keyword:** You must place `virtual` in front of the base class function (`Animal::speak()`) to signal that it can be overridden.
2. **Base Class Pointer/Reference:** The magic happens when you interact with the derived object through a pointer or reference to the base class (`Animal*` or `Animal&`). This is why `std::unique_ptr<Animal>` is used.
3. `virtual` **Destructor:** Declaring the base class destructor as `virtual` is a **best practice.** It ensures that when you delete a derived class object through a base class pointer (e.g., when the `std::unique_ptr` in the vector is cleaned up), the correct derived class destructor is called first, preventing memory and resource leaks.

