### <mark style="background: #69E772;">MongoDB profile:</mark>

Document-oriented NoSQL database.  

Schema-free.  

Based on Binary JSON; BSON.  

Organized in Group of Documents  Collections  

Auto-Sharding in order to scale horizontally.  

Simple query language. Rich, document-based queries.  

Map/Reduce support  

Open Source (GNU AGPL v3.0.)

### <mark style="background: #69E772;">Motivations:</mark>

<mark style="background: #69E772;">Problems with SQL:</mark>  
- Rigid schema  
- Not easily scalable (designed for 90’s technology or worse)  
- Requires unintuitive joins

<mark style="background: #69E772;">Benefits of mongoDB:</mark>  
- Easy interface with common languages (Java,   Javascript, PHP, etc.)  
- DB tech should run anywhere (VM’s, cloud, etc.)  
- Keeps essential features of RDBMS’s while learning from key-value noSQL systems

### <mark style="background: #69E772;">Data Model:</mark>

Document-Based  

Documents are in BSON format, consisting of field-value pairs  

Each document stored in a collection  

<mark style="background: #69E772;">Collections;</mark>  
- Have index set in common  
- Like tables of relational dbs.  
- Documents do not have to have uniform structure

### <mark style="background: #69E772;">JSON:</mark>

“JavaScript Object Notation”  

Easy for humans to write/read, easy for computers to parse/generate  

Objects can be nested  

<mark style="background: #69E772;">Built on:</mark>
- name/value pairs  
- Ordered list of values

### <mark style="background: #69E772;">BSON:</mark>

“Binary JSON”  

Binary-encoded serialization of JSON-like docs  

Also allows “referencing”  

Embedded structure reduces need for joins  

