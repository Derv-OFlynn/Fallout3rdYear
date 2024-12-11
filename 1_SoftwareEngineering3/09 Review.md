### <mark style="background: #FFB8EBA6;">Module Content:</mark>

<mark style="background: #FFB8EBA6;">Part One:</mark>
- Class Diagrams  
- Associations  
- Sequence Diagrams  
- Principle of least Knowledge  
- Interfaces / Boundary Classes  

<mark style="background: #FFB8EBA6;">Part Two:</mark>
- Design Patterns  

<mark style="background: #FFB8EBA6;">Part Three:</mark>
- OO Testing 
- ORM

### <mark style="background: #FFB8EBA6;">Class Diagrams:</mark>

<mark style="background: #FFB8EBA6;">Associations / Referential Integrity:</mark>
![](https://i.imgur.com/M3ozCFh.png)

<mark style="background: #FFB8EBA6;">Object Links:</mark>

![](https://i.imgur.com/2lMHdAt.png)

Consider an instance of the above class - it will contain two <mark style="background: #FFB8EBA6;">references</mark> to two Circle objects. This means that at runtime it will be <mark style="background: #FFB8EBA6;">linked</mark> to those objects.

![](https://i.imgur.com/gSlepCa.png)

Vice versa, the two instances of this class (``circleA`` and ``circleB``) are <mark style="background: #FFB8EBA6;">linked</mark> to the client object

The actual <mark style="background: #FFB8EBA6;">link</mark> is provided by the references (``circleA`` and ``circleB``) within the client object – interestingly, this means that only the client object “knows” about the link. In this sense, the link is uni-directional.

Note, when we talk about links we are referring to connections between objects at <mark style="background: #FFB8EBA6;">runtime</mark>. We have previously discussed modelling those at <mark style="background: #FFB8EBA6;">design time</mark> through associations.

![](https://i.imgur.com/ThgQtMo.png)

<mark style="background: #FFB8EBA6;">Unidirectional links:</mark> These links act as a communication pathways for the client object to send <mark style="background: #FFB8EBA6;">messages</mark> to the circle objects e.g. ``setRadius``

### <mark style="background: #FFB8EBA6;">Sequence Diagram:</mark>

Depicts how the code executes.

![](https://i.imgur.com/gEf3gjy.png)

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

### <mark style="background: #FFB8EBA6;">Dependencies & Associations:</mark>

An association or dependency between two classes can be thought of as a <mark style="background: #FFB8EBA6;">path of communication </mark>between instances (objects) of those classes.

![](https://i.imgur.com/udi6Wtr.png)

In the diagram above, objects of class A may talk to (i.e. send messages to) objects of class B and objects of class B may talk to objects of class A.  

Likewise, objects of classes B and C may also communicate. As there is no direct line of communication between A and C, objects of these classes <mark style="background: #FFB8EBA6;">may not communicate directly</mark>. If they do communicate, then there is an inconsistency in the mode.

### <mark style="background: #FFB8EBA6;">Principle of Least Knowledge - Law of Demeter</mark>  

<mark style="background: #FFB8EBA6;">In response to a message M, an object O should send messages only to the following objects:</mark>  
1. O itself  
2. Objects which are sent as arguments to the message M  
3. Objects which O creates as part of its reaction to M  
4. Objects which are directly accessible from O, that is, using values of attributes of O.