### <mark style="background: #FFB8EBA6;">Associations:</mark>

Associations are <mark style="background: #FFB8EBA6;">one type of relationship</mark> that can be modelled between classes (others are Dependencies, Generalisations, Realisations).  

Associations <mark style="background: #FFB8EBA6;">describe the reason</mark> for the relationship between the classes and the rules that govern it (e.g. Multiplicities).  

Associations can be termed <mark style="background: #FFB8EBA6;">Aggregate</mark> (one class is part-of or sub-ordinate to the other).  

Associations can be termed <mark style="background: #FFB8EBA6;">Composite</mark> (one class is considered the whole and the other is considered part-of the whole, the part-of class has a lifetime that is dependent on the other).  

Associations can be <mark style="background: #FFB8EBA6;">Directed</mark> – the relationship only goes one way (uni-directional). If not, they are considered bi-directional.

<mark style="background: #FFB8EBA6;">Implementing Associations:</mark>
- We can implement a simple association using a <mark style="background: #FFB8EBA6;">class member variable</mark> that holds a reference  
- A <mark style="background: #FFB8EBA6;">reference member variable only allows one direction of navigability</mark> (from the object holding the reference to the object being referenced)  
- If we keep the navigability to one direction (if possible) then the <mark style="background: #FFB8EBA6;">implementation will be less complicated</mark> – it keeps the responsibility of maintaining the association to one class

Associations provide relationships between the classes as defined in the real-world problem domain. 

They dictate how instances of the classes (the objects) can be linked at runtime and are implemented as class attributes.  

Dependencies are another type of class relationship that can be modelled at design time (denoted by a dashed arrow). These relationships show that one class is dependent on another. 

An example of this maybe that an instance of one class acquires a link to an instance of the other at some point in its lifetime (possibly a return parameter from an operation call) and uses it to perform an operation. If that operation were to change, it could affect the class that is dependent on it. The links between these objects are not modelled/implemented as class attributes (member variables).

### <mark style="background: #FFB8EBA6;">Implementing Uni-directional Associations:</mark>

<mark style="background: #FFB8EBA6;">One to One – 0..1 (optional association)</mark>
 
A reference variable in an instance of a class (object) can hold a reference to another object OR It can hold the null reference

This means the “default” multiplicity for such an association is “0..1”