<mark style="background: #69E772;">Goals:</mark>  
- Lightweight  
- Traversable  
- Efficient (decoding and encoding

### <mark style="background: #69E772;">BSON Example:</mark>

```JSON
{  
	"_id" : "37010"  
	"city" : "ADAMS",  
	"pop" : 2660,  
	"state" : "TN",  
	"councilman" : {  
		name: "John Smith"  
		address: "13 Scenic Way"  
	}  
}
```

### <mark style="background: #69E772;">The _id Field:</mark>

By default, each document contains an ``_id`` field.  

<mark style="background: #69E772;">This field has a number of special  characteristics:</mark>  
- Value serves as primary key for collection.  
- Value is unique, immutable, and may be any non-array type.  
- Default data type is ``ObjectId``, which is “small, unique, fast to generate, and ordered.” Sorting on an ``ObjectId`` value is roughly equivalent to sorting on creation time.

``_id`` is a 12 bytes hexadecimal number which assures the uniqueness of every document.  

You can provide ``_id`` while inserting the document. If you don’t provide then MongoDB provides a unique id for every document.  

These 12 bytes first 4 bytes for the current timestamp, next 3 bytes for machine id, next 2 bytes for process id of MongoDB server and remaining 3 bytes are simple incremental VALUE.

### <mark style="background: #69E772;">mongoDB vs. SQL:</mark>

![](https://i.imgur.com/gaJmrf5.png)

### <mark style="background: #69E772;">Data type:</mark>

<mark style="background: #69E772;">String</mark> − This is the most commonly used datatype to store the data. String in MongoDB must be UTF-8 valid.  

<mark style="background: #69E772;">Integer</mark> − This type is used to store a numerical value. Integer can be 32 bit or 64 bit depending upon your server.  

<mark style="background: #69E772;">Boolean</mark> − This type is used to store a boolean (true/ false) value.  

<mark style="background: #69E772;">Double</mark> − This type is used to store floating point values.  

<mark style="background: #69E772;">Arrays</mark> − This type is used to store arrays or list or multiple values into one key.  

<mark style="background: #69E772;">Timestamp</mark> − ``ctimestamp``. This can be handy for recording when a document has been modified or added.  

<mark style="background: #69E772;">Object</mark> − This datatype is used for embedded documents.

### <mark style="background: #69E772;">Data Type</mark>

<mark style="background: #69E772;">Null</mark> − This type is used to store a Null value.  

<mark style="background: #69E772;">Symbol</mark> − This datatype is used identically to a string; however, it's generally reserved for languages that use a specific symbol type.  

<mark style="background: #69E772;">Date</mark> − This datatype is used to store the current date or time in UNIX time format. You can specify your own date time by creating object of Date and passing day, month, year into it.  

<mark style="background: #69E772;">Object ID</mark> − This datatype is used to store the document’s ID.  

<mark style="background: #69E772;">Binary data</mark> − This datatype is used to store binary data.  

<mark style="background: #69E772;">Code</mark> − This datatype is used to store JavaScript code into the document.  

<mark style="background: #69E772;">Regular expression</mark> − This datatype is used to store regular expression.

### <mark style="background: #69E772;">Basic operations:</mark>

![](https://i.imgur.com/t6iBn4u.png)

### <mark style="background: #69E772;">CRUD operations - create:</mark>

![](https://i.imgur.com/gsnczTa.png)

![](https://i.imgur.com/CaGLwYa.png)

![](https://i.imgur.com/dOPMsK1.png)

### <mark style="background: #69E772;">CRUD operations - read:</mark>

![](https://i.imgur.com/Aep3rKq.png)

### <mark style="background: #69E772;">Logical tests:</mark>

![](https://i.imgur.com/SbYXPkY.png)

### <mark style="background: #69E772;">Querying:</mark>

```SQL
db.<collection>.find({ $or: [  
<field>:<value1>  
<field>:<value2> ]  
})  
SELECT *  
FROM <table>  
WHERE <field> = <value1> OR <field> = <value2>;  
Alternative: checking for multiple values of same field  
db.<collection>.find({<field>: {$in [<value>, <value>]}})
```

### <mark style="background: #69E772;">CRUD operations - update:</mark>

![](https://i.imgur.com/IOe0L80.png)

### <mark style="background: #69E772;">CRUD operations - delete:</mark>

![](https://i.imgur.com/Rzx0TTw.png)

### <mark style="background: #69E772;">Schema Design:</mark>

<mark style="background: #69E772;">SQL vs Mongo Concepts:</mark>
![](https://i.imgur.com/rfgAdYs.png)

### <mark style="background: #69E772;">Mongo is basically schema-free:</mark>

The purpose of schema in SQL is for meeting the requirements of tables and SQL implementation  

Every “row” in a database “table” is a data structure, much like a “struct” in C, or a “class” in Java. A table is then an array (or list) of such data structures  

So what we design in mongoDB is basically same way how we design a compound data type binding in JSON

### <mark style="background: #69E772;">There are some patterns:</mark>

<mark style="background: #69E772;">Embedding:</mark> 
- Embed the document into the other document  
- Similar to denormalized joins

<mark style="background: #69E772;">Linking (also known as reference):</mark>  
- Use the id of a document as a field in another document  
- similar to a FK in SQL

### <mark style="background: #69E772;">One to One relationship - embedding:</mark>

![](https://i.imgur.com/uXnJ4UF.png)

### <mark style="background: #69E772;">One to many relationship - embedding:</mark>

![](https://i.imgur.com/8u1uw9a.png)

### <mark style="background: #69E772;">One to many relationship –  Linking</mark>

![](https://i.imgur.com/gEJqwEc.png)

### <mark style="background: #69E772;">Linking vs. Embedding:</mark>

Embedding is a bit like pre-joining data  

Document level operations are easy for the server to handle  

Embed when the “many” objects always appear with (viewed in the context of) their parents.  

Linking when you need more flexibility, less redundancy. It is not the MongoDB way.

### <mark style="background: #69E772;">Modeling Checkouts:</mark>

```JSON
student = {  
	_id: "joe"  
	name: "Joe Bookreader",  
	join_date: ISODate("2011-10-15"),  
	address: { ... }  
}  
book = {  
	_id: "123456789"  
	title: "MongoDB: The Definitive Guide",  
	authors: [ "Kristina Chodorow", "Mike Dirolf" ],
	...
}
```

```JSON
student = {  
	_id: "joe"  
	name: "Joe Bookreader",  
	join_date: ISODate("2011-10-15"),  
	address: { ... },  
	checked_out: [  
	{ _id: "123456789", checked_out: "2012-10-15" },  
	{ _id: "987654321", checked_out: "2012-09-12" },  
	...  
	]  
}
```

### <mark style="background: #69E772;">Model Tree Structure:</mark>

![](https://i.imgur.com/ss0Y4JD.png)

```SQL
db.categories.insert( { _id: "MongoDB", parent: "Databases" } )  
db.categories.insert( { _id: "dbm", parent: "Databases" } )  
db.categories.insert( { _id: "Databases", parent: "Programming" } )  
db.categories.insert( { _id: "Languages", parent: "Programming" } )  
db.categories.insert( { _id: "Programming", parent: "Books" } )  
db.categories.insert( { _id: "Books", parent: null } )  
db.categories.findOne( { _id: "MongoDB" } ).parent  
db.categories.ensureIndex( { parent: 1 } )  
db.categories.find( { parent: "Databases" } )
```

### <mark style="background: #69E772;">Another Example:</mark>

Suppose a client needs a database design for his blog/website and see the differences between RDBMS and MongoDB schema design.  

Website has the following requirements:  
- Every post has the unique title, description and url.  
- Every post can have one or more tags.  
- Every post has the name of its publisher and total number of likes.  
- Every post has comments given by users along with their name, message, data-time and likes.  
- On each post, there can be zero or more comments.

![](https://i.imgur.com/4AYsQHw.png)

### <mark style="background: #69E772;">MongoDB Document:</mark>

```JSON
{  
	_id: POST_ID  
	title: TITLE_OF_POST,  
	description: POST_DESCRIPTION,  
	by: POST_BY,  
	url: URL_OF_POST,  
	tags: [TAG1, TAG2, TAG3],  
	likes: TOTAL_LIKES,  
	comments: [  
		{  
			user:'COMMENT_BY',  
			message: TEXT,  
			dateCreated: DATE_TIME,  
			like: LIKES  
		},  
		{  
			user:'COMMENT_BY',  
			message: TEXT,  
			dateCreated: DATE_TIME,  
			like: LIKES  
		}  
	]  
}
```

# <mark style="background: #FF5582A6;">SLIDE 35</mark>
