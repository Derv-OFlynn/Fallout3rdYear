OOP is a way of writing programmes

An object is an abstraction of something in the **problem domain** e.g. Table

<mark style="background: #FFB8EBA6;">Purpose:</mark>
- promotes an understanding of the real world
- Provides a practical basis for computer implementation

<mark style="background: #FFB8EBA6;">Characteristics:</mark>
- State
- Behaviour
- Identity

![](https://i.imgur.com/xQzOKfN.png)


<mark style="background: #FFB8EBA6;">Three Pillars of OOP:</mark>
- Encapsulation
- Inheritance
- Polymorphism

### <mark style="background: #FFB8EBA6;">Encapsulation:</mark>

Fundamentally, <mark style="background: #FFB8EBA6;">encapsulation</mark> is a simple concept – hide the internals (data & behaviour) of an object from other objects

Fundamentally, encapsulation is a simple concept – hide the internals (data & behaviour) of an object from other objects.  

With this, we can then control the access to the object’s internals whatever way we want. Also, we can implement and modify the implementation without affecting other objects (i.e. the rest of the system)

Private variables can only be access through the methods provided

![](https://i.imgur.com/15pSpAz.png)


Client objects can be thought of as sending messages to other objects when calling methods

![](https://i.imgur.com/Lsxh5Rn.png)

<mark style="background: #FFB8EBA6;">Interfaces:</mark> Defines how one object is allowed to interact with another object.

An object’s <mark style="background: #FFB8EBA6;">interface</mark> is the set of publicly accessible operations.  

It is worth mentioning here that there is generally no need to automatically generate the accessor (getter) and mutator (setter) methods for a private member variable (something that development tools might do). They should only exist if other objects need to get/set/change the variable – this is often the case but not always.

![](https://i.imgur.com/CMgrQ9G.png)

### <mark style="background: #FFB8EBA6;">Inheritance:</mark>

A class (<mark style="background: #FFB8EBA6;">subclass</mark>) can extend another class (the <mark style="background: #FFB8EBA6;">superclass</mark>)

The subclass inherits the methods of the superclass by implementing its own version of the method.

The subclass may override a method in the superclass by implementing its own version of the method. The new version may call the method of the superclass.

Enables subtype <mark style="background: #FFB8EBA6;">Polymorphism</mark>.

![](https://i.imgur.com/avYUyRZ.png)

Methods from the superclass can be overridden in the subclass.

The superclass is a <mark style="background: #FFB8EBA6;">generalisation</mark> and the subclass is a <mark style="background: #FFB8EBA6;">specialisation</mark> "is-a" relationship.

The terms <mark style="background: #FFB8EBA6;">base class</mark> and <mark style="background: #FFB8EBA6;">derived class</mark> are also used for the superclass and subclass, respectively.
A class diagram is intended to give a clear picture of the classes in a system and the relationships between them.

<mark style="background: #FFB8EBA6;">Note:</mark> In Java, every class has the class Object as a superclass, i.e. class Object is the root of  the class hierarchy in Java. See the API documentation.

<mark style="background: #FFB8EBA6;">Note:</mark> 
- <mark style="background: #FFB8EBA6;">Statically typed</mark> languages: check types of variables at compile-time and enforce constraints.  
- <mark style="background: #FFB8EBA6;">Dynamically typed</mark> languages: check types at run-time.  
- <mark style="background: #FFB8EBA6;">Strongly typed</mark> languages: do not allow implicit conversions between types.  
- <mark style="background: #FFB8EBA6;">Weakly typed</mark> languages: will perform implicit conversions between different types.  

E.g.  
Java / C# - Statically and Strongly typed  
Python – Dynamically and Strongly typed  
C++ - Statically and Weakly typed  
JavaScript - Dynamically and Weakly typed

### <mark style="background: #FFB8EBA6;">Polymorphism:</mark>

The core of polymorphism is that objects of different types can be accessed through a single interface - they appear the same but behave differently.

![](https://i.imgur.com/oVkXdYQ.png)

<mark style="background: #FFB8EBA6;">Subtype:</mark>  
- declare a class as a subclass of another class  
- inheritance - subclass inherits attributes and operations of the superclass  
- operation overriding - subclass can override superclass operations (same name and  signature)  
- relevant to both statically typed & dynamically typed languages  
- design and code re-use - aids maintainability  

<mark style="background: #FFB8EBA6;">Parametric:</mark> 
- Generic data-types and generic operation parameters  

<mark style="background: #FFB8EBA6;">Function/operator/method overloading - Ad hoc:</mark>  
- Same name but different signatures (number and type of parameters)  
- Relevant to both statically typed & dynamically typed languages - just a matter of when the type is determined - compile-time / run-time  

<mark style="background: #FFB8EBA6;">Coercion - Ad hoc</mark>  
- implicit type conversion  
- e.g. convert integer to floating point; convert subclass type to superclass type

![](https://i.imgur.com/DOBxFKS.png)

There are various ways in which the Animal, Pig, Dog and Cat classes/interfaces could be implemented but the key illustration is that there is one interface (defined by Animal), three different concrete types (possibly sub classes of <mark style="background: #FFB8EBA6;">Animal</mark>) and different behaviour when the speak() method is invoked on an <mark style="background: #FFB8EBA6;">Animal</mark> object (method overriding).

## <mark style="background: #FFB8EBA6;">UML Review:</mark>


<mark style="background: #FFB8EBA6;">Model Views:</mark>
- **User View** - Use-case diagrams
- **Structural View** - Class Diagrams. How the system does it.
- **Behavioural View** - Sequence Diagrams. State chart diagrams.
- **Environment View** Deployment Diagrams.
- **Implementation View** - Component Diagrams

<mark style="background: #FFB8EBA6;">UML Definitions:</mark>

<mark style="background: #FFB8EBA6;">Class:</mark>
- A class is a description of a set of objects that share attribute, operations (behaviours), relationship with other objects.  
- The purpose of a class is to declare a collection of operations, and attributes that fully describe the structure and behaviour for all objects of that class.  

<mark style="background: #FFB8EBA6;">Object:</mark>  
- An Object is an instance that originates from a class; it is structured and behaves according to its class.  

<mark style="background: #FFB8EBA6;">Generalisation:</mark>  
- Taxonomic(hierarchical) relationship between a more general element and a more specific element that is fully consistent with the first element and that adds additional information

<mark style="background: #FFB8EBA6;">Generalisations in Object Classes:</mark>
- Arrange real-world object classes into hierarchies
- Models the difference and similarities between classes
- When two classes are arranged into a hierarchy the more specialised class will <mark style="background: #FFB8EBA6;">inherit</mark> all the characteristics from the more generalised class (superclass).

![](https://i.imgur.com/dwd5DbP.png)

<mark style="background: #FFB8EBA6;">Generalisation has a number of benefits:</mark>
- Reduces redundancy – if there was only an Employee class with an employeeType attribute, we would need all three attributes of the subclasses above in the Employee class. So if an instance/object represents a monthly paid employee then hourlyRate and hoursWorked may be redundant (this could depend on other factors...)  
- Reuses design artefacts – e.g. superclasses and already designed subclasses  
- Reuses compile time artefacts – existing classes  
- Reduces brittleness – adding new subclasses does not affect existing classes/code  
- Eases maintainability & understanding


### <mark style="background: #FFB8EBA6;"> Review of the Object Model:</mark>

The object model is a general way of thinking about the structure of OO programs

The fundamental property of the object model is that computation takes place in and between objects

The object model is the common computational model shared by UML and Object-Oriented Programming Languages.

Individual Objects are responsible for maintaining part of a system's data and for implementing aspects of its overall functionality.

An object supports the data stored by that object and the methods, or functions, to access and update the data it contains.

Developing an <mark style="background: #FFB8EBA6;">Object Model</mark> allows us to use the real world domain to drive the initial structure of the system. This initial “mapping” of the real world domain/concepts is then also called the <mark style="background: #FFB8EBA6;">conceptual</mark> or <mark style="background: #FFB8EBA6;">domain model</mark>.

### <mark style="background: #FFB8EBA6;">Network of Objects:</mark>

The global behaviour of the system emerges from the interaction of many distinct objects. The relationships between the data stored in the individual objects must be recorded.  

These requirements are supported by allowing objects to be linked together - this is typically achieved by enabling one object to hold a reference to another.  

The object model views a running program as a  network, or graph of objects. The objects form  the nodes in the graph, and the arcs connecting the objects are known as <mark style="background: #FFB8EBA6;">links</mark>. 

The object network represents relationships between data entities - Objects can be  
created and destroyed at run-time and the  
links between them can also be changed -  
the structure, or topology, of the object  
network is therefore highly dynamic,  
changing as a program runs