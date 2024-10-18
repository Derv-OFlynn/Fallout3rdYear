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

![](https://i.imgur.com/Em4RKzr.png)

### <mark style="background: #BABD00;">DAS w/ internal controller and external storage:</mark>

![](https://i.imgur.com/OhJimG2.png)

Direct Attached Storage -RAID controller is internal to the computer system, and the disk drives are attached to the controller via a single path

### <mark style="background: #BABD00;">DAS ext. controller & ext. storage:</mark>

![](https://i.imgur.com/yndLZVx.png)

![](https://i.imgur.com/JV0aDmz.png)

### <mark style="background: #BABD00;">I/O Transfer:</mark>

<mark style="background: #BABD00;">RAID Controller:</mark>  
-  Contains the “smarts”  
- Determines how the data will be written (striping, mirroring, RAID 10, RAID 5, etc.)  

<mark style="background: #BABD00;">Host Bus Adapter (HBA):</mark>  
- Simply transfers the data to the RAID controller.  
- Does not do any RAID or striping calculations. Speed!  
- Required for external storage.

### <mark style="background: #BABD00;">The Old Storage Environment:</mark>

Direct Attached Storage (DAS)  

Storage is captive ‘behind’ the server  

Server CPU must handle user I/O requests, but also:  
- User-database inquiries  
- User file/print serving  
- Data-integrity checking  
- Communication with other devices  

Data access is file system and platform dependant  

Costly to scale; complex to manage

![](https://i.imgur.com/Utvgob9.png)

### <mark style="background: #BABD00;">NAS: What is it?</mark>

<mark style="background: #BABD00;">NAS:</mark> Network Attached Storage  

Designed to provide shared access to storage across a standard TCP/IP network  

Sharing data across TCP/IP by converting block-level SCSI commands to file sharing protocols  

‘sharing protocols’ ? (Common file sharing protocols):  
- UNIX Network File System (NFS) was developed originally for sharing files between UNIX systems across a LAN.  
- Support expanded to include non-UNIX systems;  
- (but most NFS clients today are computers running some flavour of UNIX/Linux.)  

Windows Common Internet File System (CIFS) created by Microsoft, formerly known as Server Message Block (SMB), developed by IBM in DOS.

### <mark style="background: #BABD00;">NAS I/O Requests:</mark>
  
File I/O is a higher-level type of request that, in essence, specifies the file to be accessed, an offset into the file (as if the file was a set of contiguous bytes), and a number of bytes to read or write beginning at that offset.  

Unlike block I/O, there is no awareness of a disk volume or disk sectors in a file I/O request.  

Inside the NAS product (“appliance”), an operating system or OS kernel tracks where files are located on disk and issues a block I/O request to the disks to fulfil the file I/O read and write requests it receives.

### <mark style="background: #BABD00;">Network Storage Possibilities:</mark>

For small businesses, the solution for managing storage  
intelligently is consolidation.  

Rather than dispersing data across several PCs, laptops or small servers, consolidating storage into one or two locations makes it much easier to grow, manage and protect.  

When storage is freed from the constraints of individual PCs and file servers, it can be put on the network as a separate, single resource that can be allocated to applications as necessary.

### <mark style="background: #BABD00;">NAS:</mark>

Storage “Appliances” utilise a stripped-down OS that optimises file protocol performance  

Instead of starting with a general-purpose computer and  
configuring or removing features from that base, NAS designs begin with the bare-bones components necessary to support file transfers and add features “from the bottom up.”  

Clients generally access a NAS over an ethernet connection. The NAS appears on the network as a single "node" that is the IP address of the head device.

### <mark style="background: #BABD00;">SAN - Storage Area Network:</mark>

SANs are networked infrastructures designed to provide a flexible, high-performance, and highly scalable storage environment.  

High-performance Fibre Channel switches and Fibre Channel network protocols ensure that device connections are both reliable and efficient.

![](https://i.imgur.com/qLvCf9O.png)

![](https://i.imgur.com/pjgA2ZE.png)

A Storage Area Network (SAN) is a specialized, high-speed network that provides network access to storage devices.  

SANs are typically composed of hosts, switches, storage elements, and storage devices that are interconnected using a variety of technologies, topologies, and protocols.  
SANs may span multiple sites..

[SAN explanation](https://www.snia.org/education/storage_networking_primer/san/what_san "https://www.snia.org/education/storage_networking_primer/san/what_san")

### <mark style="background: #BABD00;">SAN - Benefits:</mark>

<mark style="background: #BABD00;">Access:</mark>  
- longer distance between processors and storage, higher availability, improved performance (because I/O traffic is offloaded from a LAN to a dedicated network, and because Fibre Channel is generally faster than most LAN media).  
- larger number of processors can be connected to the same storage device compared to typical built-in  device attachment facilities.

<mark style="background: #BABD00;">Consolidation:</mark> 
- Replacement of multiple independent storage devices by fewer devices that support capacity sharing —disk and tape pooling.  
- SANs provide the ultimate in scalability - software can allow multiple SAN devices to appear as a single pool of storage accessible to all processors on the SAN.  
- Storage on a SAN can be managed from a single point of control. Controls over which hosts can see which storage (called zoning and LUN masking) can be implemented.

<mark style="background: #BABD00;">Protection:</mark>  
- LAN-free backups occur over the SAN rather than the (slower) LAN, and server-free backups can let disk storage “write itself” directly to tape without processor overhead.  

<mark style="background: #BABD00;">Data Sharing:</mark>  
- sharing data, as noted earlier, offers benefits such as reducing the number of copies of files, increasing accessibility to current data and reducing the need to transfer copies of data between servers over the network.

### <mark style="background: #BABD00;">SAN - Different Technologies:</mark>

Multiple technologies can be used when building a SAN  

Traditionally the dominant technology is Fiber Channel, but IP based solutions are also quite popular for specific applications (due to costs!)  
  
The concept of SAN is also independent from the devices that are attached to it.  
- Can be disks, tapes, RAIDs, file servers, or other!  
- Yes, Magnetic Tape storage is still used in 2024: Often cheaper than alternative, can last 30 years or more (if kept clean, dry and protected) which is excellent for compliance with industry-specific storage regulations.

### <mark style="background: #BABD00;">Storage Systems Architecture:</mark>

![](https://i.imgur.com/l70GUI3.png)

### <mark style="background: #BABD00;">NAS vs SAN Similarities and differences:</mark>

![](https://i.imgur.com/9QNOQ9O.png)

Note the relative position of the File system in each case.

![](https://i.imgur.com/PIiYH61.png)

### <mark style="background: #BABD00;">NAS with HTTPS:</mark>

Many NAS systems also support Hypertext Transfer Protocol (HTTPS).  

Clients can often download files in their Web browser from a NAS that supports HTTPS.  

NAS systems also commonly employ HTTPS as an access protocol for Web-based administrative user interfaces.

### <mark style="background: #BABD00;">NAS vs. SAN:</mark>

<mark style="background: #BABD00;">NAS</mark> is optimised for ease-of-management and file sharing using lower-cost Ethernet-based networks.  

Installation is relatively quick, and storage capacity is automatically assigned to users on demand.  

<mark style="background: #BABD00;">SAN</mark> is optimised for performance and scalability.  
- Major potential benefits include support for high-speed Fibre Channel media which is optimised for storage traffic, managing multiple disk and tape devices as a shared pool with a single point of control, specialised backup facilities that can reduce server and LAN utilization and wide industry support.  
- Cost savings can be obtained over TCP/IP using iSCSI (later).

### <mark style="background: #BABD00;">NAS Costs?</mark>

NAS will generally cost more than DAS (because of its built-in file sharing intelligence), but has the following potential advantages:  
- distance (because it is attached over a network), large number of users being able to access the same storage device  
- capacity pooling within the NAS appliance (sharing capacity among all hosts using the NAS)  
- file sharing (as opposed to data transfer or multiple copies on distributed hosts).

### <mark style="background: #BABD00;">Summary:</mark>

![](https://i.imgur.com/EMKCax4.png)
