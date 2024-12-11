Lecturer: Pierpaolo Dondio

2 hours class, 2 hours lab per week

60% exam, 40% CA

CA:
- Based on labs
- Labs are not graded on the day
- Labs are divided into two batches of five labs each
- Graded on demoing the lab (Week 7 and Week 13)

Exam:
- Theory, Exercise, similar to past papers
- Answer 4 out of 5 questions

This is the most important module (ever)
- Jobs
- Good outlook
- Strategic to Ireland
- More jobs than DB experts

BBU -> Boring But Useful

Content nutshell:
- ER Diagram Revision/DB design (10%)
- Advanced topics: Advanced Queries, Indexes, Transactions, Triggers (20%)
- Python and Database Integration (20%)
- Working with tabular data and/or unstructured data (15%)
	- Web API/scraping via Python
	- Data Cleaning
	- Pandas
- NoSQL systems: (35%)
	- More on MongoDB
	- Graph Databases (Neo4j)
	- Hybrid databases with Postgres

Technologies:
- Postgres
- MongoDB
- Neo4j
- Python


### <mark style="background: #69E772;">Things we will learn:</mark>

<mark style="background: #69E772;">Design:</mark>
- Relational data model for db
- non-relational model for DB  
- Design a non relational model for a graph database  

<mark style="background: #69E772;">Practical:</mark> 
- PostgreSQL and PL/pgSQL.  
- MongoDB and Javascript.  
- Data manipulation for data science (Python (Pandas)).  
- Neo4j  

<mark style="background: #69E772;">Theoretical:</mark>  
- Concurrent usage, architecture, data protection, security, recovery, indexes.  
- Big Data and SQL

### <mark style="background: #69E772;">Can you?</mark> 
- Master SQL queries, functions, programs
- Optimize a relational schema?  
- Design MongoDB collections?  
- Query unstructured data?  
- Querying structured and non-structured data.  
- Implementing schema and task-based transactions, using commit and roll-back, taking concurrency issues into account.  
- Design, implement and query MongoDB collections.  

If you can’t, you will!

### <mark style="background: #69E772;">Data Definition Language:</mark>

- Create, Alter, Drop  
- Tables, sequences, views  

Rules of relational databases: All attributes of an entity should be dependent on the key, the whole key and nothing but the key.  

<mark style="background: #69E772;">Relationships:</mark>  
- 1:1  
- 0,1:many  
- many:many  
- reflexive join

![](https://i.imgur.com/49Jhp4n.png)

### <mark style="background: #69E772;">Data Manipulation Language:</mark>

- INSERT, UPDATE, DELETE  
- The SELECT language.  
- Query, subqueries, aggregation

![](https://i.imgur.com/WofrNGS.png)

### <mark style="background: #69E772;">Exam:</mark>

GraphDB and QIS/GIS are NOT in the exam. No RAID. They are only in labs

3 questions, choose 2. Worth 50% each.

Every question covers multiple topics

No syntax given.

Design questions present

Will need to write SQL and simple Mongo queries

Shared exam between 856/857/858

<mark style="background: #69E772;">Topics:</mark>
- RDBMS: Open questions like is it better to write triggers/procedure in the db or write them in the application.
- Normalisation
- Query plan and query execution:
	- How to read and plana  query
	- Sequential Scan vs index scan vs heap scan vs bitmap
	- Join better than subqueries
	- Where to put an index
- Write SQL queries: Window functions. Will def be on exam as it was not in the syllabus last year.
- MongoDB design advantages and disadvantages
	- Embedding vs referencing
	- JSON design
	- MongoDB theory: Sharding vs replication / flexibility of design / base vs. ACID