### <mark style="background: #69E772;">Type of File:</mark>

Database tables are saved on a collections of files

<mark style="background: #69E772;">Type of file:</mark>
- Unordered
- Ordered
- Hashed

### <mark style="background: #69E772;">Type of File: Unordered</mark>

Also called a <mark style="background: #69E772;">heap</mark> or a <mark style="background: #69E772;">pile</mark> file.

New records are inserted at the end of the file.

A <mark style="background: #69E772;">linear search</mark> through the file records is necessary to search for a record. This requires reading and searching half the file blocks on the average, and is hence quite expensive.

Record insertion is quite efficient.

Reading the records in order of a particular field requires sorting the file records. 

### <mark style="background: #69E772;">Ordered Files:</mark>

Also called a <mark style="background: #69E772;">sequential</mark> file.

File records are kept sorted by the values of an <mark style="background: #69E772;">ordering field</mark>.

Insertion is expensive: records must be inserted in the correct order.

It is common to keep a separate unordered <mark style="background: #69E772;">overflow</mark> (or <mark style="background: #69E772;">transaction</mark>) file for new records to improve insertion efficiency; this is periodically merged with the main ordered file.

A <mark style="background: #69E772;">binary search</mark> can be used to search for a record on its <mark style="background: #69E772;">ordering field</mark> value.

This requires reading and searching log2 of the file blocks on the average, an improvement over linear search.

Reading the records in order of the ordering field is quite efficient.

