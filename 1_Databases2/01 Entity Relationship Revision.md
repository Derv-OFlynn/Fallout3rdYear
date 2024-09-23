After completing this chapter, you should be able to:
- Explain the three phases of <mark style="background: #69E772;">database design</mark>, (Why are multiple phases useful?)
- Evaluate the significance of the <mark style="background: #69E772;">Entity-Relationship Model</mark> (ER model) for DB design,  
- Enumerate the basic constructs of the ER model,
- Develop <mark style="background: #69E772;">ER diagrams</mark> (schemas in the ER model) for a given application,  
- <mark style="background: #69E772;">Translate</mark> ER models into equivalent (as far as possible) relational models.

### <mark style="background: #69E772;">Database Design:</mark>

Overall goal of DBMS usage: Efficiently develop programs to support given real-world tasks.  

These programs need to <mark style="background: #69E772;">store data persistently</mark>.  

To develop these programs, apply proven methods of <mark style="background: #69E772;">software engineering</mark> - specialized to support <mark style="background: #69E772;">data-intensive</mark> programs.  
 
<mark style="background: #69E772;">Database Design</mark> is the process of developing a  
<mark style="background: #69E772;">database schema</mark> for a given application.  
DB design is a subtask of the overall software engineering effort.

The specification of programs and data is intertwined:  
- The schema should contain the data needed by the programs.  
- Programs are often easy to develop once the structure of the data to be manipulated has been specified.  
  
Data, however, is an <mark style="background: #69E772;">independent resource </mark>:
- Typically, additional programs will be developed later based on the collected data.  
- Also, <mark style="background: #69E772;">ad-hoc</mark> queries will be posed against the DB

During DB design, a <mark style="background: #69E772;">formal model of the relevant aspects</mark> of the real world (“mini world”, “domain of discourse”) must be built.  

Once the DB is up and running, questions will be posed against the DB. Knowledge of these questions beforehand is important input to the DB design process and helps to identify the  
relevant parts of the real world.  

In some sense, the real world is the <mark style="background: #69E772;">measure of correctness</mark> for the DB schema: the possible DB states should correspond to the states of the real world.

DB design is not easy for a variety of reasons: 
- <mark style="background: #69E772;">Expertise:</mark> The designer must become an expert for the application domain or needs to talk to such experts.  Depending on the domain, these experts might not be used to give a complete and formal account of their field.  
- <mark style="background: #69E772;">Flexibility:</mark> The real world typically permits exceptions and corner cases. Does the DB schema need to reflect these?  
- <mark style="background: #69E772;">Size:</mark> Database schemas may become huge (in terms of number of relations, attributes, constraints).  
- Due to this complexity, DB design is a <mark style="background: #69E772;">multi-step</mark> process.

<mark style="background: #69E772;">Three Phases of DB Design:</mark>
1. <mark style="background: #69E772;">Conceptual Database Design</mark>. Produces the initial model of the mini world in a conceptual data model (e.g., in the ER model).  
2. <mark style="background: #69E772;">Logical Database Design.</mark> Transforms the conceptual schema into the data model supported by the DBMS (e.g., the relational model).  
3. <mark style="background: #69E772;">Physical Database Design.</mark> Design indexes, table distribution, buffer size, etc., to maximize performance of the final system (subject of “Datenbanken II ”).

<mark style="background: #69E772;">Why multiple design phases?</mark>  
- Partition the problem, attack one sub-problem after the other. 
- For example, during conceptual design there is no need to worry about performance aspects or limitations of the specific SQL dialect of the RDBMSs.  
- DBMS features do not influence the conceptual design and only partially influence the logical design.
- Thus, the conceptual design work is not invalidated, if a different DBMS is used later on.

### <mark style="background: #69E772;">Examples:</mark>

<mark style="background: #69E772;">ER schema in graphical notation:</mark>  

