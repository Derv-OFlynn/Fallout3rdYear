### <mark style="background: #FFB8EBA6;">Design Patterns:</mark>

Have you ever encountered a design problem and silently thought: <mark style="background: #FFB8EBA6;">I wonder if anyone has developed a solution to this?</mark>

What if there was a standard way of describing a problem (so you could look it up), and an organized method for representing the solution to the problem?

<mark style="background: #FFB8EBA6;">Design patterns</mark> are a codified method for describing problems and their solution that allows the software engineering community to capture design knowledge in a way that enables it to be reused.  

Each pattern describes a problem that occurs over and over again in our environment and then describes the core of the solution to that problem. “a three-part rule which expresses a relation between a certain <mark style="background: #FFB8EBA6;">context</mark>, a <mark style="background: #FFB8EBA6;">problem</mark>, and a <mark style="background: #FFB8EBA6;">solution</mark>.”

### <mark style="background: #FFB8EBA6;">Basic Concepts:</mark>

Context allows the reader to understand the environment in which the problem resides and what solution might be appropriate within that environment.  

A set of requirements, including limitations and constraints, acts as a system of forces that influences how the problem can be interpreted within its context and how the solution can be effectively applied.

### <mark style="background: #FFB8EBA6;">Categories of Patterns:</mark>

<mark style="background: #FFB8EBA6;">Creational patterns</mark> focus on the creation, composition, and representation of objects, e.g.  
- <mark style="background: #FFB8EBA6;">Abstract factory pattern:</mark> centralize decision of what factory to instantiate  
- <mark style="background: #FFB8EBA6;">Factory method pattern:</mark> centralize creation of an object of a specific type choosing one of several implementations  

<mark style="background: #FFB8EBA6;">Structural patterns</mark> focus on problems and solutions associated with how classes and objects are organized and integrated to build a larger structure, e.g.,  
- <mark style="background: #FFB8EBA6;">Adapter pattern:</mark> 'adapts' one interface for a class into one that a client expects  
- <mark style="background: #FFB8EBA6;">Aggregate pattern:</mark> a version of the Composite pattern with methods for aggregation of children  

<mark style="background: #FFB8EBA6;">Behavioural patterns</mark> address problems associated with the assignment of responsibility between objects and the manner in which communication is effected between objects, e.g.,  
- <mark style="background: #FFB8EBA6;">Command pattern:</mark> Command objects encapsulate an action and its parameters  
- <mark style="background: #FFB8EBA6;">Chain of responsibility pattern:</mark> Command objects are handled or passed on to other objects by logic-containing processing objects

### <mark style="background: #FFB8EBA6;">Other Collections of Patterns:</mark>

<mark style="background: #FFB8EBA6;">Architectural patterns</mark> describe broad-based design problems that are solved using a structural approach.  

<mark style="background: #FFB8EBA6;">Data patterns</mark> describe recurring data-oriented problems and the data modelling solutions that can be used to solve them.  

<mark style="background: #FFB8EBA6;">Component patterns</mark> (also referred to as design patterns) address problems associated with the development of subsystems and components, the manner in which they communicate with one another, and their placement within a larger architecture  

<mark style="background: #FFB8EBA6;">Web App patterns</mark> address a problem set that is encountered when building WebApps and often incorporates many of the other patterns categories just mentioned.

### <mark style="background: #FFB8EBA6;">Frameworks:</mark>

Patterns themselves may not be sufficient to develop a complete design.  
- In some cases it may be necessary to provide an implementation-specific skeletal infrastructure, called a <mark style="background: #FFB8EBA6;">framework</mark>, for design work.  
- That is, you can select a “reusable mini-architecture that provides the generic structure and behavior for a family of software abstractions, along with a context ... which specifies their collaboration and use within a given domain.”  

A framework <mark style="background: #FFB8EBA6;">is not an architectural pattern</mark>, but rather a skeleton with a collection of “plug points” (hooks and slots) that enable it to be adapted to a specific problem domain.  

The plug points enable you to integrate problem specific classes or functionality within the skeleton.

### <mark style="background: #FFB8EBA6;">Describing a Pattern:</mark>

<mark style="background: #FFB8EBA6;">Pattern name:</mark> describes the essence of the pattern in a short but expressive name  

<mark style="background: #FFB8EBA6;">Intent:</mark> describes the pattern and what it does  

<mark style="background: #FFB8EBA6;">Problem:</mark> describes the problem that the pattern addresses  

<mark style="background: #FFB8EBA6;">Motivation:</mark> provides an example of the problem  

<mark style="background: #FFB8EBA6;">Context:</mark> describes the environment in which the problem resides including application domain  

<mark style="background: #FFB8EBA6;">Forces:</mark> lists the system of forces that affect the manner in which the problem must be solved (including limitations / constraints)  

<mark style="background: #FFB8EBA6;">Solution:</mark> provides a detailed description of the solution proposed for the problem  

