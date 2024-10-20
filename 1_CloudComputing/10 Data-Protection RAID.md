#CloudComputing 

<mark style="background: #BABD00;">Upon completion of this lesson, you should be able to:</mark>  
- Describe RAID implementation methods  
- Describe the three RAID techniques  
- Describe commonly used RAID levels  
- Describe the impact of RAID on performance  
- Compare RAID levels based on their cost, performance, and protection

<mark style="background: #BABD00;">During this lesson the following topics are covered:</mark>  
- RAID Implementation methods  
- RAID array components  
- RAID techniques

### <mark style="background: #BABD00;">RAID Techniques:</mark>

<mark style="background: #BABD00;">RAID:</mark> It is a technique that combines multiple disk drives into a logical unit (RAID set) and provides protection, performance, or both.

Due to mechanical components in a disk drive it offers limited performance  

An individual drive has a certain life expectancy and is measured in MTBF (Mean Time Between Failures):  
- For example: If the MTBF of a drive is 750,000 hours, and there are 1000 drives in the array, then the MTBF of the array is 750 hours (750,000/1000)  

RAID was introduced to mitigate these problems

### <mark style="background: #BABD00;">RAID Implementation Methods</mark>  

#### <mark style="background: #BABD00;">Software RAID implementation</mark>  

Uses host-based software to provide RAID functionality  

<mark style="background: #BABD00;">Limitations:</mark>  
- Use host CPU cycles to perform RAID calculations, hence impact overall system performance  
- Support limited RAID levels  
- RAID software and OS can be upgraded only if they are compatible  

#### <mark style="background: #BABD00;">Hardware RAID Implementation</mark>  

Uses a specialized hardware controller installed either on a host or on an array

### <mark style="background: #BABD00;">RAID Array Components:</mark>

