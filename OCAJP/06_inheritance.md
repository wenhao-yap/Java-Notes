# Chapter 6:Working with inheritance <!-- omit in toc -->

[Back to Home](../Readme.md)

## Tables of Content <!-- omit in toc -->

- [Inheritance](#inheritance)
  - [Benefits](#benefits)
  - [Derived Class](#derived-class)
    - [base class members that are inherited](#base-class-members-that-are-inherited)
    - [base class members that are not inherited](#base-class-members-that-are-not-inherited)
  - [Abstract base class versus concrete base class](#abstract-base-class-versus-concrete-base-class)
    - [Inheritance for abstract base class](#inheritance-for-abstract-base-class)
  - [Terms to remember](#terms-to-remember)
- [Interfaces](#interfaces)

## Inheritance

Enables you to reuse code that has already been defined by a class

### Benefits

- smaller derived class definitions
- ease of modification to common properties and behaviour
- extensibility
- used tried and tested code from base class
- concentrate on the specialized behaviour of your classes
- logical structure and grouping
  
### Derived Class

- A derived class can inherit only what it can see
- derived class can hide or override its base class's members

#### base class members that are inherited

- `Default` : accessed in derived class only if the base and derived classes reside in same package
- `Protected` : accessible to all derived classes regardless of the packages
- `Public` : visible to all other classes

#### base class members that are not inherited

- private members of base class
- base class members with default access, if the base class and derived classes exist in seperate packages
- can call a base class's constructors but doesn't inherit them

### Abstract base class versus concrete base class

#### Inheritance for abstract base class

- Can never create objects of an abstract class
- base class can be defined as an abstract class, even if it doesn't define any abstract methods
- A derived class should implement all the abstract methods of its base class. If it doesn't, it must be defined as an abstract derived class
- can use variables of an abstract class to refer to objects  of its derived class

### Terms to remember

- *Base class* : A class inherited by another class
  - Also known as *superclass* or *parent class*
- *Derived class* : A class inherits from another class.
  - Also known as *subclass*, *extended class*, *child class*
- IS-A *relationship* : A relationship shared by base and derived classes

## Interfaces

- Need interfaces to enable multiple classes to support a set of relevant behaviors.  
- Extending is not ideal as irrelevant behaviors will be accessed too and java does not allow a class to inherit from multiple classes
- a class can implement multiple interfaces
- all methods of an interface is implicitly public
- declaration of an inteface can't include class name
- An inteface can never extend any class