---
layout: default
title: Encapsulation!
permalink: /encapsulation/
---
# Encapsulation!

By setting up classes with `public` and `private` members, we are able to create a defined interface and implementation for our class. This allows you to use objects of the class, without having to fully understand how they work. Instead, you only have to understand how to interact with them. This reduces the complexity of using these objects, and increases the number of objects we're capable of interacting with.

## Interface and Implementation

**Interfaces** are how a user will interact with the objects of the class. This is the public API that the users will work with, sometimes called the Public Interface.

**Implementation** is the code that actually makes the class work. This includes the member variables and the bodies of the member functions that contain the program logic.

These concepts work through the idea of Data Hiding. This is used to enforce separation of the interface and implementation. When you set the data members of the class to private and the member functions to public, users are only able to interact with the object through its public functions and won't be able to directly access any private data.

This makes the class easier to use, and reduces complexity, since the user doesn't need to know how the class works, they only have to understand the public interface: what functions are available, what arguments they take, and what values they return.

Data hiding also allows for better error detection and handling. When a variable is used or modified, our setters and getters are going to ensure that the data is valid for how the object is supposed to work. You can also be sure that, if there is a bug in how the code is working, you can be sure that it exists only in the setters or getters, not in any of the random places those functions may have been called.

You can also change the implementation details of the class without breaking the public interface. If you need to update how the class is working, for instance storing values in an array instead of as separate variables, users of the interface don't have to change how they're using the objects. You just need to make sure the internal functions are all working with the new implementation.

## To Member Function, or Not to Member Function

Unlike some other object-oriented languages, such as Java and C#, C++ can have both member and non-member functions for classes. A general rule of thumb is to prefer implementing functinos as non-member functions whenever possible, especially if they contain application specific data or logic. The reason for this is to distill the class to only have what is required for that class to function.

### A Helpful Guide On Member or Non-Member

Here's a simple guide on when to go member versus non-member:

- Use a member function when C++ requires it (for example, Constructors, Destructors, Virtual Functions).
- Prefer member function when it requires access to private data that should not be exposed
- Prefer non-member functions otherwise (especially if they don't modify the state of the object).

When designing the class, keep in mind the following:

- If you make a non-member function that needs to access data, adding those access functions requires adding 2 new functions, increasing size and complexity that may not be worth the trade-off of a non-member function.
- Do not add access functions to data that should not be directly accessible or that would allow the user to violate a class invariant.

The last consideration when designing your class is how to structure the order of your data members and functions. The Google C++ Style Guide has the following recommendation:

- Types and Type Aliases (typedef, using, enum, nested structs and classes, and friend types)
- Static Constants
- Factory functions
- Constructors and Assignment operators
- Destructor
- All other functions (static and non-static member functions, and friend functions)
- Data Members (static and non-static)
