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

### <mark style="background: #69E772;">Some considerations while designing Schema in MongoDB</mark>

Design your schema according to user requirements.  

Combine objects into one document if you will use them together. Otherwise separate them (but make sure there should not be need of joins).  

Duplicate the data (but limited) because disk space is cheap as compare to compute time.  

Do joins while write, not on read.  

Optimize your schema for most frequent use cases.  

Do complex aggregation in the schema.

### <mark style="background: #69E772;">Before Index:</mark>
 
 <mark style="background: #69E772;">What does a database normally do when we query?</mark>  
- MongoDB must scan <mark style="background: #69E772;">every</mark> document.  
- Inefficient because process <mark style="background: #69E772;">large volume</mark> of data

![](https://i.imgur.com/P1PL932.png)

### <mark style="background: #69E772;">Definition of Index:</mark>

Indexes are special data structures that store a small portion of the <mark style="background: #69E772;">collection’s</mark> data set in an easy to traverse form.

![](https://i.imgur.com/CJ9T74i.png)

### <mark style="background: #69E772;">Index in MongoDB:</mark>  

<mark style="background: #69E772;">Creation index:</mark>  ``db.users. createIndex( { score: 1 } )``  

<mark style="background: #69E772;">Show existing indexes:</mark> ``db.users.getIndexes()``  

<mark style="background: #69E772;">Drop index:</mark>  
``db.users.dropIndex( {score: 1}``

<mark style="background: #69E772;">Types:</mark>    
- Single Field Indexes  
- Compound Field Indexes  
- Multikey Indexes

<mark style="background: #69E772;">Single Field Indexes:</mark>  
``db.users. createIndex( { score: 1 } )``

![](https://i.imgur.com/885a68a.png)

<mark style="background: #69E772;">Compound Field Indexes:</mark>  
``db.users. createIndex( { userid:1, score: -1 } )``

![](https://i.imgur.com/SRzjtb7.png)

<mark style="background: #69E772;">Multikey Indexes:</mark>  
``db.users.createIndex( { addr.zip:1} )``

![](https://i.imgur.com/YItYx1r.png)

### <mark style="background: #69E772;">Aggregation:</mark>  

Operations that process data records and return computed results.  

MongoDB provides aggregation operations  

Running data aggregation on the mongod instance simplifies application code and limits resource requirements.  

<mark style="background: #69E772;">Aggregation can be done with:</mark>  
- Pipeline ($group operator)  
- ``Map_reduce``

### <mark style="background: #69E772;">Pipelines:</mark>

MongoDB’s <mark style="background: #69E772;">aggregation framework</mark> is modelled on the concept of data processing pipelines. Documents enter a multi-stage pipeline that transforms the documents into an aggregated result.  

The most basic pipeline stages provide <mark style="background: #69E772;">filters</mark> that operate like queries and <mark style="background: #69E772;">document transformations</mark> that modify the form of the output document.  

Other pipeline operations provide tools for grouping and sorting documents by specific field or fields as well as tools for aggregating the contents of arrays  

Pipeline stages can use <mark style="background: #69E772;">operators</mark> for tasks such as calculating the average or concatenating a string.  

Pipeline is the preferred method for data aggregation in MongoDB.

### <mark style="background: #69E772;">Aggregation using pipeline:</mark>

![](https://i.imgur.com/lmKakx0.png)

### <mark style="background: #69E772;">Some Aggregator Operators:</mark>

![](https://i.imgur.com/cPzxwN3.png)

### <mark style="background: #69E772;">$count // example</mark> 

```JSON
{ "_id" : 1, "subject" : "History", "score" : 88 }  
{ "_id" : 2, "subject" : "History", "score" : 92 }  
{ "_id" : 3, "subject" : "History", "score" : 97 }  
{ "_id" : 4, "subject" : "History", "score" : 71 }  
{ "_id" : 5, "subject" : "History", "score" : 79 }  
{ "_id" : 6, "subject" : "History", "score" : 83 }
``` 

```SQL
db.scores.aggregate(  
[  
{ $match: { score: { $gt: 80} } },  
{ $count: "passing_scores“ }  
])  
Output:  
{ "passing_scores" : 4 }
```

```SQL
db.test_db.find({gender: 'f'});  
db.test_db.find({gender: 'm'});  
db.test_db.find({gender: 'm', $or: [{nationality: 'english'}, {nationality:'american'}]});  
db.test_db.find({gender: 'm', $or: [{nationality: 'english'},{nationality: 'american'}]}).sort({nationality: -1});  
db.test_db.find({gender: 'm', $or: [{nationality: 'english'},{nationality: 'american'}]}).sort({nationality: -1, first: 1});  
db.test_db.find({gender: 'm', $or: [{nationality: 'english'},{nationality: 'american'}]}).limit(2);  
db.test_db.update({first: 'james', last: 'caan'}, {$set:{hair_colour: 'brown'}});  
db.test_db.update({ nationality: "american" },{ $inc: { age: 2} })  
db.test_db.aggregate( [ { $match: { 'age' : { '$gte' : 37 }}}, {$group: { _id: '$nationality', total : { $sum : 1} }}] );  
db.test_db.aggregate( [ { $match: { 'age' : { '$gte' : 37 }}}, {$group: { _id: '$gender', total : { $sum : 1} }}] );  
db.test_db.aggregate( [ {$group: { _id: '$gender', avg_age : { $avg : '$age'} }}] );
```

### <mark style="background: #69E772;">Documents Update:</mark>

MongoDB does not allow to update a field by using an expression containing other fields of the collection  

Therefore, you cannot write ``$field = $field + 1`` or something similar (as we did for SQL)  

For numeric update, use the ``$inc`` operator with update function  

Or.. JavaScript always an option!  

Example:  
```JSON
{ _id: 1, item: "abc123", quantity: 10, metrics: { orders: 2, ratings: 3.5 } }  

db.products.update( { item: "abc123" }, { $inc: { quantity: -2, "metrics.orders": 1 }})
```

### <mark style="background: #69E772;">Multiple Updates:</mark>

Add {multi: true). It controls the ability of mongoDB to update more than one field in a single query  

Try:  
```JSON
> db.pierpaolo.update({first: { $ne: "aa"} }, { $inc: {age : 2}})  

WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })  

db.pierpaolo.update({first: { $ne: "aa"} }, { $inc: {age : 2}},{multi: true})  
WriteResult({ "nMatched" : 7, "nUpserted" : 0,"nModified" : 7 })
```

### <mark style="background: #69E772;">Mongo & JavaScript:</mark>

You can store your commands in a js script and execute them with ``mongo js_file.js``

### <mark style="background: #69E772;">Shell – Script Commands:</mark>

![](https://i.imgur.com/uOutnWV.png)

### <mark style="background: #69E772;">Cursors:</mark>

```JavaScript
var myCursor = db.inventory.find( { type: 'food' } );  

while (myCursor.hasNext()) {  
	print(tojson(myCursor.next())); }  

myCursor.forEach(printjson);  

var documentArray = myCursor.toArray();  
var myDocument = documentArray[3];  

var myDocument = myCursor[3];
```

### <mark style="background: #69E772;">Map Reduce:</mark>

Algorithm (“template”) to perform distributed parallel computation  

Used in MongoDB for performing distributed queries, for instance aggregated queries  

MongoDB provides the function map-reduce  

Map reduce is a concept from functional programming

```JavaScript
map even [3,4,5,6,7,9] = [4,6]
```

<mark style="background: #69E772;">Has two phases:</mark>  
- A <mark style="background: #69E772;">map</mark> stage that processes each document and emits one or more objects for each input document  
- A <mark style="background: #69E772;">reduce</mark> phase that combines the output of the map operation. 
- An <mark style="background: #69E772;">optional</mark> finalise stage for final modifications to the result  

Uses Custom JavaScript functions which provides greater flexibility but is less efficient and more complex than the aggregation pipeline  

Can have output sets that exceed the 16 megabyte output limitation of the aggregation pipeline.

```JSON
db.collection( {  
	mapReduce: <collection>,  
	map: <function>,  
	reduce: <function>,  
	{  
		out: <output>,  
		query: <document>,  
		sort: <document>,  
		limit: <number>,  
	}  
	finalize: <function>,  
	verbose: <boolean> 
} )
```

![](https://i.imgur.com/1Glbnb6.png)

<mark style="background: #69E772;">Map Reduce example:</mark>
![](https://i.imgur.com/Ufvc0K6.png)
![](https://i.imgur.com/qwK1NBZ.png)
![](https://i.imgur.com/hF2J8nF.png)

In MongoDB, map-reduce operations use custom JavaScript functions to <mark style="background: #69E772;">map</mark>, or associate, values to a key. If a key has multiple values mapped to it, the operation <mark style="background: #69E772;">reduces</mark> the values for the key to a single object.

### <mark style="background: #69E772;">The Map and Emit Function:</mark>

In MongoDB, the emit function is used within the MapReduce framework to output key-value pairs during the mapping phase. When you define a MapReduce operation, the map function iterates over each document in a collection, and emit allows you to specify a key and value to pass to the reduce function for further processing.  

The map function is applied to each document in a collection. For each document, you use emit(key, value) to emit a key-value pair. These emitted pairs are then grouped by key.

```JavaScript
function() { ... emit(key, value); }
```

<mark style="background: #69E772;">The map function has the following requirements:</mark>  
- In the map function, reference the current document as <mark style="background: #69E772;">this</mark> within the function.  
- The map function should <mark style="background: #69E772;">not</mark> access the database for any reason.  
- The map function should be pure, or have <mark style="background: #69E772;">no</mark> impact outside of the function (i.e. side effects.)  
- The map function may optionally call ``emit(key,value)`` any number of times to create an output document associating key with value.

<mark style="background: #69E772;">Reduce Function:</mark> The reduce function takes each unique key and an array of all values associated with that key (from the map phase).  

The reduce function processes these values and reduces them to a single result for each unique key.  

The reduce function performs an "aggregation".