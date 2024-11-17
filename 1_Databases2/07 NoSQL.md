### <mark style="background: #69E772;">SQL Characteristics:</mark>
- Data stored in columns and tables  
- Relationships represented by data  
- Data Manipulation Language  
- Data Definition Language  
- Transactions (ACID)  
- Abstraction from physical layer

### <mark style="background: #69E772;">Data Manipulation Language (DML):</mark>

Data manipulated with Select, Insert, Update, & Delete statements  
```SQL
Select T1.Column1, T2.Column2 ...  
From Table1, Table2 ...  
Where T1.Column1 = T2.Column1 ... 
``` 

Data Aggregation  

Functions and Procedures  

Explicit transaction control

### <mark style="background: #69E772;">Data Definition Language (DDL):</mark>

Schema defined at the start  

```SQL
Create Table (Column1 Datatype1, Column2 Datatype 2, ...)
```  

Constraints to define and enforce relationships  
- Primary Key  
- Foreign Key  
- Etc.  

Triggers to respond to Insert, Update , & Delete  

Stored Modules  

Alter ...  

Drop ...  

Security and Access Control

### <mark style="background: #69E772;">NO SQL.. Why?</mark>

Web-based applications caused spikes. Especially true for public-facing e-Commerce sites  

Internet, distributed data, big data...  

Developers begin to front RDBMS with memcache or integrate other caching mechanisms within the application

### <mark style="background: #69E772;">Scaling up:</mark>

Issues with scaling up when the dataset is just too big  

RDBMS were not designed to be distributed  

Began to look at multi-node database solutions  

Known as ‘scaling out’ or ‘horizontal scaling’  

Different approaches include:   
- Master-slave  
- Sharding

### <mark style="background: #69E772;">Master/Slave</mark>

All writes are written to the master. All reads performed against the replicated slave databases  

Critical reads may be incorrect as writes may not have been propagated down  

Large data sets can pose problems as master needs to duplicate data to slaves

### <mark style="background: #69E772;">Partition or sharding:</mark>

Scales well for both reads and writes  

Not transparent, application needs to be partition-aware  

Can no longer have relationships/joins across partitions  

Loss of referential integrity across shards

### <mark style="background: #69E772;">Other ways to scale RDBMS:</mark>

No JOINs, thereby reducing query time. This involves de-normalizing data.  

In-memory databases  

NO SQL started with the aim to address the scaling problem

### <mark style="background: #69E772;">NoSQL Definition:</mark>

A Generation of Databases mostly addressing some of the points: being <mark style="background: #69E772;">non-relational</mark>, <mark style="background: #69E772;">distributed</mark>, <mark style="background: #69E772;">open-source</mark> and <mark style="background: #69E772;">horizontal scalable</mark>. 

The original intention has been <mark style="background: #69E772;">modern web-scale databases</mark>. 

The movement began early 2009 and is growing rapidly. 

<mark style="background: #69E772;">Often more characteristics apply as:</mark> 
- schema-free, 
- easy replication support, 
- simple API, 
- eventually consistent / BASE (not ACID), 
- a huge data amount, and more.

### <mark style="background: #69E772;">What is NoSQL?</mark>

Stands for <mark style="background: #69E772;">Not Only SQL</mark>  

Class of non-relational data storage systems  

Class of data management systems inherently  
- Non-relational  
- Distributed  
- Horizontally scalable  
- With optional schemas  
- Providing simple APIs  

All NoSQL relax one or more of the ACID properties. But some of them can also do ACID!

### <mark style="background: #69E772;">NoSQL distinguishing characteristics:</mark> 
- Large data volumes - “big data”  
- Scalable replication and distribution, Potentially thousands of machines, Potentially distributed around the world  
- Queries need to return answers quickly  
- Mostly query, few updates  
- Asynchronous Inserts & Updates  
- Schema-less  
- ACID transaction properties are not needed – BASE  
- CAP Theorem 
- Open source development

### <mark style="background: #69E772;">CAP THEOREM:</mark>