![](https://i.imgur.com/c5Ndqu0.png)

### <mark style="background: #69E772;">Average Access Times:</mark>

The following table shows the average access time to access a specific record for a given type of file

![](https://i.imgur.com/JTzu8BH.png)

### <mark style="background: #69E772;">Hashed Files:</mark>

The file blocks are divided into M equal-sized buckets, numbered bucket0, bucket1, ..., bucketM-1.

Typically, a bucket corresponds to one (or a fixed number of) disk block.

One of the file fields is designated to be the <mark style="background: #69E772;">hash key</mark> of the file.

The record with hash key value K is stored in bucket i, where i=h(K), and h is the <mark style="background: #69E772;">hashing function</mark>.

Search is very efficient on the hash key.

Collisions occur when a new record hashes to a bucket that is already full.
- An overflow file is kept for storing such records.
- Overflow records that hash to each bucket can be linked together. 

There are numerous methods for collision resolution, including the following:

<mark style="background: #69E772;">Open addressing:</mark> Proceeding from the occupied position specified by the hash address, the program checks the subsequent positions in order until an unused (empty) position is found. 

<mark style="background: #69E772;">Chaining:</mark> For this method, various overflow locations are kept, usually by extending the array with a number of overflow positions. In addition, a pointer field is added to each record location. A collision is resolved by placing the new record in an unused overflow location and setting the pointer of the occupied hash address location to the address of that overflow location. 

<mark style="background: #69E772;">Multiple hashing:</mark> The program applies a second hash function if the first results in a collision. If another collision results, the program uses open addressing or applies a third hash function and then uses open addressing if necessary.

### <mark style="background: #69E772;">Hashed Files - Chaining:</mark>

![](https://i.imgur.com/pjIgtt7.png)

To reduce overflow records, a hash file is typically kept 70-80% full.

The hash function h should distribute the records uniformly among the buckets

Otherwise, search time will be increased because many overflow records will exist.

Main disadvantages of static external hashing:

Fixed number of buckets M is a problem if the number of records in the file grows or shrinks.

Ordered access on the hash key is quite inefficient (requires  sorting the records).

### <mark style="background: #69E772;">Dynamic Hashing:</mark>

![](https://i.imgur.com/oAQHXxv.png)

### <mark style="background: #69E772;">Extendible Hashing:</mark>

![](https://i.imgur.com/76GX5Km.png)

### <mark style="background: #69E772;">Indexes:</mark>

<mark style="background: #69E772;">Indexes</mark> are additional auxiliary access structures with typically provide either faster access to data or secondary access paths without effecting the physical storage of the data.

They are based on <mark style="background: #69E772;">indexing field(s)</mark> that are used to construct the <mark style="background: #69E772;">index</mark>.

Indexes can be <mark style="background: #69E772;">sparse</mark> or <mark style="background: #69E772;">dense</mark>. A dense index has an entry for each record.

<mark style="background: #69E772;">Single-Level Indexes:</mark>
- Primary (Clustered or not)
- Secondary
- Bitmap

<mark style="background: #69E772;">Multi-Level Indexes:</mark>
- Binary Trees
- B-Trees

Single Level = there is only 1 level of indirection. The entries in the index are pointing to the data in the table

Multiple-Index = entries in the index might point to other entries in the index , that eventually point to the data

A <mark style="background: #69E772;">Primary Index</mark> is specified on the <mark style="background: #69E772;">ordering key field</mark> where each tuple has a <mark style="background: #69E772;">unique</mark> value.

A <mark style="background: #69E772;">Secondary Index</mark> is specified on a <mark style="background: #69E772;">NON-ORDERING Field</mark> of the file.

### <mark style="background: #69E772;">Primary Indexes:</mark>

A <mark style="background: #69E772;">Primary Index</mark> is constructed of two parts: The <mark style="background: #69E772;">first field</mark> is the same data type of the primary key of a file block of the data file and the second field is file block pointer.

If the primary index is clustered, the file is physically sorted using the indexing field. If this is the case:

The <mark style="background: #69E772;">Anchor Record</mark> or <mark style="background: #69E772;">Block anchor</mark> is the <mark style="background: #69E772;">first</mark> record in a file block. This is where the <mark style="background: #69E772;">value</mark> for the <mark style="background: #69E772;">first field</mark> of the <mark style="background: #69E772;">primary index</mark> come from along with the respective address of that block.

![](https://i.imgur.com/HEXDLxH.png)

### <mark style="background: #69E772;">Primary Indexes (clustered)</mark>

The primary index file is usually smaller than the data file it’s indexing because
- There are usually fewer index entries than records in the data file (because a block holds more than one record)
- The individual index records are smaller than data file records

Binary <mark style="background: #69E772;">search</mark> on index file is faster than binary search on the database

But slow for insertion and deletion 
- records have to be kept in order in the data file
- AND index file has to be kept in order too

### <mark style="background: #69E772;">Note on Primary Index (clustered):</mark>

We have shown a primary <mark style="background: #69E772;">sparse</mark> index, where the “big” file (=table) is physically sorted by the key and the index structure indexes each block. This is usually called a clustered index, since each entry in the index points to a “cluster” or values

Some DBs (latest Oracle versions) implement primary index like secondary index. 
- The table is left unordered like a heap
- The index structure has an entry for each record (not each block) and it is a dense index

### <mark style="background: #69E772;">Secondary Indexes:</mark>

An index file that uses a non primary field as an index e.g. Job field in the employee table

They improve the performance of queries that use attributes <mark style="background: #69E772;">other</mark> than the primary key

You can use a separate index for every attribute you wish to use in the ``WHERE`` clause of your select query

But there is the overhead of maintaining a large number of these indexes 

A <mark style="background: #69E772;">Secondary Index</mark> is an <mark style="background: #69E772;">ordered file</mark> with two fields.  The first is of the same data type as some <mark style="background: #69E772;">non-ordering</mark> field and the second is either a block or a record pointer.

If the <mark style="background: #69E772;">entries</mark> in this <mark style="background: #69E772;">non-ordering</mark> field <mark style="background: #69E772;">must</mark> be <mark style="background: #69E772;">unique</mark> this field is sometime referred to as a <mark style="background: #69E772;">Secondary Key</mark>. This results in a dense index.

For a secondary index, an external index file has a list of pointers to the various values of the indexed column (i.e. It’s a logical index, not physical)  so you can have many secondary indexes
- What would a secondary index to a telephone directory look like? E.g. Road Name?
- WHY would you use a secondary index?

### <mark style="background: #69E772;">Primary Indexes (not clustered):</mark>

A <mark style="background: #69E772;">Primary Index</mark> can also be not clustered. In this case, the file (table) is not physically sorted by the index key.

For each entry in the table, there is an entry in the index, so a primary index not clustered is a dense index.

![](https://i.imgur.com/TbQHCBr.png)


### <mark style="background: #69E772;">Secondary Index on a Non-key field:</mark>

A secondary index is an index defined on a non-key field. It can be implemented as a primary index (not clustered) but since there is <mark style="background: #69E772;">no guarantee</mark> that the value will be <mark style="background: #69E772;">unique</mark> the previous index method will not work in all the case.
- <mark style="background: #69E772;">Option 1:</mark> Include index entries for each record.  This results in multiple entries of the same value.
- <mark style="background: #69E772;">Option 2:</mark> Use variable length records with a pointer to each block/record with that value.
- <mark style="background: #69E772;">Option 3:</mark> Have the pointer; point to a block or chain of blocks that contain pointers to all the blocks/records that contain the field value. Example of multi-level index

![](https://i.imgur.com/nMjJWpC.png)

### <mark style="background: #69E772;">Multilevel Indexes:</mark>

A <mark style="background: #69E772;">Multilevel Index</mark> is where you construct an <mark style="background: #69E772;">Second- Level</mark> index on a <mark style="background: #69E772;">First-Level</mark> Index. Continue this process until the entire index can be contained in a <mark style="background: #69E772;">Single File Block</mark>.

This allows much faster access than binary search because at each level the size of the index is reduced by the fan out factor. Rather just by 2 as in binary search.

![](https://i.imgur.com/0K6Gs1T.png)


### <mark style="background: #69E772;">Bitmap Index:</mark>

An index implemented as a map of bits

Each unique entry in the index is a string of bits

Usually used on fields that are not (or rarely)  modified 

Fields with low cardinality

Used in read-only environment like data warehouses

Typical example: day of the week, gender,…

<mark style="background: #69E772;">How many bytes is a bitmap index on:</mark>
- Day of the week for 10 millions records 
- Gender for 1 billion records

![](https://i.imgur.com/18a9SKZ.png)

![](https://i.imgur.com/u5yJKVk.png)


### <mark style="background: #69E772;">Multilevel index:</mark>

In databases, multi-level indexes are implemented using a tree structure

A tree is a data structure with specific rules, which ones?

### <mark style="background: #69E772;">Explain Analyse in Postgres:</mark>

It gives information on query execution time, cost and steps need to compute the output of each query

![](https://i.imgur.com/f6Pk6Ic.png)


### <mark style="background: #69E772;">Query Cost:</mark>

Cost: arbitrary units, 1 unit = cost to read a page (of data) sequentially. They make sense only to compare queries.
	Sort  (cost=66.83..69.33 rows=1000 width=17) 

<mark style="background: #69E772;">Two costs:</mark>
- Startup cost. This is an estimate of how long it will take to fetch the first row
- Total cost: how long will it take to return all the rows the query requires

Rows = number of rows (estimated) and width = estimated size in bytes

Using ``EXPLAIN ANALYZE`` you can also see the actual time spent executing the query dividing in “planning time” and “execution time”. 

```plSQL
explain analyze select * from persons;

Seq Scan on persons  (cost=0.00..214.00 rows=10000 width=60) (actual time=0.015..0.358 rows=10000 loops=1)

-- Planning Time: 0.063 ms
-- Execution Time: 0.526 ms
```

### <mark style="background: #69E772;">How is cost computed?</mark>

```plSQL
explain analyze select * from persons; 
Seq Scan on persons  (cost=0.00..214.00 rows=10000 width=60)
```


<mark style="background: #69E772;">Why total cost of 214?</mark>
- The cost parameters seq_page_cost, cpu_tuple_cost  have the following defaults values:
- seq_page_cost  = 1, 
- cpu_tuple_cost  = 0.01 (time to process each tuple, see https://postgresqlco.nf/doc/en/param/cpu_tuple_cost/)

Total cost of Seq Scan = (estimated sequential page reads * seq_page_cost) + (estimated rows returned * cpu_tuple_cost)

How do I know how many pages were read?

```plSQL
explain (analyze, buffers) select * from persons; 
Seq Scan on persons  (cost=0.00..214.00 rows=10000 width=60)
Buffers: shared hit=114
```

We need to execute the explain with the keyword buffers as well

```
Total cost of Seq Scan = (estimated sequential page reads * seq_page_cost) + (estimated rows returned * cpu_tuple_cost)
= (114 * 1) + (10000 * 0.01) = 114 + 100.00 = 214.00
```

<mark style="background: #69E772;">Some other parameters (default value):</mark>
- ``random_page_cost``  (4) = estimate of the cost of a non-sequentially fetched disk page
- ``cpu_operator_cost`` (0.025) = estimate of the cost of processing each operator or function call
- ``cpu_index_tuple_cost``  (0.005) =  estimate of the cost of processing each index entry during an index scan

```plSQL
explain analyze select * from persons; 

Index Scan Backward using per_index on persons  (cost=0.29..387.29 rows=10000 width=60)
  Buffers: shared hit=171
```

<mark style="background: #69E772;">Total cost:</mark>
- 171 pages read => 171 * 1 = 171 (cost for scan the table)
- 10000 rows in the index => 10000 * 0.05 = 500
- 32 * 1 + 200 * 0.05 + 2000 * 0.01 =32+20+10 = 62

### <mark style="background: #69E772;">Cost of Query:</mark>

![](https://i.imgur.com/IsiVKhD.png)


There is an index on the unique1 field

The second query has a higher cost even if it filters the row, why?

The third query creates a bitmap index, more info next slide…

### <mark style="background: #69E772;">Bitmap Index:</mark>

In order to improve query performance, Postgres might decide to create a bitmap index in memory.

The bitmap of pages is created dynamically for each query. It is not cached or re-used, and it is discarded at the end of the bitmap index scan.

For every row, a set of bit is added to store the location of the data

What is "Recheck condition" and why is it needed?

If the bitmap gets too large we convert it to "lossy" style, in which we only remember which pages contain matching tuples instead of remembering each tuple individually (the index is no more by row but by page). When that happens, the table-visiting phase has to examine each tuple on the page and recheck the scan condition to see which tuples to return.  (Tom Lane)

A bitmap index scan becomes lossy if ``work_mem`` is not big enough to contain a bitmap that contains one bit per table row. 