<mark style="background: #FFB8EBA6;">Collaborations:</mark> describes how other patterns contribute to the solution  

<mark style="background: #FFB8EBA6;">Consequences:</mark> describes the potential trade-offs that must be considered when the pattern is implemented and consequences of its use  

<mark style="background: #FFB8EBA6;">Implementation:</mark> identifies special issues that should be considered when implementing the pattern  

<mark style="background: #FFB8EBA6;">Known uses:</mark> provides examples of actual uses of the design pattern in real applications  

<mark style="background: #FFB8EBA6;">Related patterns:</mark> cross-references related design patterns

### <mark style="background: #FFB8EBA6;">Thinking in Patterns:</mark>

Shalloway and Trott suggest the following approach that enables a designer to think in patterns:  
1. Be sure you understand the big picture—the context in which the software to be built resides. The requirements model should communicate this to you.  
2. Examining the big picture, extract the patterns that are present at that level of abstraction.  
3. Begin your design with ‘big picture’ patterns that establish a context or skeleton for further design work.  
4. “Work inward from the context” looking for patterns at lower levels of abstraction that contribute to the design solution.  
5. Repeat steps 1 to 4 until the complete design is fleshed out.  
6. Refine the design by adapting each pattern to the specifics of the software you’re trying to build.

### <mark style="background: #FFB8EBA6;">Design Tasks</mark>

Examine the requirements model and develop a problem hierarchy.

Beginning with a broad problem, determine whether one or more architectural patterns are available for it.

Using the collaborations provided for the architectural pattern, examine subsystem or component level problems and search for appropriate patterns to address them.

Repeat until all broad problems have been addressed

Be certain to refine the design as it is derived from patterns using design quality criteria as a guide.

### <mark style="background: #FFB8EBA6;">Common Design Mistakes</mark>

Not enough time has been spent to understand the underlying problem, its context and forces, and as a consequence, you select a pattern that looks right, but is inappropriate for the solution required.  

Once the wrong pattern is selected, you refuse to see your error and force fit the pattern.  

In other cases, the problem has forces that are not considered by the pattern you’ve chosen, resulting in a poor or erroneous fit.  

Sometimes a pattern is applied too literally and the required adaptations for your problem space are not implemented.

### <mark style="background: #FFB8EBA6;">DAO Pattern:</mark>

Recall our discussion on database connectivity...

![](https://i.imgur.com/N6Zw4RG.png)

Most major RDBMS providers supply JDBC code libraries to allow java developers to easily connect to their database

![](https://i.imgur.com/Vmpufox.png)

Each RDBMS has its own implementation of the JDBC Java Interfaces  

E.g. Each JDBC library must have a class that implements the Statement interface  

<mark style="background: #FFB8EBA6;">Statement</mark> - the object used for executing a static SQL statement and returning the results it produces.

![](https://i.imgur.com/P5NDyuk.png)

The url giving the location of the database (would not normally hard-code this here).

The SQL query to execute against the database

The ``ResultSet`` object contains the data returned from the database

### <mark style="background: #FFB8EBA6;">Managing Data:</mark>

Consider a table in a database called ``customer`` with the following columns:  
```SQL
custNumber (integer)  
custName (varchar)  
contactLastName (varchar)  
contactFirstName (varchar)  
phone (varchar)  
creditLimit (double)
```

![](https://i.imgur.com/bIjAIDX.png)

### <mark style="background: #FFB8EBA6;">The Data Access Object (DAO) Pattern:</mark>

<mark style="background: #FFB8EBA6;">Intent:</mark> Isolate the application/business layer from the persistence layer using an abstract API.

![](https://i.imgur.com/Eh5ugrh.png)

Encapsulates all the activity required to connect to the database and retrieve the data. It creates a Customer object, fills it with the data and returns it to the client.

![](https://i.imgur.com/kZUiWmJ.png)

### <mark style="background: #FFB8EBA6;">Example DAO code:</mark>

![](https://i.imgur.com/sH0OppO.png)

This example illustrates the methods that our DAO class might have

Note, we still need to add database connection handling code to this.

<mark style="background: #FFB8EBA6;">Example client code using the DAO object:</mark>
![](https://i.imgur.com/sDaUDfl.png)

### <mark style="background: #FFB8EBA6;">For reference: JDBC PreparedStatement:</mark>

We have used the <mark style="background: #FFB8EBA6;">Statement</mark> class to send SQL to the DBMS.  

SQL is sent to the DBMS which has to compile it before execution.  

``PreparedStatement`` objects are given the SQL on creation of the object which is then normally sent to the DBMS at that time.  

When our code wants to execute the statement – the DBMS does not have to compile it.  

We can re-use our ``PreparedStatement`` object without requiring re-compilation by the DBMS

![](https://i.imgur.com/9SUykju.png)

![](https://i.imgur.com/SBwm9yJ.png)
