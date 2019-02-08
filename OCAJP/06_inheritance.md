# Chapter 6: Working with inheritance <!-- omit in toc -->

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
  - [Interface declaration](#interface-declaration)
    - [Valid Access modifiers for an interface](#valid-access-modifiers-for-an-interface)
    - [Valid Access modifiers for members for an interface](#valid-access-modifiers-for-members-for-an-interface)
    - [Valid non-access modifier for an interface](#valid-non-access-modifier-for-an-interface)
  - [Methods in interface](#methods-in-interface)
    - [1. abstract](#1-abstract)
    - [2. default](#2-default)
    - [3. static](#3-static)
  - [Implementing single interface](#implementing-single-interface)
    - [Implement abstract methods](#implement-abstract-methods)
    - [Overriding default methods](#overriding-default-methods)
    - [Static methods](#static-methods)
  - [Implementing multiple interfaces](#implementing-multiple-interfaces)
    - [same constant names](#same-constant-names)
    - [same abstract method names](#same-abstract-method-names)
    - [same default method names](#same-default-method-names)
    - [same static method names](#same-static-method-names)
  - [Extending multiple interfaces](#extending-multiple-interfaces)
    - [extend with same abstract method names](#extend-with-same-abstract-method-names)
    - [extend with same default method names](#extend-with-same-default-method-names)
    - [extend with same static method names](#extend-with-same-static-method-names)
  - [Modifying existing methods of an interface](#modifying-existing-methods-of-an-interface)

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
- interface cannot define constructor unlike class

### Interface declaration

- declaration of an inteface can't include class name
- An inteface can never extend any class

#### Valid Access modifiers for an interface

You can declare a **top-level interface** with only public and no modifier(default access). Any other modifier will result in compilation error.  
Inner or nested types can be declared using any access level

#### Valid Access modifiers for members for an interface

All members of an interface(eg. variables,inner interfaces) are inherently public because that's the only modifier they can accept.

``` java
interface MyInterface {
  int AGE; //won't compile; should assign value to final variable
  private int number = 10;  //won't compile
  protected void aMethod();  //wont't compile
  //Interace2 is implicitly prefixed with public
  interface interface2{}
  //Interface member can be prefixed with public
  public interface interface4{}
}
```

#### Valid non-access modifier for an interface

- abstract
- strictfp : floating-point calculations identical cross-platform

**Invalid modifiers(won't compile)**: final, static, transient, synchronized, volatile

### Methods in interface

Methods of an interface are implicity public. A class that implements an interface can't make the interface's methods more restrictive

#### 1. abstract

specify a behavior(set of methods), which must be defined by the class that implements it. It is defined without a method body.  
keyword *abstract* is optional as interface methods are implicitly abstract

#### 2. default

require keyword *default*  
Implementing classes might choose to override or use the default method from interface

``` java
interface Interviewer {
  abstract void conductInterview();
  default void submitInterviewStatus(){
    System.out.println("Accept");
  }
}
```

#### 3. static

- Enable you to define utility methods in the interfaces that they belong to
- Accessed by interface name and not reference variable unlike *static* method in base class that can be accessed by both

### Implementing single interface

#### Implement abstract methods

*abstract* method of interface must be implemented using access modifier *public*

#### Overriding default methods

While overriding a default method, you must not use the keyword *default*. Rules for overriding default and regular methods are the same

#### Static methods

*static* methods in a class and the interface that it implements are not related to each other (i.e. *static* method in class doesn't hide or override the *static* method in the interface that it implements)

### Implementing multiple interfaces

#### same constant names

a class can implement multiple interfaces with same constant name, as long as a call to these interfaces is not ambiguous.  
i.e. prefixed with the interface name eg. Jumpable.MIN_DISTANCE

#### same abstract method names

a class can implement multiple interfaces with the same *abstract* method names if they have the same signature or form an overloaded set of methods

#### same default method names

a class can implement multiple interfaces with same *default* method name and signature, if it overrides its default implementation.

#### same static method names

a class can implement multiple interfaces with same static method names, irrelevant of their return types or signature

### Extending multiple interfaces

Resolution rules in case of  multiple inheritance:

1. classes always win: a method implemented in a class always has priority over an interface default method
2. Otherwise, subinterfaces always win
3. Otherwise, the targeted superinterface must be specified using the *super* keyword *eg. BaseInterface1.super.getName()*

#### extend with same abstract method names

an abstract method doesn't define a body, hence the question of which methods inherited is irrelevant

#### extend with same default method names

Java ensures that it shouldn't inherit multiple method implementations for the same method. Will result in compilation error unless override default method

``` java
interface BaseInterface1{
  default void getName(){ System.out.println("Base 1"); }
}
interface BaseInterface2{
  default void getName(){ System.out.println("Base 2"); }
}
//compile successful if default implementation is override
interface MyInterface extends BaseInterface1,BaseInterface2 {
  default void getName(){ System.out.println("Just me"); }
}
```

#### extend with same static method names

static methods are never inherited so no conflicts can occur

### Modifying existing methods of an interface

- **static -> default** : code that calls the method won't compile
- **static -> abstract** : implementing class might not compile
- **abstract -> default** : code compile
- **abstract -> static** : code that calls the method won't compile. This is because static methods of an interface are called by prefixing the method name with interface name
- **default -> abstract** : class that implements might fail to compile if it doesn't override the default method of the interface
- **default -> static** : code that calls the method won't compile
