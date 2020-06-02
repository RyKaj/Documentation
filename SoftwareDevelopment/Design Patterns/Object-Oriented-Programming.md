<div id="main" class="aui-page-panel">

<div id="main-header">

<div id="breadcrumb-section">

1.  [Information Technology](index.html)
2.  [3.0 Sofware Development
    Lifecycle](3.0-Sofware-Development-Lifecycle_380470491.html)
3.  [Design Patterns](Design-Patterns_451820045.html)



# Information Technology : Object-Oriented Programming - OOP



## General

To discuss about the object-oriented programming (abbreviate **OOP**) we
need to become reading the definition of this on Wikipedia:

> **Object-oriented programming** (**OOP**) is a [programming
> paradigm](https://en.wikipedia.org/wiki/Programming_paradigm) based on
> the concept of “
> [objects](https://en.wikipedia.org/wiki/Object_\(computer_science\))”,
> which can contain [data](https://en.wikipedia.org/wiki/Data), in the
> form of
> [fields](https://en.wikipedia.org/wiki/Field_\(computer_science\))
> (often known as *attributes),* and code, in the form of procedures
> (often known as
> [*methods*](https://en.wikipedia.org/wiki/Method_\(computer_science\))*).*

We will try to analyze the four principles of the definition of the OOP:

  - **Programming paradigm**: anyone could think that the OOP is itself
    a programming language, but the definition express that the OOP is a
    paradigm of programming. The paradigm show the way to realize your
    application with a focus on a entity that became the main concept of
    the programming: the object.
  - **Object**: the object is the digital representation of the reality.
    Every things that you see is representable (or programmable) as an
    object. The object, like many other things, follow a life-cycle; in
    fact the object born, live and died: yes, LIVE\! The object can be
    defined in a file that commonly is called class, but is live through
    an instance of himself.
  - **Fields (or attributes)**: every object has proper characteristics
    that permit to define its appearance. The fields collect information
    about objects that can be represented in different form or type.
    There is the type to express textual string or numerical information
    or at most a date.
  - **Methods**: when the object is instantiated it is life, but to
    animate it we need to use the methods. With the method is possible
    to evolve the information contained in the object. The invocation of
    a method on an instance of the object can update the information
    contained into the fields or request to the object to make an action
    on himself or to another object.

The objects instantiated are like a file in a file cabinet: every object
is a drawer in the file cabinet; if you open the drawer you can get the
information contained into the object and manage it.

### The power of the OOP languages

In the last sixty years the paradigm of the OOP was widely stressed and
we assisted at born and diffusion of many languages based on the OOP
paradigm.

The power of the OOP languages reside in three key concepts:
flexibility, modularity and representation of the reality. Now we will
try to discuss about these three concepts and the application on the
programming language.

The **flexibility** is the first key concept that we will analyze. The
OOP born to be used on different development scenarios; the presence of
the objects that represent the concepts of the scenario of application
emphasizes this concept: it is possible, with the same language based on
OOP define a library structure or the halls of a cinema or the
supermarket products. So every real concept is achievable with an
extension of object and the application in different contest make the
OOP a flexible paradigm.

The second key concept is the **modularity**. The OOP paradigm agrees to
the definition of objects and every object can interact with other
objects creating a hierarchy. If this hierarchy of objects realizes a
functional sylos this is identifiable like a module or most commonly a
library. The possibility to realize, include and use library write by
third part agree to realize applications very quickly; otherwise the
developer need to realize the functionality included into the external
libraries. The maximum expression of the library is the framework that
collect a lot of library to provide a wide set a function.

The last concept is the **representation of the reality**. This concept
is at the base of the flexibility; the OOP represent a reality, but it
also can represent most than a single reality: so the it is flexible.
With the objects, attributes and methods orchestrate by programming
paradigm we can realize a digital representation of the reality: a DVD
becomes an object, a title becomes an attribute, watching the film
becomes an action or more simply a method. With the OOP changed the way
to design the application and also changed the way to think programming.

### How the OOP change the way of think programming

Before dissemination of the object-oriented programming languages, the
developers were used to think programming basing on procedural
languages. The procedural languages, that are diffused also today, are
most different than the OOP because follow a paradigm based on function,
routine or subroutine interconnected.

With the introduction and diffusion of the OOP languages the software
engineer, the architect, the developer or the tester has needed to
change the way to make applications.

The OOP architect has needed to think a new way to design and put in
communication the objects: these approach has given rise for example to
the born of the famous Design Patterns. On the other hand the OOP
introduced new problems and new issues ( *from abend to exception…*).

A developer has needed to changes the metric on which realize the
software: the developer had need to minimize the number of MIPS of his
software wrote with a procedural language and that run on Mainframe
while for the OOP languages, the same developer, had need to think the
software optimizing the number of instances of object contained in
memory.

There have been [many attempts](http://c2.com/cgi/wiki?DefinitionsForOo)
to define OOP and a widely accepted definition to classify a programming
language as Object  
Oriented is based on two requirements:

  - its capability to model a problem through objects
  - its support of a few principles that grant modularity and code reuse

## Capability to Model a Problem through Objects

### Association

This is the object’s capability to refer another independent object

### Aggregation

This is the object’s capability to embed one or more independent objects

### Composition

This is the object’s capability to embed one or more dependent objects

### Abstraction

Abstract means a concept or an Idea which is not associated with any
particular instance. Using abstract class/Interface we express the
intent of the class rather than the actual implementation. In a way, one
class should not know the inner details of another in order to use it,
just knowing the interfaces should be good enough.

Data abstraction is the simplest of principles to understand. Data
abstraction and encapuslation are closely tied together, because a
simple definition of data abstraction is the development of classes,
objects, types in terms of their interfaces and functionality, instead
of their implementation details. Abstraction denotes a model, a view, or
some other focused representation for an actual item. Its the
development of a software object to represent an object we can find in
the real world. Encapsulation hides the details of that implementation.

Each of these library’s assets should be represented by its own class
definition.  Without inheritance though, each class must independently
implement the characteristics that are common to all loanable assets. 
All assets are either checked out or available for checkout.  All assets
have a title, a date of acquisition and a replacement cost.  Rather than
duplicate functionality, inheritance allows you to inherit functionality
from another class, called a superclass or base class.

## Support of a few principles that grant modularity and code reuse

### Encapsulation

Encapsulation is the mechanism of hiding of data implementation by
restricting access to public methods. Instance variables are kept
private and accessor methods are made public to achieve this.

It is the hiding of data implementation by restricting access to
accessors and mutators.

#### Accessor

An accessor is a method that is used to ask an object about itself. In
OOP, these are usually in the form of properties, which have, under
normal conditions, a *get* method, which is an accessor method. However,
accessor methods are not restricted to properties and can be any public
method that gives information about the state of the object.

#### Mutator Mutators

Are public methods that are used to modify the state of an object, while
hiding the implementation of exactly how the data gets modified.
Mutators are commonly another portion of the property discussed above,
except this time its the set method that lets the caller modify the
member data behind the scenes.

### Inheritance

Inheritances expresses “is-a” and/or “has-a” relationship between two
objects. Using Inheritance, In derived classes we can reuse the code of
existing super classes. In Java, concept of “is-a” is based on class
inheritance (using `extends`) or interface implementation (using
`implements`).

Now lets discuss inheritance.  Objects can relate to eachother with
either a “has a”, “uses a” or an “is a” relationship.  “Is a” is the
inheritance way of object relationship.  The example of this that has
always stuck with me over the years is a library (I think I may have
read it in something Grady Booch wrote).  So, take a library, for
example.  A library lends more than just books, it also lends magazines,
audiocassettes and microfilm.  On some level, all of these items can be
treated the same: All four types represent assets of the library that
can be loaned out to people.  However, even though the 4 types can be
viewed as the same, they are not identical.  A book has an ISBN and a
magazine does not.  And audiocassette has a play length and microfilm
cannot be checked out overnight.

### Polymorphism

It means one name many forms. It is further of two types — static and
dynamic. Static polymorphism is achieved using method overloading and
dynamic polymorphism using method overriding. It is closely related to
inheritance. We can write a code that works on the superclass, and it
will work with any subclass type as well.

Polymorphism means one name, many forms.  Polymorphism manifests itself
by having multiple methods all with the same name, but slighty different
functionality.  Many VB6ers are familiar with interface polymorphism. 
I’m only going to discuss polymorphism from the point of view of
inheritance because this is the part that is new to many people. 
Because of this, it can be difficult to fully grasp the full potential
of polymorphism until you get some practice with it and see exactly what
happens under different scenarios.  We’re only going to talk about
polymorphism, like the other topics, at the basic level.

There are 2 basic types of polymorphism.  Overridding, also called
run-time polymorphism, and overloading, which is referred to as
compile-time polymorphism.  This difference is, for method overloading,
the compiler determines which method will be executed, and this decision
is made when the code gets compiled. Which method will be used for
method overriding is determined at runtime based on the dynamic type of
an object.

References

  - [Medium - What are four basic principles of Object Oriented Programming?](https://medium.com/@cancerian0684/what-are-four-basic-principles-of-object-oriented-programming-645af8b43727)
  - [Code Better - 4 major principles of Object-Oriented  Programming](http://codebetter.com/raymondlewallen/2005/07/19/4-major-principles-of-object-oriented-programming/)
  - [Medium - The miracle of object oriented programming](https://medium.com/quick-code/the-miracle-of-object-oriented-programming-837c3b1f1e59)
  - [Medium - Is javascript a true oop language](https://medium.com/@andrea.chiarelli/is-javascript-a-true-oop-language-c87c5b48bdf0)

