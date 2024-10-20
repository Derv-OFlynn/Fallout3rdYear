#CloudComputing
### <mark style="background: #BABD00;">Design Challenges of non-functional requirements:</mark>

Our objective is to understand the non-functional requirements of a distributed system.  

These are concerned with the <mark style="background: #BABD00;">quality</mark> of the system  

Certain requirements are common to many distributed systems:  
- Resource Sharing  
- Openness  
- Concurrency  
- Scalability  
- Fault Tolerance  
- Transparency

### <mark style="background: #BABD00;">Resource Sharing:</mark>

Ability to use any hardware, software or data anywhere in the system  

Cost effective for sharing expensive resources  

Security implications due to many users accessing the common resources  
- How do control/restrict access? Resource manager components  
- Resource manager controls access, provides naming scheme and controls concurrency  
- Client-server v n-tier architecture (distributed objects)

### <mark style="background: #BABD00;">Openness:</mark>

Openness is concerned with extendibility and improvability of distributed systems  

Well defined and documented interfaces of components need to be published. 

Allows other components know what services are available  

System needs to adhere to recognized standards  

Components achieve openness by communicating using well-defined interfaces  
- supports changing functional requirements as an organisation grows  
- Helps preserve the investment  
- Supports the integration of new components

<mark style="background: #BABD00;">Coupling</mark> refers to the degree of dependency between components in a system.

### <mark style="background: #BABD00;">Concurrency:</mark>

Components in distributed systems are executed in concurrent processes  

Components access and update shared resources (e.g. variables, databases, device drivers)  

Integrity of the system may be violated if concurrent updates are not coordinated  
- Lost updates  
- Inconsistent analysis (Non-Repeatable Read)

<mark style="background: #BABD00;">Lost Update:</mark>
- Lost updates occur when two or more processes select the same data and then update the data based on the value originally selected.  
- Each process is unaware of the other processes.  
- The last update overwrites updates made by the other process, which results in lost data.  
	1. Session #1 reads Account A, gets 300.  
	2. Session #2 reads Account A, gets 300.  
	3. Session #2 updates Account A to 400 (+100) and commits.  
	4. Session #1 updates Account A to 350 (+50) and commits.  
- In this scenario, because Session #1 does not know that another session has already modified the account, the update by Session #2 is overwritten ("lost").

### <mark style="background: #BABD00;">Scalability:</mark>

Adoption of distributed systems to  
- accommodate a growing load (e.g. more users)  
- respond faster (this is the hard one)  

Usually done by adding more and/or faster hosts or processors  

Components should not need to be changed when scale of a system increases  

Design components to be scalable! They shouldn’t have to be revisited as things scale up.

### <mark style="background: #BABD00;">Fault Tolerance:</mark>

Hardware, software and networks fail for lots of reasons  

Distributed systems must maintain availability even at low levels of hardware/software/network reliability, which is a huge improvement over centralised systems  

Operations that continue even in the presence of faults are referred to as fault-tolerant  

Fault tolerance is achieved by redundancy (replication)

### <mark style="background: #BABD00;">Transparency:</mark>

Non-functional requirements can be satisfied through the various forms of transparency within distributed systems.  

Application developers and users should perceive distributed systems as  
- One system  
- A collection of co-operating components which should be hidden  
- Efficient and cost-effective to construct and maintain (only possible if the complexity of distribution is hidden from the users)

### <mark style="background: #BABD00;">Dimensions of Transparency:</mark>

Defined in the international standard on Open Distributed Processing (ODP):  
“Distribution transparency is the property of hiding the properties  of distribution from end users”.

Transparency in computing is discussed in terms of hiding complexity from the user.

![](https://i.imgur.com/kanUCML.png)

<mark style="background: #BABD00;">Access Transparency:</mark>
- Enables local and remote components to be accessed using identical operations.  
- Example: File system operations in NFS.  
- Example: Navigation in the Web.  
- Example: SQL Queries  

It is critical in building distributed systems using heterogeneous computer architecture and programming languages.

<mark style="background: #BABD00;">Migration Transparency:</mark>
A component can be relocated without users or clients noticing it (i.e. allows the movement of information objects within a system without affecting the operations of users or application programs)  
- Example: NFS  
- Example: Web Pages

<mark style="background: #BABD00;">Replication Transparency:</mark>
- A replica is a component copy that remains synchronized with its original.  
- Users or application programs have no knowledge of the replica.  
- Example: Distributed DBMS  
- Example: Mirroring Web Pages.

<mark style="background: #BABD00;">Concurrency Transparency:</mark>
- Users and programmers are unaware that components request services concurrently.  
- Enables several processes to operate concurrently using shared information objects without interference between them.  
- Example: NFS  
- Example: Automatic teller machine network  
- Example: Database management system

<mark style="background: #BABD00;">Scalability Transparency:</mark>
- Allows the system and applications to expand in scale without change to the system structure or the application algorithms.  
- Example: World-Wide-Web  
- Example: Distributed Database

<mark style="background: #BABD00;">Performance Transparency:</mark>
- Allows the system to be reconfigured to improve performance as loads vary.  
- Example: Distributed make

<mark style="background: #BABD00;">Failure Transparency:</mark>
- Enables distributed system to conceal faults.  
- Allows users and applications to complete their tasks despite the failure of other components.  
- Depends on concurrency and replication transparency.  
- Example: Database Management System

### <mark style="background: #BABD00;">Transparency Summary:</mark>

<mark style="background: #BABD00;">Transparency</mark> - Perceive distributed systems as One system  

<mark style="background: #BABD00;">Access</mark> - Enables local and remote information objects to be accessed using identical operations  

<mark style="background: #BABD00;">Location</mark> - Enables information objects to be accessed without knowledge of their location  

<mark style="background: #BABD00;">Migration</mark> - A component can be relocated without users or clients noticing it  

<mark style="background: #BABD00;">Replication</mark> - A replica is a component copy that remains synchronized with its original.  

<mark style="background: #BABD00;">Concurrency</mark> - Enables several processes to operate concurrently using shared information objects without interference between them.  

<mark style="background: #BABD00;">Scalability</mark> - Allows the system and applications to expand in scale without change to the system structure or the application algorithms  

<mark style="background: #BABD00;">Performance</mark> - Allows the system to be reconfigured to improve performance as loads vary  

<mark style="background: #BABD00;">Failure</mark> - Enables distributed system to conceal faults.