![](https://i.imgur.com/ixQfptR.png)

<mark style="background: #69E772;">C - Consistency:</mark>
- This is a given in a relational database
- If a RDBMS is not in a consistent state, it is not available.
- Remember what happens when two sessions are accessing the same data — only the consistent data is available to both.
- all nodes should see the same data at the same time

<mark style="background: #69E772;">A — Availability:</mark>
- A MongoDB database will always have data available because it has replicas of every piece of data and it only promises "eventual consistency"
- node failures do not prevent survivors continuing to operate

<mark style="background: #69E772;">P — Partition tolerance (tolerating network breaks):</mark>
- In a distributed situation, RDBMS will not allow a transaction to go through unless all nodes involved are in a consistent state.
- In a distributed situation, MongoDB will go ahead with transactions for available nodes and let the others catch up later.
- the system continues to operate despite arbitrary message loss, No set of failures less than total network failure is allowed to cause the system to respond incorrectly.

<mark style="background: #69E772;">It is impossible for a distributed systems to provide all of the above features</mark>

### <mark style="background: #69E772;">2 Out of 3: BASE vs ACID:</mark>

<mark style="background: #69E772;">C+A:</mark>  
- Always available and consistent  
- Single site databases  
- Cluster Databases (why?)  

<mark style="background: #69E772;">C+P:</mark>  
- Distributed Databases  
- Minority Locking  
- System is unavailable for a while..  

<mark style="background: #69E772;">A+P:</mark>  
- DNS  

### <mark style="background: #69E772;">ACID properties of transactions:</mark>

Basic (ACID) properties of a transaction are:  
1. <mark style="background: #69E772;">Atomicity</mark> ‘All or nothing’ property.  
2. <mark style="background: #69E772;">Consistency</mark> Must transform database from one consistent state to another.  
3. <mark style="background: #69E772;">Isolation</mark> Partial effects of incomplete transactions should not be visible to other transactions.  
4. <mark style="background: #69E772;">Durability</mark> Effects of a committed transaction are permanent and must not be lost because of later failure.

### <mark style="background: #69E772;">BASE Transactions:</mark>

<mark style="background: #69E772;">Acronym contrived to be the opposite of ACID</mark>  
- <mark style="background: #69E772;">B</mark>asically <mark style="background: #69E772;">A</mark>vailable,  
- <mark style="background: #69E772;">S</mark>oft state,  
- <mark style="background: #69E772;">E</mark>ventually consistent  

<mark style="background: #69E772;">Characteristics:</mark>  
- Weak consistency – stale data OK  
- Availability first  
- Best effort  
- Approximate answers OK  
- Simpler and faster

### <mark style="background: #69E772;">BASE:</mark>

When no updates occur for a long period of time, eventually all updates will propagate through the system and all the nodes will be consistent  

For a given accepted update and a given node, eventually either the update reaches the node or the node is removed from service  

Known as <mark style="background: #69E772;">BASE</mark> (Basically Available, Soft state, Eventual consistency), as opposed to ACID

### <mark style="background: #69E772;">What am I giving up using NoSQL?</mark>
- joins  
- group by  
- order by  
- ACID transactions  
- SQL as a sometimes frustrating but still powerful query language  
- easy integration with other applications that support SQL

### <mark style="background: #69E772;">Advantages of NoSQL:</mark>
- Cheap, easy to implement  
- Data are replicated and can be partitioned  
- Easy to distribute  
- Don't require a schema  
- Can scale up and down  
- Quickly process large amounts of data  
- Relax the data consistency requirement (CAP)  
- Can handle web-scale data, whereas Relational DBs cannot
- Simple APIs  
- Java Example: Document.save(myObject)  
- Good integration  
- Designed to be horizontally scalable (elastic)  
- Flexible data model  
- Majority free and/or Open Source 
- Free and Commercial production support

### <mark style="background: #69E772;">RDBMS Advantages:</mark>
- Proven  
- Available talent / Well-known  
- AD-Hoc querying  
- Scalable (limits?)  
- Free and Commercial production support

### <mark style="background: #69E772;">Disadvantages of NoSQL:</mark>

Data is generally duplicated, potential for inconsistency  

<mark style="background: #69E772;">No standard:</mark>
- schema  
- format for queries  
- language  

Difficult to impose complicated structures  

Depend on the application layer to enforce data integrity  

No guarantee of support  

Too many options, which one, or ones to pick

### <mark style="background: #69E772;">Where would I use a NoSQL database?</mark>

Do you have somewhere a large set of uncontrolled, unstructured, data that you are trying to fit into a RDBMS?  
- Log Analysis  
- Social Networking Feeds  
- Data that is not easily analysed in a RDBMS such as time-based data  
- Large data feeds that need to be massaged before entry into an RDBMS  
- Data that are is relational (like graph-like data?)

### <mark style="background: #69E772;">Hybrid approach: Polyglot Persistence</mark>

Using different DB technologies for different storage requirements

![](https://i.imgur.com/3zR6pbY.png)

![](https://i.imgur.com/jXQpu3J.png)

### <mark style="background: #69E772;">Schemaless data with Postgres:</mark>

Explore the boundaries between SQL and NoSQL databases  

Know a little bit more about postgres

<mark style="background: #69E772;">SQL:</mark>  
- Relational model  
- Normalise data as much as possible  
- Row in a table have the same schema

<mark style="background: #69E772;">NoSQL:</mark>  
- Document-oriented database  
- Data semi structured  
- No schema enforced over documents  
- Metadata attached to documents

### <mark style="background: #69E772;">First schemaless data: Hstore:</mark>

Key-Value data structure  

GiST and GIN index support for some operators  

Used in rows with many attributes that are rarely examined

```
"name"=>"michele"  
"surname"=>"capra"  
"age"=> 18  
"city"=>"Brescia"  
"state"=>"Italy"
```

[HStore Demo](https://github.com/piccoloaiutante/schemaless-postgres/hstore)

### <mark style="background: #69E772;">JSON data:</mark>

Javascript Object Notation  

Two type of field json/jsonb  

<mark style="background: #69E772;">More flexible than hstore:</mark> 
- nesting, 
- data validation

Store the exact copy of the input  

Spaces and keys (even duplicated) order are preserved  

Reparse on each processing

### <mark style="background: #69E772;">JSONB:</mark>

Json parsed on insert and stored in binary format  

Keys order and spaces are lost  

When duplicated keys, only last value is saved  

Supports indexing

[JSON Demo](https://github.com/piccoloaiutante/schemaless-postgres/tree/master/json)

[Modelling Demo](https://github.com/piccoloaiutante/schemaless-postgres/blob/master/json/model.md)

### <mark style="background: #69E772;">Solution:</mark>

Leave data that we use for join into value type field.  

All the rest should go to ``jsonb`` data.

### <mark style="background: #69E772;">GIS:</mark>

Geographic information system  

Storing, manipulate, analyze location information.  

x,y,z axis -> longitude, latitude, elevation

### <mark style="background: #69E772;">Postgis:</mark>

Spatial database extender for postgres  

Add support for geographic object  

Support for location queries in SQL

### <mark style="background: #69E772;">Desktop tool</mark>

pgAdmin supports spatial data but not rendering  

QGIS favourite cross platform client  

You can get it from here http://qgis.org/en/site/

<mark style="background: #69E772;">OpenGIS Consortium for 2D data:</mark>  
- Two data format representation:  
- Well-Known Text (WKT)  
- Well-Known Binary (WKB)

### <mark style="background: #69E772;">Data type - Point:</mark>

A point in a Cartesian plane.

![](https://i.imgur.com/DJ7HHJR.png)

### <mark style="background: #69E772;">Data type - LineString:</mark>

A polygonal chain is a connected series of line segments

![](https://i.imgur.com/KWH1x93.png)

### <mark style="background: #69E772;">Data type - Polygon:</mark>

A plane figure that is bounded by a finite chain of straight line segments closing in a loop to form a closed polygonal chain or circuit

![](https://i.imgur.com/grkkgw0.png)

![](https://i.imgur.com/011n8bI.png)

![](https://i.imgur.com/zuUQUqK.png)

### <mark style="background: #69E772;">Data type - Multipoint:</mark>

A series of points

![](https://i.imgur.com/IC9ibKJ.png)

### <mark style="background: #69E772;">Data type – Multiline string:</mark>

A series of line strings

![](https://i.imgur.com/8h8NlFF.png)

### <mark style="background: #69E772;">Data type – Multi polygon:</mark>

A collection of polygon

![](https://i.imgur.com/Zfe28Ec.png)

### <mark style="background: #69E772;">Postgis data type:</mark>

<mark style="background: #69E772;">Geography:</mark>  
- ellipsoidal spatial data type (latitutde + longitude)  
- unit measure is meter  

<mark style="background: #69E772;">Geometry:</mark>  
- euclidean coordinate system  
- planar spatial data type

### <mark style="background: #69E772;">Dataset examples 1:</mark>

New York subway stations (point)
![](https://i.imgur.com/CAD4cvC.png)

New York streets (multiline)
![](https://i.imgur.com/ltYhqb3.png)

New York neighborhood (polygon)
![](https://i.imgur.com/7Fvb1f4.png)

### <mark style="background: #69E772;">POSTGIS:</mark>

[POSTGIS documentation](https://postgis.net/docs/reference.html#idm11151)

[POSTGIS demo](https://github.com/piccoloaiutante/schemaless-postgres/postgis)

### <mark style="background: #69E772;">Ltree data:</mark>

Labels of data stored in a hierarchical tree-like structure  

Support indexing

<mark style="background: #69E772;">Label:</mark> sequence of alphanumeric characters and underscores  

<mark style="background: #69E772;">Path:</mark> sequence of zero or more labels separated by dots  
Operators to manipulate labels and paths

[Ltree demo](https://github.com/piccoloaiutante/schemaless-postgres/ltree)

### <mark style="background: #69E772;">Example:</mark>

![](https://i.imgur.com/qaogNLk.png)

### <mark style="background: #69E772;">Recap:</mark>

<mark style="background: #69E772;">Schemaless data in postgres:</mark> 
- Hstore  
- Json/jsonb  
- Geography/geometry  
- Ltree  

<mark style="background: #69E772;">Old data type:</mark> array