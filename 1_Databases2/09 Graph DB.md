# <mark style="background: #FF5582A6;">NOT EXAMINABLE</mark>

### <mark style="background: #69E772;">What is a graph?</mark>

<mark style="background: #69E772;">Graph:</mark> An abstract representation of a set of objects where some pairs are connected by links.

![](https://i.imgur.com/bXoCx5R.png)

### <mark style="background: #69E772;">Different Kinds of Graphs:</mark>

<mark style="background: #69E772;">Undirected Graph:</mark> 
![](https://i.imgur.com/3rMddsk.png)

<mark style="background: #69E772;">Directed Graph:</mark> 
![](https://i.imgur.com/z8iNO0z.png)

<mark style="background: #69E772;">Pseudo Graph:</mark>  
![](https://i.imgur.com/0jLBv3j.png)

<mark style="background: #69E772;">Multi Graph:</mark>  
![](https://i.imgur.com/sMiLvWA.png)

<mark style="background: #69E772;">Hyper Graph:</mark>
![](https://i.imgur.com/1ZJZQuA.png)

<mark style="background: #69E772;">Weighted Graph:</mark>  
![](https://i.imgur.com/Rwa5NPq.png)

<mark style="background: #69E772;">Labeled Graph:</mark>  
![](https://i.imgur.com/HdEnVdB.png)

<mark style="background: #69E772;">Property Graph:</mark>
![](https://i.imgur.com/vlUds1g.png)

### <mark style="background: #69E772;">What is a Graph Database?</mark>

A database with an explicit graph structure  

Each node knows its adjacent nodes  

As the number of nodes increases, the cost of a local step (or hop) remains the same  

Plus an Index for lookups

### <mark style="background: #69E772;">Node in Neo4j:</mark>

![](https://i.imgur.com/Nts3G5P.png)

### <mark style="background: #69E772;">Relationships in Neo4j:</mark>

Relationships between nodes are a key part of Neo4j.

![](https://i.imgur.com/bKOBfGV.png)

### <mark style="background: #69E772;">Properties:</mark>  

Both nodes and relationships can have properties.  

Properties are key-value pairs where the key is a string.  

Property values can be either a primitive or an array of one primitive type.  

For example String, int and int[] values are valid for properties.

![](https://i.imgur.com/UjTAfHx.png)

### <mark style="background: #69E772;">Graph Data Model:</mark>

![](https://i.imgur.com/pCVlRem.png)
![](https://i.imgur.com/X5MnN4z.png)
![](https://i.imgur.com/xESBGrY.png)

### <mark style="background: #69E772;">Relational Databases:</mark>

![](https://i.imgur.com/OS0apEW.png)

### <mark style="background: #69E772;">Graph Databases:</mark>

![](https://i.imgur.com/MZOSAG6.png)

![](https://i.imgur.com/G1DaIwd.png)

### <mark style="background: #69E772;">Neo4j Design Tips - from ER to Graph:</mark> 

<mark style="background: #69E772;">Table to Node Label:</mark> each entity table in the relational model becomes a label on nodes in the graph model.  

<mark style="background: #69E772;">Row to Node:</mark> each row in a relational entity table becomes a node in the graph.  

<mark style="background: #69E772;">Column to Node Property:</mark> columns (fields) on the relational tables become node properties in the graph.  

<mark style="background: #69E772;">Business primary keys only:</mark> remove technical primary keys, keep business primary keys.  

<mark style="background: #69E772;">Add Constraints/Indexes:</mark> add unique constraints for business primary keys, add indexes for frequent lookup attributes.

<mark style="background: #69E772;">Foreign keys to Relationships:</mark> replace foreign keys to the other table with relationships, remove them afterwards.  

<mark style="background: #69E772;">No defaults:</mark> remove data with default values, no need to store those.  

<mark style="background: #69E772;">Clean up data:</mark> duplicate data in denormalized tables might have to be pulled out into separate nodes to get a cleaner model.  

<mark style="background: #69E772;">Index Columns to Array</mark> indexed column names (like email1, email2, email3) might indicate an array property. 

<mark style="background: #69E772;">Join tables to Relationships:</mark> join tables are transformed into relationships, columns on those tables become relationship properties

### <mark style="background: #69E772;">The Matrix Graph Database:</mark>

![](https://i.imgur.com/Kr3nEqs.png)

### <mark style="background: #69E772;">Exercise:</mark>

Convert the following Relational Model into a Graph DB
![](https://i.imgur.com/dl27BIi.png)

![](https://i.imgur.com/vFmv6y1.png)

### <mark style="background: #69E772;">Why to use a Graph Database:</mark>  

<mark style="background: #69E772;">SQL:</mark>  
- It is hard to represent highly connected data in a graph-like structure.  
- They are good for “1 step” relations.  

<mark style="background: #69E772;">NOSQL:</mark>  
- Most NOSQL databases store sets of disconnected documents/values/columns.  
- This makes it difficult to use them for connected data and graphs. One well-known strategy for adding relationships to such stores is to embed an aggregate’s identifier inside the field belonging to another aggregate—effectively introducing foreign keys. But this requires joining aggregates at the application level, which quickly becomes prohibitively expensive

### <mark style="background: #69E772;">Graph Databases:</mark> 

<mark style="background: #69E772;">Data Model:</mark>  
- Nodes with properties  
- Named relationships with properties  

<mark style="background: #69E772;">Examples:</mark>  
- Neo4j, 
- Sones GraphDB, 
- OrientDB, 
- InfiniteGraph,  
- AllegroGraph

### <mark style="background: #69E772;">Graph Databases: Strengths and Weaknesses:</mark> 

<mark style="background: #69E772;">Strengths:</mark>  
- Extremely powerful data model  
- Performant when querying interconnected data  
- Easily to query  

<mark style="background: #69E772;">Weaknesses:</mark>  
- Sharding  
- Not everything is a graph

### <mark style="background: #69E772;">Typical Use Cases for Graph Databases:</mark>

- Recommendations  
- Business Intelligence  
- Social Computing  
- Geospatial  
- Genealogy  
- Time Series Data  
- Web Analytics  
- Fraud Detection

### <mark style="background: #69E772;">Maturity of Data Models:</mark>

![](https://i.imgur.com/NjKWXQr.png)

<mark style="background: #69E772;">Most NOSQL:</mark> ~8 years  

<mark style="background: #69E772;">Relational:</mark> 42 years  

<mark style="background: #69E772;">Graph Theory:</mark> 276 years

### <mark style="background: #69E772;">Neo4j:</mark>

<mark style="background: #69E772;">Introducing Neo4j:</mark>
- Introduced in 2010  
- Developed by Neo Technologies  
- Most Popular Graph Database  
- Open source  
- Java-based  
- NoSQL Graph Database

### <mark style="background: #69E772;">Graph Database:</mark>  

<mark style="background: #69E772;">Nodes represent entities:</mark>  
- Edges represent relationships  
- Connections between data are explored  
- Faster for associative data sets  
- Intuitive  

Optimal for searching social network data

Database that uses graph structures with nodes, edges and properties to store data  

<mark style="background: #69E772;">Provides index-free adjacency:</mark> Every node is a pointer to its adjacent element  

<mark style="background: #69E772;">Edges:</mark>
- hold most of the important information  
- connect nodes to other nodes  
- connect nodes to properties

### <mark style="background: #69E772;">Advantage of Graph Databases:</mark>

When there are relationships that you want to analyse Graph databases become a very nice fit because of the data structure  

Graph databases are very fast for associative  
data sets, like social networks  

Map more directly to object oriented applications  

Object classification and Parent->Child relationships

### <mark style="background: #69E772;">Disadvantages:</mark>

If data is just tabular with not much relationship between the data, graph databases do not fare well  

OLAP support for graph databases is not well developed. Lots of research happening in this area.

### <mark style="background: #69E772;">Major disadvantage:</mark>  

Is it easy to break a graph in pieces?  

Partitioning a graph is very hard!  

A distribute graph-database is challenging

### <mark style="background: #69E772;">Salient features of Neo4j:</mark>

<mark style="background: #69E772;">Neo4j is schema free:</mark> Data does not have to adhere to any convention  

<mark style="background: #69E772;">ACID:</mark> atomic, consistent, isolated and durable for logical units of work  

Easy to get started and use  

Well documented and large developer community  
<mark style="background: #69E772;">Support for wide variety of languages:</mark> 
- Java, 
- Python, 
- Perl, 
- Scala, 
- Cypher, etc

### <mark style="background: #69E772;">More Reasons Why Neo4j is Great:</mark> 

High performance graph operations: Traverse 1,000,000+ relationships/sec on commodity hardware  

32 billion nodes & relationships per Neo4j instance  

64 billion properties per Neo4j instance  

Small footprint - Standalone server is ~65mb