![](https://i.imgur.com/jppzt5M.png)

### <mark style="background: #BABD00;">RAID Techniques:</mark>

<mark style="background: #BABD00;">Striping:</mark>  Striping is a technique which offers the best performance of any RAID configuration. In a striped array, data is interleaved across all the drives in the array.  

<mark style="background: #BABD00;">Mirroring:</mark>  whatever you write to one drive, gets written simultaneously to another. Thus, you always have an exact duplicate of your data on the  
second drive.  

<mark style="background: #BABD00;">Parity:</mark> RAID controller adds a parity (extra) byte of data tacked onto the actual data being written to the array. Added by the RAID controller to equal either an even or an odd number. By analysing this value, the controller can determine whether the information has been compromised in any way. If it has, it can replace the data automatically with data from the other drive.

### <mark style="background: #BABD00;">RAID Technique – Striping:</mark>

![](https://i.imgur.com/s1Ctt8x.png)

### <mark style="background: #BABD00;">RAID Technique – Mirroring:</mark>

![](https://i.imgur.com/J8yI01A.png)

### <mark style="background: #BABD00;">RAID Technique - Parity:</mark>

![](https://i.imgur.com/WVbET7q.png)

### <mark style="background: #BABD00;">Data Recovery in Parity Technique:</mark>

![](https://i.imgur.com/KylOBLE.png)

### <mark style="background: #BABD00;">Lesson 2 - RAID Levels:</mark>

<mark style="background: #BABD00;">During this lesson the following topics are covered:</mark>  
- Commonly used RAID levels  
- RAID impacts on performance  
- RAID comparison  
- Hot spare

<mark style="background: #BABD00;">Commonly used RAID levels are:</mark>  
- RAID 0 – Striped set with no fault tolerance  
- RAID 1 – Disk mirroring  
- RAID 1 + 0 – Nested RAID  
- RAID 3 – Striped set with parallel access and dedicated parity disk  
- RAID 5 – Striped set with independent disk access and a distributed parity  
- RAID 6 – Striped set with independent disk access and dual distributed parity

### <mark style="background: #BABD00;">RAID 0:</mark>

![](https://i.imgur.com/5L6OURW.png)

<mark style="background: #BABD00;">RAID 0:</mark> non-redundant array of disk drives  

Also called "stripe" mode.  

Operations on the array will be split across the devices e.g. a large write could be split up as 4 kB to disk 0, 4 kB to disk 1, 4 kB to disk 2, then 4 kB to disk 0 again, and so on.  

<mark style="background: #BABD00;">Pro:</mark> parallel writing increase speed nX where n = no. of partitions, x speed on single drive  

<mark style="background: #BABD00;">Con:</mark> No Redundancy, inefficient use of disk space: no savings!  

RAID 0 provides no redundancy, and as such, should never be used for  applications where data is critical.

![](https://i.imgur.com/d6U6m0l.png)

### <mark style="background: #BABD00;">RAID 1:</mark>

![](https://i.imgur.com/1jD4yum.png)

<mark style="background: #BABD00;">RAID-1 (Mirroring):</mark>  
- used on two or more disks.  
- This mode maintains an exact mirror of the information on one disk on the other disk(s).  

<mark style="background: #BABD00;">Pros:</mark> if disk removed (or crashes), all data is still intact  

<mark style="background: #BABD00;">Cons:</mark> Increase of cost proportional to the amount of redundancy.  

Performance may be impacted if copy is done serially.

![](https://i.imgur.com/pRW1DlG.png)

### <mark style="background: #BABD00;">RAID 1 + 0 (RAID 2):</mark>

![](https://i.imgur.com/rDSkUV5.png)

Also called Nested RAID
### <mark style="background: #BABD00;">RAID 3 & 4:</mark>

<mark style="background: #BABD00;">RAID 3:</mark>  
- Similar to RAID 2 which uses byte level striping and a dedicated parity disk  
- BUT RAID 3 uses simple (&fast) XOR algorithm to generate parity.  
- Data is striped (at the byte level) across multiple disks. The parity information is sent to a dedicated parity disk, but the failure of any disk in the array can be tolerated.  
- Pros: delivers good performance and fault tolerance.  
- Cons: dedicated parity disk does slow down write speeds because the parity info has to be written to the parity drive whenever a write occurs  

![](https://i.imgur.com/JlJ8OEY.png)

![](https://i.imgur.com/RAsCHIW.png)

<mark style="background: #BABD00;">RAID 4:</mark>  
- very similar to RAID 3. RAID 4 uses block level striping with parity disk. (Block> Byte)  
- Pros? advantage of block level change the stripe size to suit your application needs.

![](https://i.imgur.com/FCq7YgC.png)

### <mark style="background: #BABD00;">RAID 5:</mark>

Most popular member of the RAID family - combines block level striping with distributed parity for:  
- good performance,  
- fault tolerance  
- storage efficiency.  

<mark style="background: #BABD00;">Distributing parity stripes over a series of hard drives:</mark> 
- Minimizes write bottlenecks of RAID levels 3 and 4  
- Provides relief to the concentration of write activity on a single drive, which in turn enhances overall system performance.  

RAID 5 is often used as an all-purpose RAID solution, but it is also used for database and file server applications.  

RAID 5 requires a minimum of three hard drives, but often costs less to implement than RAID 3 or 4.  

RAID recovery may be necessary if more than one disk fails.

![](https://i.imgur.com/UijDLWM.png)

![](https://i.imgur.com/M9qfCk1.png)

### <mark style="background: #BABD00;">RAID 6:</mark>

![](https://i.imgur.com/bqT87M7.png)

### <mark style="background: #BABD00;">RAID Impacts on Performance:</mark>

![](https://i.imgur.com/EZWrYvI.png)

In RAID 5, every write (update) to a disk manifests as four I/O operations (2 disk reads and 2 disk writes)  

In RAID 6, every write (update) to a disk manifests as six I/O operations (3 disk reads and 3 disk writes)  

In RAID 1, every write manifests as two I/O operations (2 disk writes)

### <mark style="background: #BABD00;">RAID Comparison:</mark>

![](https://i.imgur.com/U2NwEv6.png)

### <mark style="background: #BABD00;">Suitable RAID Levels for Different Applications:</mark>

<mark style="background: #BABD00;">RAID 1+0:</mark>  
- Suitable for applications with small, random, and write intensive (writes typically greater than 30%) I/O profile  
- Example: OLTP, RDBMS – Temp space  

<mark style="background: #BABD00;">RAID 3:</mark>  
- Large, sequential read and write  
- Example: data backup and multimedia streaming  

<mark style="background: #BABD00;">RAID 5 and 6:</mark>  
- Small, random workload (writes typically less than 30%)  
- Example: email, RDBMS – Data entry

### <mark style="background: #BABD00;">Hot Spare:</mark>

![](https://i.imgur.com/8CAgpPA.png)

### <mark style="background: #BABD00;">Summary:</mark>  

<mark style="background: #BABD00;">Key points covered in this module:</mark>  
- RAID implementation methods and techniques  
- Common RAID levels  
- RAID write penalty  
- Compare RAID levels based on their cost and performance