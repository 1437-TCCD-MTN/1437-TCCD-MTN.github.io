---
layout: default
title: Stepping into Classes
permalink: /classes/
---
# Stepping into Classes

As we discussed on the previous page, classes are the blueprints by which we
define the objects we will be using in our programs. With a class, you are
defining an entirely new data type, one that is able to hold data and perform
actions on that data. One way of thinking about it is a class is a template,
and objects are variables that are created from that template.

## Defining a Class in C++

If you have used `struct`s in C++, classes are going to be instantly familiar.
You define them the same way, just using the `class` keyword instead of
`struct`. You can see an example below:

```C++
class Rectangle {
public:
    Rectangle() : m_length{0}, m_width{0} {};
    Rectangle(int length, int width) : m_length{length}, m_width{width} {};
    Rectangle(const Rectangle& other) : m_length{other.m_length}, m_width{other.m_width} {};
    ~Rectangle();
    int getLength() { return m_length; }
    int getWidth() { return m_width; }
    void setlength(int length) { m_length = length; }
    void setWidth(int width) { m_width = width; }
    void print(){
        std::cout << "Rectangle: (" << length ", " << width << ")" << std::endl;
    }
private:
    int m_length;
    int m_width;
}
```

The above code snippet defines a rectangle object. This takes in a length and
width and prints them back out.

## So What Is All This Anyway?

Let's briefly break down the code snippet above, we'll cover everything
more comprehensively along the way.

### `Class Rectangle{}`

This is defining the class. It is creating the name of the template for our
new data type, and providing the scope for which everything related to the
class will be defined.

* * *

### Constructors and Destructors

Classes have special functions called Constructors and Destructors that help
with setting up and tearing down your objects as they are used throughout the
code. The Constructors and Destructors have a few things in common:

- They both use the same exact name as the class for their function signature
- They both do not have a return type, not even `void`.

They have a several things that differentiate them:

- You can only have one Destructor per class. You can have as many Constructors
as you want, you just have to follow normal function overloading rules when
defining them.
- Constructors can take arguments, Destructors _cannot_.
- You call Constructors manually when you create an object of the class,
Destructors are called automatically when the object goes out of scope. You can
technically call a Destructor manually, but you should _never_ do this as it can
lead to double deletion of resources and undefined behavior.

#### Constructors

There
are three kinds of constructors that you can use with C++, the default
constructor, parameterized constructor, and the copy constructor.

The default constructor works by taking no parameters, and just initializing
the member values with a default value. In our example, this is
`Rectangle() : m_length{0}, m_width{0} {};`.

The parameterized constructor works like a regular function with parameters,
initializing the values of the member variables with those parameters. In
our example, this is
`Rectangle(int length, int y) : m_length{length}, m_width{y} {};`.

The copy constructor allows you to create an object using the values from an
already elengthisting object. This is useful when you have an object that has most
of the same values you'll be using, allowing you to create the object with those
values and then update just what is different in your new object. In our
example, this is
`Rectangle(const Rectangle& other) : m_length{other.m_length}, m_width{other.m_width} {};`. In general, it is best practice to use an implicit copy
constructor, instead of defining your own. The implicit copy constructor will
initialize the new object with the values of the data members from the old
object.

In each of the constructors, it has three parts. The function signature,
`Rectangle()`, the value initialization, `m_length{0}, m_width{0}`, and finally a function
body. In the function body you can do any other operations you need to set up
the object, but it is optional if all you are doing is initializing the
variables with the parameters passed. This could be used for something like a
`m_area` variable in the class, calculating the area based on the length and
width and initializing the variable with that information, instead of asking it
from the user.

#### Destructors

The primary role of a Destructor is to release any resources that the object
acquired during its lifetime. This is _especially_ crucial when dealing with
_dynamic memory allocation_. If an object allocates memory using `new`, the
destructor _must_ deallocate the memory using `delete` (or `delete[]` for
arrays). If you don't manage the memory this way, it will result in a memory
leak.

* * *

### Access Specifiers

These are the access specifiers that define how outside parts of the program
is able to use the class code. There are three different levels of access
that can be granted.

#### `public`

When creating your class, the general convention is to define your `public`
methods and members first. These members and methods serve as your public
API that anyone who uses your class will be able to see and access.
Members declared as `public` are accessible from anywhere in the program,
both inside and outside of the class.

