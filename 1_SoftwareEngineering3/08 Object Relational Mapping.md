The relational model does not equal the object-oriented model.

![](https://i.imgur.com/xqORCMB.png)

### <mark style="background: #FFB8EBA6;">ORM Introduction:</mark>

A technique for converting data between a relational database and an object-oriented programming language.  

A data persistence strategy  

Data persistence code/package  

The result of an ORM implementation is often likened to that of a ‘virtual object database’.  

ORM provides database independence  

The ability to seamlessly manipulate data stored in a relational database using an object programming language  

It provides a way to resolve the object-relational impedance mismatch.  

This object-relational impedance mismatch is considered to be the core problem.

### <mark style="background: #FFB8EBA6;">Object-relational Mismatch Issues:</mark>

How to map columns, rows, and tables to objects?  

How to deal with relationships?  

How to deal with associations?  

How to map object inheritance to relational tables?  

How to deal with the different design goals  
- The relational model is designed for data storage and retrieval. Its focus is in terms of how to best manage data.  
- The OO model is all about how to best model behaviour.  

How to make objects persistent?

![](https://i.imgur.com/EKJ5lFc.png)

### <mark style="background: #FFB8EBA6;">The Goals of ORM:</mark>

Take advantages of the things that Relational Database technologies do well  

Use the rich features of Object Technologies

![](https://i.imgur.com/vxx06VQ.png)

### <mark style="background: #FFB8EBA6;">Database Connectivity:</mark>

<mark style="background: #FFB8EBA6;">Open Database Connectivity</mark> (ODBC) - standard software API for using RDBMS.  
- ODBC spec. offers a procedural API for using SQL queries to access data.  
- Programmer can write applications without concern for the specifics of each RDBMS encountered.  

<mark style="background: #FFB8EBA6;">Java Database Connectivity</mark> (JDBC)

![](https://i.imgur.com/OMS9vfR.png)

Most major RDBMS providers supply JDBC code libraries to allow java developers to easily connect to their database.

![](https://i.imgur.com/VXwqF4Y.png)

Each RDBMS has its own implementation of the JDBC Java Interfaces  

E.g. Each JDBC library must have a class that implements the ``Statement`` interface  

``Statement`` - The object used for executing a static SQL statement and returning the results it produces

### <mark style="background: #FFB8EBA6;">JDBC Approaches:</mark>

<mark style="background: #FFB8EBA6;">Write SQL conversion methods by hand:</mark>  
- Tedious and requires lots of code  
- Extremely error-prone  
- Non-standard SQL ties the application to specific databases  
- Vulnerable to changes in the object model  
- Difficult to represent associations between objects

![](https://i.imgur.com/bYb7ZHJ.png)

### <mark style="background: #FFB8EBA6;">Other Approaches:</mark>

<mark style="background: #FFB8EBA6;">Object Oriented Database Systems:</mark>
- No complete query language implementation exists  
- RDMS standards more stable

<mark style="background: #FFB8EBA6;">NoSQL Database Systems:</mark>
- E.g. Document data stores  
- Relatively new and disparate  
- Performance variances

### <mark style="background: #FFB8EBA6;">A Common & Popular Solution:</mark>

Use an <mark style="background: #FFB8EBA6;">Object-Relational Mapping System</mark> (e.g. EclipseLink, Hibernate)  

Provides a simple API for storing & retrieving Java objects directly to and from the database  

<mark style="background: #FFB8EBA6;">Transparent:</mark> object model is unaware

![](https://i.imgur.com/GQZGpcF.png)

### <mark style="background: #FFB8EBA6;">ORM Architecture:</mark>

Middleware that manages persistence  

Provides an abstraction layer between the domain model and the database.

![](https://i.imgur.com/U6Z5J5H.png)

1) Data objects passed to DAO layer  
2) Method: SQL conversion  
3) Method: ORM using data/transfer objects

### <mark style="background: #FFB8EBA6;">Advantages of ORM:</mark>

<mark style="background: #FFB8EBA6;">Make RDBMS look like ODBMS:</mark> Data are accessed as objects, not rows and columns  

<mark style="background: #FFB8EBA6;">Simplify many common operations e.g.</mark>  ``manager.find(Company.class, "name = 'Mitsubishi'")``  

<mark style="background: #FFB8EBA6;">Improve portability:</mark> Separate DB specific SQL statements from application code  

<mark style="background: #FFB8EBA6;">Productivity:</mark>  
- Eliminates lots of repetitive code – focus on business logic  
- Database schema is generated automatically  

<mark style="background: #FFB8EBA6;">Maintainability:</mark>  
- Fewer lines of code –easier to understand  
- Easier to manage change in the object model  

<mark style="background: #FFB8EBA6;">Performance:</mark>  
- Lazy loading –associated/linked objects are fetched only when needed  
- Caching  

<mark style="background: #FFB8EBA6;">Database vendor independence:</mark>  
- The underlying database is abstracted away  
- Can be configured outside the application

### <mark style="background: #FFB8EBA6;">Mapping Objects to an RDBMS:</mark>

<mark style="background: #FFB8EBA6;">Two Approaches to Mapping:</mark>
![](https://i.imgur.com/IMbNMMn.png)

![](https://i.imgur.com/xweO7zo.png)

### <mark style="background: #FFB8EBA6;">Map Hierarchy to a Single Table:</mark>

The attributes from all the classes are extracted into a single table.  

An additional attribute is added to indicate the type of Department

![](https://i.imgur.com/6XNfU2t.png)

<mark style="background: #FFB8EBA6;">Advantages:</mark>  
- approach is simple  
- easy to add new classes.  
- only one table - no need for table joins giving efficient data retrieval.  

<mark style="background: #FFB8EBA6;">Disadvantages:</mark>  
- Not all attributes are relevant resulting in many null or empty attributes  
- The tables may not comply with normalization practices.

### <mark style="background: #FFB8EBA6;">Map Each Concrete Class to a Table:</mark>

![](https://i.imgur.com/F6EpP71.png)

A table is created for each concrete class. 

The attributes of the base class are included for each table.  

<mark style="background: #FFB8EBA6;">Advantages:</mark>  
- Good performance in terms of accessing a single object’s data.  

<mark style="background: #FFB8EBA6;">Disadvantages:</mark>  
- A class change requires a change to its corresponding table and any corresponding tables of its child classes.  
- Can result in much repeating data

### <mark style="background: #FFB8EBA6;">Map All Classes to a Table:</mark>

Every class has an associative table in the database.  

<mark style="background: #FFB8EBA6;">Advantages:</mark>
- Easy to add or modify subclasses  
- Easy to modify base class  
- The one-to-one mapping makes this approach easy to  understand

<mark style="background: #FFB8EBA6;">Disadvantages:</mark>  
- Data access in terms of a reads and writes can be slow because there are more tables involved.  
- More table joins may be required in order to perform a data related operation.  
- Ad-hoc reporting can be difficult

![](https://i.imgur.com/LXAY70N.png)

### <mark style="background: #FFB8EBA6;">Mapping Object Relationships in Tables:</mark>

<mark style="background: #FFB8EBA6;">Class Associations</mark>  
- One to One  
- One to Many  
- Many to Many  
- Uni-directional Association  
- Bi-directional Association

### <mark style="background: #FFB8EBA6;">Types of Class/Object Associations:</mark>

<mark style="background: #FFB8EBA6;">One to One:</mark> Employee to Role  

<mark style="background: #FFB8EBA6;">One to Many:</mark> Department to Employee  

<mark style="background: #FFB8EBA6;">Many to Many:</mark> Employee to Task  

<mark style="background: #FFB8EBA6;">Uni-directional Association:</mark> Employee to Role  

<mark style="background: #FFB8EBA6;">Bi-directional:</mark> Employee <-> Department

![](https://i.imgur.com/YniBfvS.png)

### <mark style="background: #FFB8EBA6;">Implementing Class/Object Associations:</mark>

Use of References and operations  

One-to-one uses a reference with getters/setters  

One to many uses a collection (``ArrayList``, ``Vector``) with ``add()``, ``remove()``, etc.

### <mark style="background: #FFB8EBA6;">Mapping Object Associations as Joins in Relational DB:</mark> 

Joins implemented using foreign keys FKs  

One to Many implemented by FK in the Many table  

Many to many implemented using a join or associative table

![](https://i.imgur.com/0AxyFPh.png)

### <mark style="background: #FFB8EBA6;">Retrieving an Object and Relationships from Database:</mark>

<mark style="background: #FFB8EBA6;">Example – Retrieving a Department from the DB:</mark>  
1. Read Department row from the database  
2. Instantiate a Department object and set the attributes – remember one of the attributes is a Collection  
3. Read all related Employees from the database  
4. Instantiate an Employee object for each and set the attributes  
5. Add a reference to each Employee object to the Collection (attribute of the Department object)

### <mark style="background: #FFB8EBA6;">Saving Objects and Relationships:</mark>

<mark style="background: #FFB8EBA6;">Example:</mark>  
- Create a SQL transaction to ensure referential integrity 
- Add update/insert statements for each object to the transaction.  
- Update/insert statement includes both the attributes and the key values.  
- Submit and commit the transaction

### <mark style="background: #FFB8EBA6;">Some ORM Tool Vendors:</mark>

Hibernate http://www.hibernate.org/  

Oracle TopLink http://www.oracle.com/technetwork/middleware/toplink/overview/index.html  

CocoBase http://www.thoughtinc.com/cber_index.html  

MyBatis www.mybatis.org  

EclipseLink http://www.eclipse.org/eclipselink/  

### <mark style="background: #FFB8EBA6;">Java Specifications</mark>  

<mark style="background: #FFB8EBA6;">Java Data Object (JDO):</mark>  
- One of the initial object mapping Java specifications  
- Flexible persistence options: RDBMS, OODBMS, files etc.  

<mark style="background: #FFB8EBA6;">Java Persistence API (JPA):</mark>  
- Targeted ORM feature set  
- Some implementations also offer NoSQL mapping  
- Hibernate 3.2 onwards supports the JPA

### <mark style="background: #FFB8EBA6;">ORM Tools Features:</mark>  

<mark style="background: #FFB8EBA6;">Basic features:</mark>  
- Be able to use inheritance, create hierarchies between entities  
- Handle any type of relations (1-1, 1-n, n-n)  
- Support for transactions  

<mark style="background: #FFB8EBA6;">Support various databases:</mark>  
- A big advantage of mapping tools is that they provide an abstraction of the underlying database engine.  
- Most of them allow switching easily between RDBMSs  

<mark style="background: #FFB8EBA6;">Be able to map a single object to data coming from multiple tables </mark>
- (joins, views).  
- Most of the tools handle a direct mapping of a class to one table.  

<mark style="background: #FFB8EBA6;">GUI to set up the mapping:</mark> Such a graphical tool presents the relational data model and lets you specify the objects to be created or at least the links between the objects and the tables.  

<mark style="background: #FFB8EBA6;">Generation of the classes:</mark>
- This can speed up the development  
- In some cases the database is mapped to hand-coded classes which may be a preference  

<mark style="background: #FFB8EBA6;">Generation of the database schema:</mark>  
- Some tools work only with a database they generated.  
- Big issue for legacy databases

Support for stored procedures in SQL  

<mark style="background: #FFB8EBA6;">Lazy loading:</mark> the loading of some of the related data as it is needed  

Cache dynamically generated queries so that they don't get rebuilt at each call.  

<mark style="background: #FFB8EBA6;">Cache some data:</mark> to avoid too many calls to the data source.  

<mark style="background: #FFB8EBA6;">Optimised queries:</mark> update only the modified columns;  

Bulk updates or deletions.  

When thousands of records to be updated, avoid loading all the objects in memory  

Use a query (DELETE FROM Customer WHERE Balance < 0).