### <mark style="background: #69E772;">Database Normalisation:</mark>

Normalisation is a process for assigning attributes to entities. It reduces data redundancies and helps eliminate the data anomalies.  

Normalisation works through a series of stages called normal forms:  
- First normal form (1NF)  
- Second normal form (2NF)  
- Third normal form (3NF)  
- Boyce-Codd NF (BCNF)  

The highest level of normalisation is not always desirable. (we’ll see why...)

### <mark style="background: #69E772;">Scenario:</mark>

![](https://i.imgur.com/Rrtofjw.png)

### <mark style="background: #69E772;">The Need for Normalisation:</mark>

Case of a Construction Company  

Building project -- Project number, Name, Employees assigned to the project.  

Employee -- Employee number, Name, Job classification  

The company charges its clients by billing the hours spent on each project. The hourly billing rate is dependent on the employee’s position.  

Periodically, a report is generated.  

Employees can work on multiple project. The hourly rate for each employee position is fixed

### <mark style="background: #69E772;">Sample Form:</mark>

![](https://i.imgur.com/qtmZhhZ.png)

### <mark style="background: #69E772;">Sample Data:</mark>

![](https://i.imgur.com/lTKv9IF.png)

### <mark style="background: #69E772;">Table Structure based on the form:</mark>

![](https://i.imgur.com/0cKhmtL.png)

### <mark style="background: #69E772;">1NF</mark>

<mark style="background: #69E772;">1NF Definition:</mark> The term first normal form (1NF) describes the tabular format in which:  
- All the primary key attributes are defined.  
- All attributes are dependent on the primary key.  

<mark style="background: #69E772;">In a nutshell:</mark> you must have a valid primary key.  

<mark style="background: #69E772;">Terminology:</mark>  
- Candidate key: one or more field that can act as primary key  
- "dependent" on primary key = A depends on B if I can compute the value of B if I know A.

### <mark style="background: #69E772;">Dependency Diagram:</mark>
 
The primary key components are bold, underlined, and shaded in a different colour.  

The arrows above entities indicate all desirable dependencies, i.e., dependencies that are based on  
PK.  

The arrows below the dependency diagram indicate less desirable dependencies -- partial dependencies

![](https://i.imgur.com/qFutkN8.png)

### <mark style="background: #69E772;">2NF:</mark>

Conversion to Second Normal Form  

Definition: all the non-key attributes are dependant on the full primary key  

Starting with the 1NF format, the database can be converted into the 2NF format by  

Writing each key component on a separate line, and then writing the original key on the last line and  

Writing the dependent attributes after each new key.  

```SQL
PROJECT (PROJ_NUM, PROJ_NAME)  
EMPLOYEE (EMP_NUM, EMP_NAME, JOB_CLASS, CHG_HOUR)  
ASSIGN (PROJ_NUM, EMP_NUM, HOURS)
```

![](https://i.imgur.com/f9gwqCN.png)

<mark style="background: #69E772;">A table is in 2NF if:</mark>  
- It is in 1NF and  
- It includes no partial dependencies; that is, no attribute is dependent on only a portion of the primary key.  
- (It is still possible for a table in 2NF to exhibit <mark style="background: #69E772;">transitive dependency</mark>; that is, one or more attributes may be functionally dependent on a non-key attributes.)

### <mark style="background: #69E772;">3NF:</mark>

Conversion to Third Normal Form: Create a separate table with attributes in a transitive functional dependence relationship.  

```
PROJECT (PROJ_NUM, PROJ_NAME)  
ASSIGN (PROJ_NUM, EMP_NUM, HOURS)  
EMPLOYEE (EMP_NUM, EMP_NAME, JOB_CLASS)  
JOB (JOB_CLASS, CHG_HOUR)
```

<mark style="background: #69E772;">3NF Definition -  A table is in 3NF if:</mark>  
- It is in 2NF and  
- It contains no transitive dependencies.

### <mark style="background: #69E772;">The Completed Database:</mark>

![](https://i.imgur.com/zI4y1N6.png)

### <mark style="background: #69E772;">Boyce-Codd Normal Form (BCNF):</mark>

When a relation has more than one candidate key, anomalies may result even though the relation is in 3NF.  

3NF does not deal satisfactorily with the case of a relation with overlapping candidate keys, i.e. composite candidate keys with at least one attribute in common.  

BCNF is based on the concept of a determinant.  

A determinant is any attribute (simple or composite) on which some other attribute is fully functionally dependent.  
A relation is in BCNF is, and only if, every determinant is a candidate key.

A table is in Boyce-Codd normal form (BCNF) if every determinant in the table is a candidate key.  

(A determinant is any attribute whose value determines other values with a row.)  

If a table contains only one candidate key, the 3NF and the BCNF are equivalent.  

BCNF is a special case of 3NF.  

Figure 5.7 (next slide) illustrates a table that is in 3NF but not in BCNF.  

Figure 5.8 (two slide after this one) shows how the table can be decomposed to conform to the BCNF form.

<mark style="background: #69E772;">A Table in 3NF but not in BCNF: </mark>
![](https://i.imgur.com/CNACcvh.png)

AB = candidate key (and primary composite key)  

C = determinant, since B depends on B (note that B is part of the key and C is a non-key attribute) AC could have been a key as well  

Not in BCNF is C is a determinant but it is not (on its own) a candidate key

<mark style="background: #69E772;">Decomposition of a Table Structure to Meet BCNF Requirements:</mark>

![](https://i.imgur.com/09jjQZv.png)

### <mark style="background: #69E772;">Sample Data for a BCNF conversion:</mark>

![](https://i.imgur.com/51HbN4o.png)

### <mark style="background: #69E772;">Decomposition into BCNF:</mark>

![](https://i.imgur.com/Vxnjjth.png)

### <mark style="background: #69E772;">Denormalisation:</mark>

Normalisation is only one of many database design goals.  

Normalised (decomposed) tables require additional processing, reducing system speed.  

Normalisation purity is often difficult to sustain in the modern database environment. The conflict between design efficiency, information requirements, and processing speed are often resolved through compromises that include de-normalisation.

### <mark style="background: #69E772;">Useful Commands:</mark>

<mark style="background: #69E772;">Move data into a table:</mark>  

```plSQL
INSERT INTO staff( firstName, lastName,  
address, homePhone, cellPhone, latitude,  
longitude )  
SELECT firstName, lastName, address,  
homePhone, cellPhone, latitude, longitude  
FROM gfxContact
```

<mark style="background: #69E772;">Create a table from another table:</mark>

```plSQL
CREATE TABLE EMP (
EMPNO NUMBER(4) NOT NULL,  
ENAME VARCHAR2(10),  
JOB VARCHAR2(9),  
MGR NUMBER(4),  
HIREDATE DATE,  
SAL NUMBER(7, 2),  
COMM NUMBER(7, 2),  
DEPTNO NUMBER(2)
);

INSERT INTO EMP VALUES (7369, 'SMITH', 'CLERK', 7902, TO_DATE('17-DEC-1980', 'DD-MON-YYYY'), 800, NULL, 20);

INSERT INTO EMP VALUES (7499, 'ALLEN', 'SALESMAN', 7698, TO_DATE('20-FEB-1981', 'DD-MON-YYYY'), 1600, 300, 30);

-- Copying selected columns from another table
CREATE TABLE newTable  
AS (SELECT empno, ename FROM emp);
```

### <mark style="background: #69E772;">Type of File:</mark>

Database tables are saved on a collections of files  

<mark style="background: #69E772;">Type of file:</mark>  
- Unordered  
- Ordered  
- Hashed

### <mark style="background: #69E772;">Unordered:</mark>

Also called a <mark style="background: #69E772;">heap</mark> or a <mark style="background: #69E772;">pile</mark> file.  

New records are inserted at the end of the file.  

A <mark style="background: #69E772;">linear search</mark> through the file records is necessary to search for a record.  

This requires reading and searching half the file blocks on the average, and is hence quite expensive.  

Record insertion is quite efficient.  

Reading the records in order of a particular field requires sorting the file records.

### <mark style="background: #69E772;">Ordered Files:</mark>

Also called a <mark style="background: #69E772;">sequential</mark> file.  

File records are kept sorted by the values of an <mark style="background: #69E772;">ordering field</mark>.  

Insertion is expensive: records must be inserted in the correct order.  

It is common to keep a separate unordered overflow (or transaction) file for new records to improve insertion efficiency; this is periodically merged with the main ordered file.  

A <mark style="background: #69E772;">binary search</mark> can be used to search for a record on its ordering field value.  

This requires reading and searching log2 of the file blocks on the average, an improvement over linear search.  

Reading the records in order of the ordering field is quite efficient.

![](https://i.imgur.com/6pHF81B.png)

### <mark style="background: #69E772;">Average Access Times:</mark>

The following table shows the average access time to access a specific record for a given type of file

![](https://i.imgur.com/Dh43K7t.png)

### <mark style="background: #69E772;">Hashed Files:</mark>

The file blocks are divided into M equal-sized <mark style="background: #69E772;">buckets</mark>, numbered ``bucket0, bucket1, ..., bucketM-1.``  

Typically, a bucket corresponds to one (or a fixed number of) disk block.  

One of the file fields is designated to be the <mark style="background: #69E772;">hash key</mark> of the file.  

The record with hash key value K is stored in bucket i, where i=h(K), and h is the <mark style="background: #69E772;">hashing function</mark>.  

Search is very efficient on the hash key.  

Collisions occur when a new record hashes to a bucket that is already full.  

An overflow file is kept for storing such records.  

Overflow records that hash to each bucket can be linked together.
  
There are numerous methods for collision resolution, including the following:  
- <mark style="background: #69E772;">Open addressing:</mark> Proceeding from the occupied position specified by the hash address, the program checks the subsequent positions in order until an unused (empty) position is found.  
- <mark style="background: #69E772;">Chaining:</mark> For this method, various overflow locations are kept, usually by extending the array with a number of overflow positions. In addition, a pointer field is added to each record location. A collision is resolved by placing the new record in an unused overflow location and setting the pointer of the occupied hash address location to the address of that overflow location.  
- <mark style="background: #69E772;">Multiple hashing:</mark> The program applies a second hash function if the first results in a collision. If another collision results, the program uses open addressing or applies a third hash function and then uses open addressing if necessary.

### <mark style="background: #69E772;">Hashed Files - Chaining:</mark>

![](https://i.imgur.com/J3BJuEb.png)

To reduce overflow records, a hash file is typically kept 70-80% full.  

The hash function h should distribute the records uniformly among the buckets  

Otherwise, search time will be increased because many overflow records will exist.  

<mark style="background: #69E772;">Main disadvantages of static external hashing:</mark>  
- Fixed number of buckets M is a problem if the number  of records in the file grows or shrinks.  
- Ordered access on the hash key is quite inefficient (requires sorting the records)

### <mark style="background: #69E772;">Dynamic and Extendible Hashed Files:</mark>

Dynamic and Extendible Hashing Techniques  
- Hashing techniques are adapted to allow the dynamic growth and shrinking of the number of file records.  
- These techniques include the following: <mark style="background: #69E772;">dynamic</mark> <mark style="background: #69E772;">hashing</mark>, <mark style="background: #69E772;">extendible hashing</mark>, and <mark style="background: #69E772;">linear hashing</mark>.  

Both dynamic and extendible hashing use the <mark style="background: #69E772;">binary representation</mark> of the hash value h(K) in order to access a directory.  
- In dynamic hashing the directory is a binary tree. 
- In extendible hashing the directory is an array of size 2d where d is called the <mark style="background: #69E772;">global depth</mark>.

The directories can be stored on disk, and they expand or shrink dynamically.  

Directory entries point to the disk blocks that contain the stored records.  

An insertion in a disk block that is full causes the block to split into two blocks and the records are redistributed among the two blocks. The directory is updated appropriately.  

Dynamic and extendible hashing do not require an overflow area.

### <mark style="background: #69E772;">Dynamic Hashing:</mark>

![](https://i.imgur.com/Uv3pEtD.png)

![](https://i.imgur.com/pJFqO3U.png)

### <mark style="background: #69E772;">Indexes:</mark>

<mark style="background: #69E772;">Indexes</mark> are additional auxiliary access structures with typically provide <mark style="background: #69E772;">either</mark> faster access to data or secondary access paths without effecting the physical storage of the data.  

They are based on <mark style="background: #69E772;">indexing field(s)</mark> that are used to construct the <mark style="background: #69E772;">index</mark>.  

Indexes can be <mark style="background: #69E772;">sparse or dense</mark>. A dense index has an entry for each record.

### <mark style="background: #69E772;">Types of Indexes:</mark>

<mark style="background: #69E772;">Single-Level Indexes:</mark>
- Primary (Clustered or not)  
- Secondary  
- Bitmap  

<mark style="background: #69E772;">Multi-Level Indexes:</mark>  
- Binary Trees  
- B-Trees

### <mark style="background: #69E772;">Single Level Indexes:</mark>

Single Level = there is only 1 level of indirection. The entries in the index are pointing to the data in the table  

Multiple-Index = entries in the index might point to other entries in the index , that eventually point to the data  

A <mark style="background: #69E772;">Primary Index</mark> is specified on the <mark style="background: #69E772;">ordering key field</mark> where each tuple has a <mark style="background: #69E772;">unique</mark> value.  

A <mark style="background: #69E772;">Secondary Index</mark> is specified on a ``NON-ORDERING`` <mark style="background: #69E772;">Field</mark> of the file.

### <mark style="background: #69E772;">Primary Indexes:</mark>

A <mark style="background: #69E772;">Primary Index</mark> is constructed of two parts: The <mark style="background: #69E772;">first field</mark> is the same data type of the <mark style="background: #69E772;">primary key</mark> of a file block of the data file and the <mark style="background: #69E772;">second field</mark> is file <mark style="background: #69E772;">block pointer</mark>.  

If the primary index is clustered, the file is physically sorted using the indexing field. If this is the case:  

The <mark style="background: #69E772;">Anchor Record</mark> or <mark style="background: #69E772;">Block anchor</mark> is the <mark style="background: #69E772;">first</mark> record in a file block. This is where the <mark style="background: #69E772;">value</mark> for the <mark style="background: #69E772;">first field</mark> of the <mark style="background: #69E772;">primary index</mark> come from along with the respective address of that block.

![](https://i.imgur.com/DEpMMYn.png)

<mark style="background: #69E772;">The primary index file is usually smaller than the data  file it’s indexing because:</mark>  
- There are usually fewer index entries than records in the data file (because a block holds more than one record)  
- The individual index records are smaller than data file records  

Binary <mark style="background: #69E772;">search</mark> on index file is faster than binary search on the database  

<mark style="background: #69E772;">But slow for insertion and deletion:</mark>  
- records have to be kept in order in the data file  
- AND index file has to be kept in order too

### <mark style="background: #69E772;">Note on Primary Index (clustered):</mark>

We have shown a primary sparse index, where the “big” file (=table) is physically sorted by the key and the index structure indexes each block. This is usually called a clustered index, since each entry in the index points to a “cluster” or values  

Some DBs (latest Oracle versions) implement primary index like secondary index.  
- The table is left unordered like a heap  
- The index structure has an entry for each record (not each block) and it is a dense index

### <mark style="background: #69E772;">Secondary Indexes:</mark>

An index file that uses a non primary field as an index e.g. Job field in the employee table  

They improve the performance of queries that use attributes <mark style="background: #69E772;">other</mark> than the primary key  

You can use a separate index for every attribute you wish to use in the WHERE clause of your select query  

But there is the overhead of maintaining a large number of these indexes