![](https://i.imgur.com/FPMV07G.png)

- This mini world talks about instructors and courses.  
- Instructors teach courses.
- Instructors have a name and a phone number.  
- Courses are numbered and have titles.

<mark style="background: #69E772;">A possible state of this mini world:</mark>

![](https://i.imgur.com/zme396Y.png)

### <mark style="background: #69E772;">The ER Model:</mark>

The <mark style="background: #69E772;">Entity-Relationship Model</mark> is often referred to as a <mark style="background: #69E772;">semantic data</mark> model, because it more closely resembles real world scenarios than, e.g., the relational model.  
- In the ER model, we model the concept of “Instructors.” In the relational model we deal with names and phone numbers.  
- In the ER model, there is a distinction between <mark style="background: #69E772;">entities</mark> (objects) and <mark style="background: #69E772;">relationships</mark> between such entities. In the relational model, both concepts are represented by relations.

Proposed by Peter Chen (1976), today at Louisiana State University (http://bit.csc.lsu.edu/∼chen/chen.html).  
- The ER model comes with a graphical notation which helps to establish quick overviews of database application schemas.  
- Such ER diagrams are also a great way to communicate schemas to non-expert/future DB users.  
- There are no “ER Model DBMS”. Instead, we will describe a translation of ER model concepts into the relational model.

### <mark style="background: #69E772;">Basic ER Model Concepts:</mark>

<mark style="background: #69E772;">Entities:</mark>  
- An object in the mini world about which information is to be stored. Examples: persons, books, courses.  
- <mark style="background: #69E772;">Note:</mark> entities do not have to correspond to objects of physical existence. Entities may also represent conceptual objects like, e.g., vacations.  
- The mini world that has to be modelled can contain only a finite number of objects.  
- It must be possible to distinguish entities from each other, i.e., objects must have some identity.
- <mark style="background: #69E772;">Examples:</mark> entity book identified by ISBN number, entity vacations identified by travel agency booking number.

<mark style="background: #69E772;">Attribute: </mark> 
- A <mark style="background: #69E772;">property</mark> or feature of an entity (or relationship, see below). 
- Example: the title of this course entity is “Foundations of Databases.”  
- The <mark style="background: #69E772;">value</mark> of an attribute is an element of a data type like string, integer, date. 
- These values have a <mark style="background: #69E772;">printable representation</mark> (which entities have not).

<mark style="background: #69E772;">Relationship:</mark>  
- A <mark style="background: #69E772;">relation</mark> - not in the strict relational model sense - between <mark style="background: #69E772;">pairs of entities</mark> (a binary relationship).  
- Example: Grust (an entity) teaches (a relationship) the course “Foundations of Databases” (an entity)

![](https://i.imgur.com/5kG1gax.png)

Relationships may also exist <mark style="background: #69E772;">entities of the same type</mark> (“recursive relationship”):

![](https://i.imgur.com/t7Od8jP.png)

In this case, <mark style="background: #69E772;">role names</mark> have to be attached to the connecting edges.  

In the ER model, role names may be attached to any kind of relationship for documentation purposes.

Relationships may have attributes, too.

![](https://i.imgur.com/baSOex3.png)

This models the fact that a number of <mark style="background: #69E772;">points</mark> is stored for  
every pair of a student X and an exercise Y such that X  
submitted a solution for Y

### <mark style="background: #69E772;">Graphical Syntax:</mark>

1. An ER diagram contains <mark style="background: #69E772;">boxes</mark>, <mark style="background: #69E772;">diamonds</mark>, <mark style="background: #69E772;">ovals</mark>, plus <mark style="background: #69E772;">interconnecting lines</mark>.  
2. Boxes, diamonds, and ovals are each <mark style="background: #69E772;">labelled</mark> by a string.  
	- Box labels are unique in the entire diagram. 
	- Oval labels are unique for a single box or diamond.  
	- Diamond labels are unique for a pair of connected boxes.  
3. Interconnecting lines are only allowed between box - diamond, box -oval, diamond - oval.  
4. A diamond has exactly two connecting lines to boxes. There may be any number of connections to ovals. 
5. An oval has exactly one connecting line.

### <mark style="background: #69E772;">Cardinalities:</mark>

<mark style="background: #69E772;">General ER relationship:</mark>
![](https://i.imgur.com/GtUMbSE.png)

In general, there is no restriction on how often an entity  
participates in an relationship R.  

An entity can be connected to one entity of the other type, to more than one, or it can have no R-partner at all.  

However, specific application semantics dictate to how many E2 entities an E1 entity can be related:

![](https://i.imgur.com/HZMO3qt.png)

The ER model introduces the <mark style="background: #69E772;">(min, max) notation</mark> to specify an <mark style="background: #69E772;">interval</mark> of possible participations in a relationship:

![](https://i.imgur.com/fVVJEsd.png)

An entity of type E1 may be related to at least m1 and at most n1 entities of type E2.  

Likewise, m2 is the minimum number and n2 is the maximum number of E1 entities to which an E2 entity is related

<mark style="background: #69E772;">Extensions:</mark>  
- “∗” may be used as maximum if there is no limit.  
- (0, ∗) means no restriction at all (general relationship)

![](https://i.imgur.com/fHzZqFm.png)

![](https://i.imgur.com/pEHUmMa.png)

<mark style="background: #69E772;">Derive cardinalities from verbal specifications:</mark>
![](https://i.imgur.com/E2G24Si.png)

![](https://i.imgur.com/shlGKxu.png)


### <mark style="background: #69E772;">Selecting Cardinalities</mark>

Sometimes a sketch of a valid database state may help in selecting the right cardinalities, e.g., for the state sketched on slide 243, a viable cardinality for E1—R may be (0, 3).  

Application knowledge might lead to <mark style="background: #69E772;">weaker restrictions</mark>, in this example (0, 5) or (0, ∗). A cardinality (a, b) is <mark style="background: #69E772;">weaker</mark> than (c, d) if a 6 c and d 6 b.  

In real applications, the cardinalities (0, 1), (1, 1), and (0, ∗) are the most common and especially <mark style="background: #69E772;">easy to enforce in the relational model</mark>.

### <mark style="background: #69E772;">Common Cases:</mark>

Normally, the <mark style="background: #69E772;">minimum cardinality</mark> will be 0 or 1, and the <mark style="background: #69E772;">maximum cardinality</mark> will be 1 or ∗.  

Thus, only the (0, 1), (1, 1), (0, ∗), (1, ∗) cardinalities are common in practice.  

To understand a relationship, one must know the cardinality specifications on <mark style="background: #69E772;">both sides</mark>.  
The maximum cardinalities on each side are used to distinguish between <mark style="background: #69E772;">many-to-many</mark>, <mark style="background: #69E772;">one-to-many</mark> / <mark style="background: #69E772;">many-to-one</mark>, and <mark style="background: #69E772;">one-to-one</mark> relationships.

<mark style="background: #69E772;">Many-to-many relationships:</mark>
- Both maximum cardinalities are ∗ (the minimum cardinalities are 0 or 1):
- This is the most general/least restrictive case of a relationship.  
- When translated into the relational model, the representation of many-to-many relationships requires an extra table.
![](https://i.imgur.com/ovJQLVo.png)

<mark style="background: #69E772;">One-to-many relationships:</mark>
- Maximum cardinality 1 on the “many” side and ∗ on the “one” side
- One-to-many relationships do not require an extra table in an equivalent representation in the relational model
![](https://i.imgur.com/KMKy3Ax.png)

<mark style="background: #69E772;">One-to-one relationships</mark>
- Maximum cardinality 1 on both sides
- Note how <mark style="background: #69E772;">mandatory</mark> or <mark style="background: #69E772;">optional</mark> participation in an relationship determines the <mark style="background: #69E772;">minimum cardinalities</mark>.
![](https://i.imgur.com/81UVCFZ.png)

### <mark style="background: #69E772;">Cardinalities: Alternative Notations:</mark>