![](https://i.imgur.com/pof8QGD.png)

The association is implemented by a member variable in the ‘``Account``’ class holding a reference to an instance of the ‘``DebitCard``’ class.

Remember the reason that 0..1 is the default multiplicity here is that if the “``theCard``” reference can be null (in the code) it means there is no ``DebitCard`` object associated with the Account object. The association 0..1 dictates that this is correct as it means none or one ``DebitCard`` object may be associated with an Account object. We will see later that the situation can be different for one-to-one associations (i.e. not optional).

![](https://i.imgur.com/SVp8UXL.png)

Here the ``Account`` class has the responsibility to  
maintain the association because it has the  
reference member variable.  

In this example, there is a simple accessor (getter) and mutator (setter) but also a business method ``removeCard()``

We can also make this association <mark style="background: #FFB8EBA6;">immutable</mark>:
![](https://i.imgur.com/7KaVU5t.png)

There are a number of ways this could be implemented. The getter and setter are commonly implemented but methods like ``removeCard``, ``addCard`` or ``cancelCard`` might be modelled as part of the design and be more appropriate. These kind of methods might be identified through the business use cases.  

For the immutable example, we can see that the ``setCard()`` will only work if a card is  
not currently assigned. In this case, in order to change the card on an account, the  
``removeCard()`` must be invoked first – in this way we can encapsulate any business  
logic that needs to be executed when a card is removed from an account.

<mark style="background: #FFB8EBA6;">One to One – 1..1 (mandatory association):</mark>

![](https://i.imgur.com/OQqm5cr.png)

Consider the above model – in this case the <mark style="background: #FFB8EBA6;">Guarantor is mandatory</mark>  

A <mark style="background: #FFB8EBA6;">null reference</mark> to a Guarantor in the Account  
class <mark style="background: #FFB8EBA6;">cannot be allowed to exist</mark>.

This needs to be handled in the code implementing the association.

![](https://i.imgur.com/n0sl4Ay.png)

For a one to one mandatory association the 1..1 is denoted just by the single digit 1 meaning there must be 1 and only one Guarantor object linked to the Account object.  

This is implemented in the code of the constructor – a non null reference must be given to the constructor or an exception will be thrown.

<mark style="background: #FFB8EBA6;">One to Many – 1..M Associations:</mark>

![](https://i.imgur.com/hVKfMb9.png)

Consider the above model – in this case a Manager object can be linked with many Account objects  

A Manager object will need to hold multiple references to Account objects

This needs to be handled in the code implementing the association. We will need some sort of Collection object.
- In Java we can use an ``ArrayList`` object  
- This object gives us all the facilities to handle a collection of references  
- The Manager object then just concentrates on the business operations

![](https://i.imgur.com/QWMOINI.png)

<mark style="background: #FFB8EBA6;">Note 1:</mark> “0..\*” can be denoted as just “\*”. This would be an optional association – the Manager object may not have any Account objects linked to it (but can have many). “1..*” means the Manager object must have one Account object linked to it. Also remember, something like “0..5” is also possible if the business requirements dictate it.  

<mark style="background: #FFB8EBA6;">Note 2:</mark> This is a unidirectional association – the system requirements here would lead us to model that it needs to identify all the accounts for a manager but it doesn’t need to be able to identify the manager for a specific account. I.e. the Manager object knows the accounts its linked to but Account objects do not know what manager object they are linked to.  

<mark style="background: #FFB8EBA6;">Note 3:</mark> The code above is simplified for illustrative purposes. E.g. we would need to make sure that we don’t add duplicate references to the ``ArrayList``.

### <mark style="background: #FFB8EBA6;">Implementing Bi-directional Associations:</mark>

<mark style="background: #FFB8EBA6;">Bidirectional Links:</mark>  

Some associations need to be navigated in both directions 
- remember references are unidirectional – this means it will take two references to implement a link in each direction  
- the association can be implemented by including a suitable reference field in each of the associated classes

![](https://i.imgur.com/6UOG61u.png)

<mark style="background: #FFB8EBA6;">Note</mark> - above is a conceptual diagram showing the domain model. Conceptual diagrams define the association and not how that association might be implemented.

<mark style="background: #FFB8EBA6;">One-to-one Association traversed in both directions:</mark>

![](https://i.imgur.com/6XNaGW4.png)

<mark style="background: #FFB8EBA6;">Note</mark> – the diagram above would be considered a specification diagram as it contains additional information on how the model might be implemented. It shows two role-names which would correspond to the class attributes (member references) that might be implemented. It also show these classes as business classes.

<mark style="background: #FFB8EBA6;">One-to-Many Association traversed in both directions:</mark>

![](https://i.imgur.com/eAfVMvx.png)

![](https://i.imgur.com/1WAB9JO.png)

![](https://i.imgur.com/3e5zES1.png)

The concept is the same as one-to-one but in this case we can see that the Member  class will need to hold a collection of references to Book objects but the Book object only needs to hold one reference to a Member object

### <mark style="background: #FFB8EBA6;">Referential Integrity:</mark>

![](https://i.imgur.com/dddekWa.png)

With <mark style="background: #FFB8EBA6;">bi-directional associations</mark>, we need to consider how an operation of one class may effect the other associated class.  

E.g. If we had a member object with a set of <mark style="background: #FFB8EBA6;">book</mark> objects – each book object will have a reference to the <mark style="background: #FFB8EBA6;">member</mark> object. If we removed a book from the <mark style="background: #FFB8EBA6;">set of books</mark> in the <mark style="background: #FFB8EBA6;">member</mark> object’s <mark style="background: #FFB8EBA6;">set</mark>, then we should also set the reference to the member object in the <mark style="background: #FFB8EBA6;">book</mark> object to null to maintain <mark style="background: #FFB8EBA6;">referential integrity</mark>.

Essentially we don’t want objects with references to other objects that don’t have a reference back to them (for bi-directional relationships).

<mark style="background: #FFB8EBA6;">Referential Integrity Example (Member Class):</mark>

When borrowing a  book, we will create the bi-directional link between the Member object and the Book object  

As well as adding the book to its Set, it sets the member attribute of the book object to itself.
![](https://i.imgur.com/yulkpnE.png)

When returning a book, we will remove the link between the Member object and the Book object (in both directions)

As well as removing the book from its Set, it removes the member reference of the book object.

![](https://i.imgur.com/AgSkMAs.png)

Note the checks in the code to stop an infinite loop from occurring.  

As each object is calling back onto the other object when setting up and removing the links, we need these checks to stop an infinite loop happening. E.g. in the ``borrowBook()`` method in the Member class, there is a check to see if the book already exists in the set, if it does then it just returns.

<mark style="background: #FFB8EBA6;">Referential Integrity Example (Book Class):</mark>

As well as setting the member reference, it adds the book to the member object’s Set of books

![](https://i.imgur.com/Tu7Iqqh.png)

As well as removing the member reference it removes the book reference from the member object’s list

![](https://i.imgur.com/WzZcytJ.png)

Note again, the checks in the code to stop an infinite loop from occurring. In the ``setMember()`` operation, the member variable must be null before it will continue.

### <mark style="background: #FFB8EBA6;">Sequence Diagrams Revisited:</mark>

<mark style="background: #FFB8EBA6;">Object Links:</mark>
Consider an instance of the above class - it will contain two references to two Circle objects. This means that at runtime it will be linked to those objects.

![](https://i.imgur.com/JY5TeYm.png)

Vice versa, the two instances of this class (circleA and circleB) are linked to the client object

![](https://i.imgur.com/dekQZBg.png)

The actual <mark style="background: #FFB8EBA6;">link</mark> is provided by the references (``circleA`` and ``circleB``) within the client object – interestingly, this means that only the client object “knows” about the link. In this sense, the link is uni-directional.

Here we see the (java) code for an interaction between two objects. We can see that the ``SomeClient`` object invokes the ``setRadius()`` method on each of the Circle objects.

### <mark style="background: #FFB8EBA6;">Object Links:</mark>

<mark style="background: #FFB8EBA6;">Note</mark> when we talk about links we are referring to connections between objects <mark style="background: #FFB8EBA6;">at runtime</mark>. We have previously discussed modelling those <mark style="background: #FFB8EBA6;">at design time</mark> through associations.

![](https://i.imgur.com/hnuqeDk.png)

### <mark style="background: #FFB8EBA6;">Sequence Diagram:</mark>

Depicting how the code executes.

![](https://i.imgur.com/evsNZXV.png)

The client object first sends a synchronous message (``setRadius``) to ``circleA`` and then another to ``circleB``.

```Java
public class SomeClient {  
	SomeClient (Circle circleA,Circle circleB)  
	{  
		circleA.setRadius(10);  
		circleB.setRadius(12);  
	}  
}
```

### <mark style="background: #FFB8EBA6;">Collaborations:</mark>

![](https://i.imgur.com/HtleBkZ.png)

Model a set of classes that are capable of interacting for a set of purposes.  
- Collaboration / Communication Diagrams  
- <mark style="background: #FFB8EBA6;">Sequence Diagrams</mark>

A Collaboration is a UML artefact that is used to model how a set of classes can interact in order to realise a use case. Sequence diagrams play an important role as part of this.

### <mark style="background: #FFB8EBA6;">Types of Messages:</mark>

<mark style="background: #FFB8EBA6;">Synchronous:</mark>

![](https://i.imgur.com/uiYiWJs.png)

A message with a solid arrowhead at the end. If the message is a return message it appears as a dashed line rather than solid.

<mark style="background: #FFB8EBA6;">Asynchronous:</mark>

![](https://i.imgur.com/TGtBCoa.png)

A message with a line arrowhead at the end. If the message is a return message it appears as a dashed line rather than solid.

<mark style="background: #FFB8EBA6;">Lost:</mark>

![](https://i.imgur.com/zZMAWRu.png)

A lost message is one that gets sent to an object that is not modelled in the diagram. The destination for this message is a black dot.

<mark style="background: #FFB8EBA6;">Found:</mark>

![](https://i.imgur.com/tF1hr3y.png)

A found message is one that arrives from an unknown sender, or from an object that is not modelled in the diagram. The unknown part is modelled as a black dot.

<mark style="background: #FFB8EBA6;">Self-message:</mark>

A self message is usually a recursive call, or a call to another method belonging to the same object.

### <mark style="background: #FFB8EBA6;">Sequence Diagrams - Types of Frames:</mark>

![](https://i.imgur.com/2DgClPN.png)

<mark style="background: #FFB8EBA6;">alt</mark> models if / else / switch alternatives

<mark style="background: #FFB8EBA6;">opt</mark> models if conditions

A frame can be used to show how messages are sent between objects and are closely related to control flow / conditional branching in the code. <mark style="background: #FFB8EBA6;">loop</mark>, <mark style="background: #FFB8EBA6;">alt</mark> and <mark style="background: #FFB8EBA6;">opt</mark> are widely used.  

The above example shows the use of all three. We can see the use of <mark style="background: #FFB8EBA6;">alt</mark> dictates that the dispatch message is sent to different objects depending on the value of a variable.

### <mark style="background: #FFB8EBA6;">Dependencies & Associations:</mark>

<mark style="background: #FFB8EBA6;">Paths of Communication:</mark>

An association or dependency between two classes can be thought of as a <mark style="background: #FFB8EBA6;">path of communication</mark> between instances (objects) of those classes.

![](https://i.imgur.com/6mI0Ry7.png)

In the diagram above, objects of class A may talk to (i.e. send messages to) objects of class B and objects of class B may talk to objects of class A.  

Likewise, objects of classes B and C may also communicate. As there is no direct line of communication between A and C, objects of these classes <mark style="background: #FFB8EBA6;">may not communicate directly</mark>. If they do communicate, then there is an inconsistency in the model.

<mark style="background: #FFB8EBA6;">Note:</mark> Associations are implemented as member reference variables. Dependencies can also be implemented as reference variables (just not member variables). So in both cases, they set up the possibility for links to exist between objects and so the ability for those objects to communicate (send messages) with other.

### <mark style="background: #FFB8EBA6;">Principle of Least Knowledge:</mark>

<mark style="background: #FFB8EBA6;">Law of Demeter:</mark>

In response to a message M, an object O should send messages only to the following objects:  
1. O itself  
2. Objects which are sent as arguments to the message M  
3. Objects which O creates as part of its reaction to M  
4. Objects which are directly accessible from O, that is, using values of attributes of O.

In principle:  
- Each unit should have only limited knowledge about other units: only units "closely" related to the current unit.  
- Each unit should only talk to its friends; don't talk to strangers.  
- Only talk to your immediate friends.

The Principle of Least Knowledge is also known as the Law of Demeter. Essentially we want to decouple objects from each other as much as possible. This supports the goal of developing robust software. The less objects need to know about other objects the better, if things change or problems occur, the effects are then localised and should have much less of an knock-on effect on the rest of the system.

### <mark style="background: #FFB8EBA6;">Law of Demeter 1:</mark>

![](https://i.imgur.com/gaMQgJi.png)

![](https://i.imgur.com/vtU0xPQ.png)

In response to the message ``doSomething()``, object a sends a message to itself (invokes one of its own methods)

![](https://i.imgur.com/IO0o95i.png)

On the left we can see the structural (class diagram) and behavioural (sequence diagram) modelling that illustrates the first Law of Demeter. On the right we can see the implementation of it in java.

### <mark style="background: #FFB8EBA6;">Law of Demeter 2:</mark>

In response to a message M, an object O should send messages to objects which are sent as arguments to the message M

![](https://i.imgur.com/fHycGr9.png)

![](https://i.imgur.com/A10647D.png)

In response to the message ``doSomething()``, object c sends a message to object b (which was passed to it by the message).

![](https://i.imgur.com/LcdIcNb.png)

Note the dependency (dashed) arrow, stereotyped by ``<<parameter>>``. Recall that a dependency means the objects may be linked at runtime but an explicit association is not modelled at design time.

### <mark style="background: #FFB8EBA6;">Law of Demeter 3:</mark>

In response to a message M, an object O should send messages to objects which O creates as part of its reaction to M.

![](https://i.imgur.com/3zw7mGu.png)

![](https://i.imgur.com/OwSN80j.png)

In response to the message ``doSomething()``, object d sends a message to object b which is a locally scoped reference (instantiated by d) to an object of type B.

![](https://i.imgur.com/MJp1IOn.png)

Note the dependency (dashed) arrow, stereotyped by ``<<local>>``. In this case, the model tells us that an instance of D will hold a locally scoped reference to an object of type B. It is not an association which would be implemented as the B object being a member reference variable (attribute) of class D. We can see in the code that the D object gets a reference to the B object by creating it.

### <mark style="background: #FFB8EBA6;">Law of Demeter 4:</mark>

In response to a message M, an object O should send messages to objects which are directly accessible from O, that is, using values of attributes of O.

![](https://i.imgur.com/NBTktrM.png)


Note, an association (solid) arrow is modelled. b is a member variable of E which implements the association.
![](https://i.imgur.com/73sQWrR.png)

In response to the message ``doSomething()``, object e sends a message to object b which is a which is as attribute (member variable) of e.

![](https://i.imgur.com/5jTGuzv.png)

![](https://i.imgur.com/Wo9fNSF.png)

Note that in this scenario, there is an association between classes E and B (solid arrow). The implementation shows that b will be a member variable (attribute) of E.  

Also note that in the model (class diagram) we do not see b (E’s member attribute) in the diagram. This is normally the case as the association already defines it.

### <mark style="background: #FFB8EBA6;">Illustration of the principle of Least Knowledge:</mark>

Consider the following classes:
![](https://i.imgur.com/4FQ4X2L.png)

An object of class Person may talk to (i.e. send messages to) an object of class Oracle  

An object of class Oracle may talk to an object of class Knowledge.  

As there is no direct line of communication between Person and Knowledge, an object of class Person may not communicate directly with an object of class Knowledge.  

If they need to communicate directly, then there is a problem with the diagram.

Next we will illustrate the principle using a somewhat contrived example to ensure an understanding of it.

![](https://i.imgur.com/pPF8Vv6.png)

The problem here is that the ``Person`` object is <mark style="background: #FFB8EBA6;">“reaching inside”</mark> the ``Oracle`` object to get access to the ``Knowledge`` object. The Person object then ‘talks’ to the ``Knowledge`` object. This would work fine but it is inconsistent with the model above. This breaks the principle of least knowledge as there is no need for Person objects to know anything about, or even the existence of, ``Knowledge`` objects.  

It should be the responsibility of the Oracle class (and <mark style="background: #FFB8EBA6;">only</mark> the Oracle class in this case) to communicate with the Knowledge class. We should change this implementation to decouple the Person class from the Knowledge class.

### <mark style="background: #FFB8EBA6;">Current Implementation:</mark>

![](https://i.imgur.com/oeoTSki.png)

![](https://i.imgur.com/cTnS7iA.png)

<mark style="background: #FFB8EBA6;">Sequence Diagram of the existing implementation:</mark>

![](https://i.imgur.com/V0kDmyF.png)

Direct communication between a Person object and a Knowledge object

Above is a sequence diagram of the current implementation. The diagram clearly shows the inconsistency between the structural model (class diagram) and the behavioural model (as seen by the message from the Person object to the Knowledge object).

<mark style="background: #FFB8EBA6;">What to do?</mark>

![](https://i.imgur.com/GolHZus.png)

Person object now calls the new “wrapper” method, i.e. it no longer reaches inside the Oracle object to get the Knowledge object.

A new “wrapper” method (``answerToLife``) is added to the Oracle class. It now communicates with the Knowledge object.

Note here, that in the ``Oracle`` class, the “getter” method has been removed.  

According to the current model there is no need for it. Removing it stops other objects from getting direct access to the ``Knowledge`` object (which, remember, is a private attribute of the ``Oracle`` class), i.e. the ``Oracle`` class has sole responsibility for communication with the ``Knowledge`` object.

<mark style="background: #FFB8EBA6;">Better Implementation:</mark>

![](https://i.imgur.com/PnUomsa.png)

![](https://i.imgur.com/DEWAD5N.png)

<mark style="background: #FFB8EBA6;">Sequence Diagram of the new implementation:</mark>

![](https://i.imgur.com/h4Iya85.png)

This diagram is now consistent with the class diagram. The communication between the objects now adheres to the <mark style="background: #FFB8EBA6;">Law of Demeter</mark>.

Above is the sequence diagram of the new implementation. Any changes made to the Knowledge class will have no effect on the Person object.

### <mark style="background: #FFB8EBA6;">Letting Company Use Case Example:</mark>

A letting company operates a service whereby they provide apartment block properties for rent. Each apartment would have a specific rent associated with it and may or may not be occupied.  

We want to model a system which can realise the following use case...

![](https://i.imgur.com/wbeWzAy.png)

Example of the Principle of Least Knowledge where the initial solution would execute correctly from a business perspective and would pass tests etc. but where there would be inconsistencies between the structural and behavioural models that could lead to brittleness in the software.

<mark style="background: #FFB8EBA6;">Letting Company - Class diagram:</mark>

A letting company operates a service whereby they provide apartment block properties for rent. Each apartment would have a specific rent associated with it and may or may not be occupied.

![](https://i.imgur.com/PWiawFo.png)

A simplified example for illustrative purposes. Above is the structural model based on  
the use case brief description.

<mark style="background: #FFB8EBA6;">Letting Company - Sequence Diagram:</mark>

Junior developer’s attempt

![](https://i.imgur.com/4fxJZDt.png)

Above is a design (behavioural model) that would realise the use case based on the structural model. This would work fine from a business perspective and would pass tests etc. 

However, there is an inconsistency – the sequence diagram clearly shows communication between the ``lettingCompany`` object and the ap object which is inconsistent with the structural model. In this solution, the ``LettingCompany`` class needs to know everything about the Apartment class and makes them tightly coupled. 

There is no need for this, the structural model shows that we should keep these decoupled and reduce potential brittleness.

<mark style="background: #FFB8EBA6;">Letting Company - Sequence Diagram:</mark>

2nd attempt:
![](https://i.imgur.com/BlJiUPl.png)

We create a new method to fix the issue

Note the use of the opt and loop frames

Note no messages sent between the ``lettingCompany`` and ``ap`` objects

The first attempt did not comply with the association model

We introduce a new method to fix this issue. This gives the responsibility of calculating the rent for a property to the Property class rather than the ``LettingCompany`` object needing to know about Apartments, occupation and rent – these are business attributes that it does not need to know about.  

The 2nd attempt decouples the LettingCompany and Apartment classes which is the way it should be according to the model. Now, any future changes or issues with the Apartment class will not affect the LettingCompany class. By following this principle in our design and coding, we end up with a much more robust system which leverages the OO design and development paradigm well.

### <mark style="background: #FFB8EBA6;">Company Department Use Case Example:</mark>

A (company) department has many employees, each of which may have a number of jobs assigned to them. Each job would require a set number of hours to be associated with it.  

We want to model a system which can realise the following use case...

![](https://i.imgur.com/Jr4biCO.png)

Another example of the Principle of Least Knowledge where the initial solution would execute correctly from a business perspective and would pass tests etc. but where there would be inconsistencies between the structural and behavioural models that could lead to brittleness in the software.

<mark style="background: #FFB8EBA6;">Department - Sequence Diagram:</mark>

Junior developer’s attempt:
![](https://i.imgur.com/R9LpPcf.png)

Similar to the previous example – the department object is communicating with the job object...

<mark style="background: #FFB8EBA6;">Department - Sequence Diagram:</mark>

![](https://i.imgur.com/pBgp9N5.png)

Note no messages sent between department and job

New operation introduced – ``getTotalHours()`` – decouples Department and Job classes.