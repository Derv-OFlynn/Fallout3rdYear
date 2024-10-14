### <mark style="background: #FFB8EBA6;">Interface Class:</mark>

Note here that we are discussing the concept of an interface (not to be confused with user interfaces) - interfaces can be implemented in a number ways and may depend on the programming language being used.

<mark style="background: #FFB8EBA6;">Definition:</mark> An <mark style="background: #FFB8EBA6;">Interface</mark> is a selection of externally visible public operations

<mark style="background: #FFB8EBA6;">Two modelling requirements arise:</mark>
1. A class may be required to present more than one external interface to other collaborating classes  
2. Several classes may be required to present the same interface.

An <mark style="background: #FFB8EBA6;">Interface Class</mark> provides for this design. It specifies the externally-visible (public) operations of another class.

Again, note that we are defining what a interface means in terms of classes and objects. We can leverage interfaces in our software design/engineering to create robust solutions to modelling requirements.

It provides a mechanism for a class to communicate with a <mark style="background: #FFB8EBA6;">restricted view</mark> of another class  

An interface class has:
- no internal structure 
- no attributes  
- no implementation of its own  
- It compares to an abstract class (no instances). 

An interface class typically <mark style="background: #FFB8EBA6;">specifies only a limited part of the behaviour</mark> of another class.

An interface (class) allows us to specify a particular operation or set of operations that would be required (invoked) by other objects in certain contexts. Any object that provides an implementation of those operations is said to realise the interface. In Java, we can say that a class <mark style="background: #FFB8EBA6;">implements</mark> an interface.  

One typical use of interfaces is to specify a subset of operations of a class so that other objects can only utilise those operations when working with an instance of that class – see next slide.

![](https://i.imgur.com/tsgGiET.png)

<mark style="background: #FFB8EBA6;">Modelling requirement:</mark> A class may be required to present more than one external interface to other collaborating classes e.g. a restricted view.

<mark style="background: #FFB8EBA6;">Dependency</mark> relationship – a customer object will “see” a Viewable object and so will only be able to invoke the ``display()``  operation.

<mark style="background: #FFB8EBA6;">Realisation</mark> relationships between two classes - one class offers the interface of the other.  

The <mark style="background: #FFB8EBA6;">Advert</mark> class provides the implementation of the operations specified in both interfaces.

![](https://i.imgur.com/ljZfQfw.png)

In this case, there are two interfaces defined. The Advert class realises (implements) both interfaces. We can see the Viewable interface only allows a Customer object to utilise the ``display()`` method of an Advert object (the Customer objects only “sees” a Viewable object).

<mark style="background: #FFB8EBA6;">Modelling requirement:</mark>  Several classes may be required to present the same interface e.g. an API specification

<mark style="background: #FFB8EBA6;">Java Database Connectivity:</mark>

![](https://i.imgur.com/YyB6fBs.png)

Most major RDBMS providers supply JDBC code libraries to allow java developers to  
easily connect to their database.

In this case, interfaces are defined for a set of classes that need to be implemented/supplied by the vendor of an RDBMS.  

Different RDBMS’s will have different implementations of the set of interfaces. In this case, Java code that needs to communicate with a particular RDBMS will be “coded to the interface” - the code just “sees” an interface it can use and not an instance of the implementing class) and so does not even know which implementation of the interfaces it is using (Oracle, MySQL, Postgres etc.). This provides a very loose coupling between the application code and the database.  

An example of a benefit is that we could replace the RDBMS with a completely different one and not have to alter our system in anyway except perhaps some configuration.

![](https://i.imgur.com/Db2gEtk.png)

<mark style="background: #FFB8EBA6;">JDBC:</mark>
- Each RDBMS has its own implementation of the JDBC Java Interfaces  
- E.g. Each JDBC library must have a class that implements the ``Statement`` interface  
- ``Statement`` - the object used for executing a static SQL statement and returning the results it produces.

JDBC code libraries referred to as JDBC Drivers.  

Essentially consist of a single jar file containing all the necessary java classes. E.g. mysql-connector-java-x.x.xx.jar.  

Once the jar file is included in the classpath, the specific JDBC classes can be used by your own code.

<mark style="background: #FFB8EBA6;">e.g JDBC Connection Interface:</mark>

![](https://i.imgur.com/t2t7XrB.png)

Specific JDBC libraries (Oracle, MySQL, PostgreSQL, etc.) each have their own implementation of this interface (among others...) i.e. we have many different implementing objects that provide the same interface.

<mark style="background: #FFB8EBA6;">Sample Java code to retrieve data from an RDBMS:</mark>

![](https://i.imgur.com/vrd0a8U.png)

The <mark style="background: #FFB8EBA6;">url</mark> giving the location of the database (would not normally hard-code this here).

The <mark style="background: #FFB8EBA6;">SQL</mark> query to execute against the database

The <mark style="background: #FFB8EBA6;">ResultSet</mark> object contains the data returned from the database

The ``DriverManager`` class is used to obtain an appropriate ``Connection`` object.  When JDBC implementations (jar files) are included in a project – they register  themselves with the ``DriverManager`` class. When our code asks the ``DriverManager`` to get a Connection object , it uses the URL we give it to find the appropriate Driver for that URL (i.e. type of database). That Driver object is an implementation of the JDBC Driver interface – in this case it is MySQL implementation. Oracle, Postgres etc. would have their own Driver interface implementations. So we have many different classes providing the same interface(s) to our code.  

You might see legacy java code like this:  
``Class.forName( "com.mysql.jdbc.Driver" ); `` 

We can write this in our code above the ``DriverManager.getConnection()`` call, which explicitly tells the ``DriverManager`` what Driver implementation to use.  

This works fine but is no longer necessary since JDBC 4.


### <mark style="background: #FFB8EBA6;">Boundary & Controller Classes:</mark>

Boundary and Controller classes are two other common types of objects found in software architecture.

<mark style="background: #FFB8EBA6;">Three-Tier Architecture:</mark>

The aim is to separate the classes that have the responsibility for the interface with the user, or with other systems, (boundary classes) from the business classes (entity classes) and the classes that handle the application logic (control classes)

![](https://i.imgur.com/tYt1LaI.png)


<mark style="background: #FFB8EBA6;">Reasons for separating classes:</mark>
- <mark style="background: #FFB8EBA6;">Logical:</mark> Enables presentation designs that are independent of the physical hardware and the software technology 
- <mark style="background: #FFB8EBA6;">Interface Independence:</mark> Object attributes may be input/displayed in several ways and this responsibility is assigned to the presentation classes  
- <mark style="background: #FFB8EBA6;">Reuse:</mark> Of classes from all 3 layers

Note that there may be more than three tiers, and that the logical layers can map to physical platforms in a number of ways.

<mark style="background: #FFB8EBA6;">Presentation Layer:</mark>
- Handles the interface with users and other connected systems 
- Formats and presents data at the interface  
- Provides a mechanism for data entry by the user, but the events are handled by control classes
- Presentation can be many forms:  
	- for display as text or charts  
	- printing on a printer  
	- speech synthesis  
	- formatting in JSON/XML for transferral  
	
- Does not contain the business logic—rules like ‘A Campaign must have one and only one Campaign Manager’.  
- Does not handle validation, beyond perhaps simple checks on formatting, value ranges and lookup list.

The combination of boundary and controller classes often provide the architecture to support external access to the software system.

![](https://i.imgur.com/N0UMVve.png)

This is a simple illustration of an external request. The UI boundary class provides the user interface through which the user can make a request, the request is then handled by the controller where it coordinates the invocation of the business logic.