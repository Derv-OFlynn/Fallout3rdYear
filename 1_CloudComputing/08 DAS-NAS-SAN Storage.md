### <mark style="background: #BABD00;">Storage Basics:</mark>  

Information (data) is constantly flowing in and out of computers.  

Data coming in is either stored in memory for quick access (non-permanent storage) or written to disk so that it can be retrieved later.  

How this information is stored depends on several issues:  
- How will it be stored (what will it be stored ON)?  
- What is the protocol by which this data will be transferred?  
- What devices will it pass through on the way to being stored?

### <mark style="background: #BABD00;">Data Storage Types:</mark> 

Single disk drive (self explanatory)  

<mark style="background: #BABD00;">Volume:</mark> a “logical” disk drive. A concatenation of drives. When one fills up, it goes to the next one. No RAID, no striping. To the OS, a logical volume looks like one disk drive.  

<mark style="background: #BABD00;">Storage Array:</mark>Also a group of more than one disk joined together – but can do striping and/or redundancy. Implies some type of RAID  

<mark style="background: #BABD00;">SCSI:</mark> SCSI stands for Small Computer System Interface. It is a means of attaching additional storage to a computer. For example, a typical RAID Controller is a SCSI device that allows connection to an external storage enclosure with multiple drives.  

<mark style="background: #BABD00;">NAS:</mark> Network Attached Storage. Rather than simply attaching storage to one machine, it is attached to the computer network. Multiple machines can now access the storage. A file protocol must be used to communicate across the network.

<mark style="background: #BABD00;">ISCSI:</mark> Internet/SCSI protocol. Another approach to offering storage on a network. Rather then using file protocols to communicate across a TCP/IP network, native SCSI commands are “encapsulated” in TCP/IP packets.  

<mark style="background: #BABD00;">SAN:</mark> Storage Area Network. Whereas a NAS is storage that is attached to a network, SAN is a storage network in and of itself that can be attached to multiple machines.  
- SAN is an industry-wide term for both the storage and the switching network. A SAN does not have the protocol conversion overhead of NAS or ISCSI, and tends to offer better performance. A SAN may require a higher initial investment in infrastructure.  
- Devices appear as locally attached to the operating system.

### <mark style="background: #BABD00;">Network Storage:</mark>

Many forms of storage networking - Why?  

New technologies emerge and evolve but legacy systems remain – investment, familiarity, training?  

No single storage networking approach solves all problems or optimises all variables.  

There are trade-offs in cost, ease-of management, performance, distance and maturity  

Multiple storage network alternatives will coexist (often within the same organisation!)

### <mark style="background: #BABD00;">Hard Drives:</mark>

The Hard Drive - basic storage element  

Made of complex devices composed of platters, heads, cylinders and tracks  

Logical Block Addressing (LBA) addresses the sector within the disk. Modern drives have 4 kilo-byte sectors  
File systems arrange files into sectors so that they can be stored and retrieved  

The File system usually deals with clusters of blocks and uses a File Allocation Table to map a file to the sectors.

### <mark style="background: #BABD00;">Direct Attached Storage (Internal):</mark>

![](https://i.imgur.com/QJiOFVY.png)

Traditional internal data storage

# <mark style="background: #FF5582A6;">SLIDE 8</mark>