#### `protected`

The next specifier to define are the `protected` members. These members are
related to inheritance, which is a concept we'll cover later in the semester.

#### `private`

Finally, you will declare your private members. These members are only able
to be accessed from within the class itself, through other member functions
of the class itself. They are hidden from the outside world, and should
be declared last so that users who need your class can skim the top of the
file for the public API and ignore the more complelength implementation details
of your class.

#### Benefits of Access Control

These features are essential for a few reasons:

1. **Data Hiding:** By making data members `private`, you prevent them from
being directly modified from outside the class. This protects the integrity
of the data and prevents accidental corruption. In our example, if we could
only have Rectangles that are positive values, having the `m_length` and
`m_width` variables private means we can restrict modifications to the variables
so that only a function in the class can edit them, allowing us to check
the new values and ensure they are valid.
2. **Encapsulation:** Access control helps enforce the principle of
encapsulation, ensuring that objects manage their own internal state.
3. **Code Maintainability:** It makes your code easier to maintain and modify
because as long as your public API remains the same, you can change the internal
implementation of the class without affecting other parts of the program.
4. **Abstraction:** Access control allows you to present a simplified view
of a class to the outside world, hiding the complex internal details so that
users of your class can get right to using it, without worrying about how it
all works.

* * *

### Data Members

In a class, you declare the data members, then initialize them in the constructor or through setter functions. The general convention is to preface the data member variables with `m_` so that you can differentiate between passed in parameters and private data members. If you look at the constructor in our example, this allows us to initialize `m_length` with `length`, without risk of confusing the two variables.

* * *

### Access Functions

Let's consider how our Access Specifiers are working with our class objects.
Since we have `m_x` and `m_y` as private members, they can't be accessed by code
outside of the class itself. So, how do we modify them? The answer is Access
Functions. These functions allow us to explicitly define the rules that are in
place when working with the data members of our class.

There are two types of Access Functions:

- **Getters (Access Functions):** These functions _retrieve_ the value of a
private data member. They typically have a `get` prefix followed by the member
variable's name (`getWidth()`).
- **Setters (Mutator Functions):** These functions _modify_ the value of a
private data member. They usually have a `set` prefix followed by the member's
name (`setWidth()`).

With access function, you can return constant lvalue references instead of copying the value, which is useful for when data members are large or expensive to copy. You can also define getters with `auto` to help prevent unneccessary conversions of types, for example:

`const auto& getName() const {return m_name;}`

The downside here is that it obscures what the return type is from a documentation perspective, so be sure to include comments that indicates the return type when using this.

{% include callout.html content="**Best Practice**<br/><br/>Prefer to use the return value of a member function that returns by reference immediately, to avoid issues with dangling references when the implicit object is an rvalue." type="success" %}

#### Naming Conventions

The points above list the general conventions for naming these functions, but,
as always, use what makes sense. In a text adventure game (just as a completely
random, unrelated example), it may make more sense for functions that modify
the name of the player to be called `rename()` instead of `setName()`. Or to
modify their gold amount, `spendGold()` or `addGold()`.

In general, Boolean getters will often start with `is` or `has`, for example
`isAlive()`, `hasQuestItem()`.

#### Why Use Access Functions?

There are a few reasons that having these functions available comes in handy:

1. **Controlled Access:** Access functions act as gatekeepers, allowing you to
strictly control how and when a private data member is accessed or modified.
2. **Validation:** Setters can include validation logic (such as making sure
you have enough gold before spending it) to ensure that only valid values are
assigned to a data member.
3. **Flexibility:** You can change the internal implementation of how data is
stored or retrieved without affecting the code that uses the class, as long
as the interface of the access function remains the same.
4. **Read-Only or Write-Only Access:** You can create read-only properties by
only providing a getter and no setter, or write-only properties by providing
only a setter and no getter.

{% include callout.html content="**Best Practices:**<br/><br/>If your class has no invariants and requires a lot of access functions, consider using a struct (whose data members are public) and providing direct access to members instead.<br/><br/>You should also prefer to implement behaviors or actions instead of access functions. For example, instead of `setAlive(bool)` setter, use `kill()` and `revive()`.<br/><br/>Only provide access functions in cases where the public would reasonably need to get or set the value of an individual member." type="success" %}

[Moving on to Encapsulation!](/encapsulation/)