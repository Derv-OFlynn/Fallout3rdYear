# <mark style="background: #BABD00;">02 Intro to Cloud Computing</mark>


### <mark style="background: #BABD00;">What is Cloud Computing?</mark>

<mark style="background: #BABD00;">A customer-oriented definition:</mark>
- Anytime
- Anywhere
- Any device
- Any service

<mark style="background: #BABD00;">A business-oriented definition:</mark>
- Universal access
- Scalable services
- Collaborative
- New revenue models

<mark style="background: #BABD00;">A developer-oriented definition:</mark>
- Distributed Computing
- Scalable
- Access to 3rd party functionality
- Mobility

### <mark style="background: #BABD00;">SaaS (ready to use):</mark>

- Most basic form of cloud computing
- No dev necessary for user
- No resources required form the user
- Software managed from a central location
- Software delivered in a “one to many” model
- Users not required to handle software upgrades and patches  
- Application Programming Interfaces (APIs) allow for integration between different pieces of software  
- Offer powerful tools right at web browser  
- Requires no installation  
- Requires no specific knowledge of user

### <mark style="background: #BABD00;">SaaS examples:</mark>

<mark style="background: #BABD00;">Google Docs:</mark>  
- Productivity suite  
- Free to use (free Google Account required)  
- Share documents with others  
- Try it: docs.google.com

<mark style="background: #BABD00;">Dropbox:</mark>  
- Online file storage  
- Automatic synchronization across computers  
- Sharing of files with other users  
- Web access + mobile access  
- Backup of data + restore (30 days)

Salesforce (CRM)  
- Sales cloud – automation of workflow  
- Service cloud – customer service  
- Chatter – collaboration tools  
- Jigsaw – customer contact database  
- Force.com – Salesforce platform for third party apps (PaaS)  
- Heroku – third party ruby apps (PaaS)
### <mark style="background: #BABD00;">Platform as a Service (PaaS):</mark>

- "Provides developers with a proprietary APIs to make an application that will run in a specific environment"
- Can be any application you can think of  
- Is locked to the platform used for creation
- Examples: metaverse apps, PHP, Java, Python, C#

<mark style="background: #BABD00;">Benefits of PaaS?</mark>
- Many services free to use
- Pay per use - good for users, not the best for providers
- Vendor lock-in difficult due to lack of standards. Containers can combat vendor lock-in.
- Why are companies offering PaaS environments?

- Key Benefit: DATA. "We're (IT companies) not Google's customers; we're Google's product that they sell to their customers" - Bruce Schneier

<mark style="background: #BABD00;">Linking? Infrastructure as a Service:</mark>
- Real business innovation behind SaaS and PaaS is gathering data
- Most important asset cloud computing can provide is processing data
- Solution to processing vast amounts of data quickly can be found in IaaS

Infrastructure for:
- Developing
- Running
- Storing
. . . applications and data in cloud environments.

### <mark style="background: #BABD00;">IaaS:</mark>
- provides virtually limitless storage  
- provides virtually limitless computing power  
- potentially negates the need of having physical hardware at hand for doing so  
- provides numerous Linux, Unix and Windows environments to work in  
- provides variety of tools, services, SDKs and the like running on those OSs  
- Usually requires specific knowledge to use APIs for creating and managing the virtual OSs in the cloud infrastructure  
- therefore usually not user-friendly and simple to use

<mark style="background: #BABD00;">IaaS provider examples:</mark>
- AWS
- IBM Cloud
- DigitalOcean
- Microsoft Azure
- Linode
- Cloudera

### <mark style="background: #BABD00;">"Cloud Computing" Model Abstraction:</mark>

![](https://i.imgur.com/QMURBci.png)

<mark style="background: #BABD00;">Efficiency vs. Effectiveness:</mark> Efficient systems do not make wasteful use of system resources. Effectiveness is more focused on impact.

<mark style="background: #BABD00;">Cloud Repatriation:</mark> Moving from the cloud back to local data centre.

### <mark style="background: #BABD00;">How do we do cloud development?</mark>

The development process remains the same...

![](https://i.imgur.com/VAtSsxu.png)

But where we do these tasks may change..

![](https://i.imgur.com/73PMiUx.png)

<mark style="background: #BABD00;">Deployment</mark> happens in the cloud.

The major players are:
1. Amazon 
2. Microsoft Azure
3. Google

Each has their own set of tools on offer.

![](https://i.imgur.com/R7dJhAb.png)

<mark style="background: #BABD00;">Downsides:</mark>
- Security
- Lock-in
- Reliability
- Lack of control

<mark style="background: #BABD00;">Upsides:</mark>
- Scale and cost
- Encapsulated change management
- Next-generation architectures
- Choice and agility

# <mark style="background: #BABD00;">03 History of Distributed Computing</mark>

### <mark style="background: #BABD00;">Evolution of Distributed Systems:</mark>

![](https://i.imgur.com/pqVCEWy.png)

<mark style="background: #BABD00;">Monolithic Systems (Single Tier):</mark>
- Central processing (mainframe)  
- Multiple access supported by time sharing Operating Systems  
- Primitive User Interface

<mark style="background: #BABD00;">Client/Server Database Systems (Two-Tier):</mark>
- Centralised DBMS, often running on a Unix system
- Windows clients connect over a LAN.  
- Service Logic resides on a client, for example, calculation of pay after overtime rates etc..  
- Manual Installation of clients

<mark style="background: #BABD00;">Multi-Tier Systems:</mark>
- Database server on one host  
- Web server and Application server on another host  (connected by a LAN)  
- (Thin) Clients downloaded as applets. Communicates with the application server.  

![](https://i.imgur.com/oggBGaO.png)

![](https://i.imgur.com/6vQlM4C.png)

### <mark style="background: #BABD00;">Sample N-Tier (Twitter):</mark>

![](https://i.imgur.com/YuHX7i1.png)

### <mark style="background: #BABD00;">Centralised System Characteristics:</mark>

- One component with non-autonomous parts  
- Component shared by users all the time  
- All resources accessible  
- Software runs in a single process  
- Single Point of control  
- Single Point of failure

### <mark style="background: #BABD00;">Distributed System Characteristics:</mark>  

- Multiple autonomous components  
- Components are not shared by all users  
- Resources may not be accessible  
- Software runs in concurrent processes on different processors  
- Multiple Points of control  
- Multiple Points of failure

### <mark style="background: #BABD00;">Examples of Distributed Systems:</mark>

#### <mark style="background: #BABD00;">The Internet </mark> 

Heterogeneous network of computers and applications  

Implemented through the Internet Protocol Stack  

Typical configuration:
![](https://i.imgur.com/Set6LBr.png)

#### <mark style="background: #BABD00;">Distributed Multimedia- Systems</mark>  

Often use Internet infrastructure  

<mark style="background: #BABD00;">Characteristics:</mark>  
- Heterogeneous data sources that need to be synchronized in real time:  
	- Video  
	- Audio  
	- Text  
	
- Often: Distribution services  
	- Multicast  

<mark style="background: #BABD00;">Examples:</mark>  
- Tele-teaching tools  
- Video- conferencing  
- Video and audio on demand

#### <mark style="background: #BABD00;">Intranets:</mark>  
- Locally administered network  
- Usually proprietary (e. g., the University campus network)  
- Interfaces with the Internet  
- Firewalls  
- Provides services internally and externally

![](https://i.imgur.com/s5qlO5f.png)

### <mark style="background: #BABD00;">Mobile and Ubiquitous Computing Systems:</mark>

<mark style="background: #BABD00;">Cellular phone systems (e. g., GSM, UMTS):</mark>  
- Resources being shared  
	- Radio frequencies  
	- Transmission times on one frequency (UMTS: multiplexing)  
	- The mobile on the move  

<mark style="background: #BABD00;">Laptop computers:</mark>  
- Wireless LANs  
- Handheld devices (PDAs etc. – Bluetooth networks)

<mark style="background: #BABD00;">Wearable devices</mark>

![](https://i.imgur.com/v6XKXQg.png)

### <mark style="background: #BABD00;">Embedded systems:</mark>  

<mark style="background: #BABD00;">Avionics control systems</mark>  - Flight management systems in aircraft  

<mark style="background: #BABD00;">Automotive control systems</mark> - Mercedes S- Class cars are equipped with 50+ autonomous embedded processors  

<mark style="background: #BABD00;">Connected through proprietary bus</mark> - like LANs  

<mark style="background: #BABD00;">Consumer Electronics</mark> - Audio HiFi equipment  

<mark style="background: #BABD00;">Medical Devices</mark> - Pace Makers

<mark style="background: #BABD00;">Tele Surgery</mark> - "Lindbergh Operation"


### <mark style="background: #BABD00;">Additional Notes:</mark>

<mark style="background: #BABD00;">GSM</mark> - (Global System for Mobile Communications, originally Groupe SpécialMobile), is a standard developed by the European Telecommunications Standards Institute (ETSI) to describe the protocols  for second-generation (2G) digital cellular networks used by mobile phones, first deployed in Finland in July 1991.[2] As of 2014 it has become the de facto global standard for mobile communications - with over 90% market share, operating in over 219 countries and territories.[3]  

<mark style="background: #BABD00;">UMTS</mark> - The Universal Mobile Telecommunications System (UMTS) is a third generation mobile  
cellular system for networks based on the GSM standard.  

<mark style="background: #BABD00;">Multiplexing</mark> (sometimes contracted to muxing) is a method by which multiple analogue or digital signals are combined into one signal over a shared medium. The aim is to share an expensive resource.  

<mark style="background: #BABD00;">The Lindbergh Operation</mark> was a complete tele-surgical operation carried out by a team of French  
surgeons located in New York on a patient in Strasbourg, France (over a distance of several thousand miles) using telecommunications solutions based on high-speed services and sophisticated surgical robotics. The operation was performed successfully on September 7, 2001 by Professor Jacques Marescaux and his team from the IRCAD (Institute for Research into Cancer of the Digestive System). This was the first time in medical history that a technical solution proved capable of reducing the time delay inherent to long distance transmissions sufficiently to make this type of procedure possible. The name was derived from that of American aviator Charles Lindbergh, because he was the first person to fly solo across the Atlantic

# <mark style="background: #BABD00;">04 Requirements of Distributed Computing</mark>

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


# <mark style="background: #BABD00;">05 Load Balancing</mark>

### <mark style="background: #BABD00;">Load Balancing:</mark>

All inbound traffic to a web role passes through a stateless load balancer, which distributes client requests among the role instances.  

Individual role instances do not have public IP addresses, and are not directly addressable from the Internet. (This is why you can’t ‘Ping’ the IP addresses).  

Web roles are stateless, so that any client request can be routed to any role instance.  

A Status-check event is raised every 15 seconds. This can be used to indicate if the role is ready to receive traffic, or is busy and should be taken out of the load balancer rotation.

![](https://i.imgur.com/heN0psc.png)

### <mark style="background: #BABD00;">Elasticity:</mark>

<mark style="background: #BABD00;">Elasticity – What is it?</mark> 
The degree to which a system is able to adapt to workload changes by provisioning and deprovisioning resources in an automated manner, such that at each point in time the available resources match the current demand as closely as possible.  

<mark style="background: #BABD00;">Elasticity is automated scalability.</mark>  
Scalability provides the ability to increase (or decrease) the amount of resources in scaling up (more powerful instances) or out (additional instances), which is usually done through manual intervention.  

Elasticity does the same but in an automated manner, independent from human interaction.

### <mark style="background: #BABD00;">Types of Auto Scaling:</mark>

![](https://i.imgur.com/q4Kkywn.png)

### <mark style="background: #BABD00;">Vertical Auto Scaling:</mark>  

Often referred to as scaling-up or scaling down.  

Requires that you modify the hardware (expand or reduce its capacity and performance).  

Or redeploy the solution using alternative hardware that has the appropriate capacity and performance.  
Vertical scaling is often a disruptive process that requires making the system temporarily unavailable while it is being redeployed .  

<mark style="background: #BABD00;">Not a common approach in the Cloud Industry!</mark>

### <mark style="background: #BABD00;">Horizontal Auto Scaling:</mark>  

Often referred to as scaling-in or scaling-out.  

Requires deploying the solution on additional or fewer resources, which are typically commodity resources rather than high-powered systems.  

The solution can continue running without interruption while these resources are provisioned.  

When the provisioning process is complete, copies of the elements that comprise the solution can be deployed on these additional resources and made available.  

If demand drops, the additional resources can be reclaimed after the elements using them have been shut down cleanly.  

<mark style="background: #BABD00;">The most common approach to implementing Elasticity in the Cloud.</mark>

### <mark style="background: #BABD00;">AWS Auto Scaling:</mark>

![](https://i.imgur.com/FegnUtZ.png)

# <mark style="background: #BABD00;">06 Virtualisation:</mark>

<mark style="background: #BABD00;">Virtualisation:</mark> The separation of a resource or request for a service from the underlying physical delivery of that service.

### <mark style="background: #BABD00;">Buffering:</mark>

When the speed in which data is received and the speed in which data is processed are different, then we use a buffer.

Buffer is a memory space which stores the input data as it is received and passes it on to the system according to the speed it can process.

![](https://i.imgur.com/KpI5ScA.png)

<mark style="background: #BABD00;">Example:</mark>
- Video or audio streaming  
- When you download an audio or video file from the Internet, it may load the first 10% of it into a buffer and then begin to play. While the clip plays back, the computer continually downloads the  rest of the clip and stores it in the buffer. Because the clip is being played from the buffer, not  directly from the Internet, there is less of a chance that the audio or video will stall or skip when there is network congestion.  
- There are buffers for screens, printers, keyboards,  network connections, etc

### <mark style="background: #BABD00;">Caching:</mark>

Caching is a high-speed storage in a separate disk or in dedicated memory which stores a subset of data.  

Future requests for that data are served up much faster than is possible by accessing the data’s original storage location.  

Thus, a Cache is used in a system to speed up the access to frequently used data.  

Caching allows you to efficiently reuse previously retrieved or computed data.

<mark style="background: #BABD00;">Local Caching:</mark>
![](https://i.imgur.com/lZNtf1P.png)

<mark style="background: #BABD00;">Distributed Caching:</mark>
![](https://i.imgur.com/Ps32x8y.png)

<mark style="background: #BABD00;">Distributed Caching Examples:</mark>

<mark style="background: #BABD00;">Redis:</mark> an open source, in-memory data store used by millions of developers as a database, cache, streaming engine, and message broker  
- https://redis.io/ (source-available from March 2024)  
- https://valkey.io/ (open-source alternative to redis)  

<mark style="background: #BABD00;">Memcached:</mark> open source, high-performance, distributed memory object caching system, generic in nature, but intended for use in speeding up dynamic web applications by alleviating database load.  
https://memcached.org/

### <mark style="background: #BABD00;">Difference between buffering and caching:</mark>

![](https://i.imgur.com/rc5MA7S.png)

### <mark style="background: #BABD00;">Virtual Memory:</mark>

The computer software gains access to more memory than is physically installed, via the background swapping of data to disk storage.

![](https://i.imgur.com/EaMNdYo.png)

### <mark style="background: #BABD00;">Virtual Machine:</mark>

Typically a single Operating System runs on a computer at any one time  
- Single OS installed or  
- Dual Boot where you choose the OS to load  

A virtual machine (VM) is a "completely isolated guest operating system installation within a normal host operating system“.  

The underlying Operating System is unaware of the virtual environment and runs as though it is in control of the computer  

An underlying Operating System is required to manage Virtual Machines  

Virtual Machines allow Operating Systems run on wide range of hardware not originally supported  
- Windows running on Sun/Oracle hardware  
- Windows running on Apple Operating System  
- Linux running on Windows Operating System

In a Virtual Machine - each process "seems" to execute on its own processor with its own memory and devices.  
- The resources of the physical machine are shared. Virtual devices are sliced out of the physical ones. Virtual disks are subsets of physical ones.  
- Useful for running different OS simultaneously on the same machine.  
- Protection is paramount

![](https://i.imgur.com/158ainT.png)

![](https://i.imgur.com/vqfDyjV.png)


<mark style="background: #BABD00;">Example: Java Virtual Machine (JVM)</mark>  

The Java Virtual Machine allows Java code to be portable between various hardware and OS platforms.

![](https://i.imgur.com/ih1sTTz.png)

### <mark style="background: #BABD00;">Virtualisation Extended:</mark>

<mark style="background: #BABD00;">Desktop virtualisation</mark> is a technology which enables detachment of the user state, the Operating System (OS), and the applications from endpoint devices.

Enables organizations to host and centrally manage desktops. Desktops run as virtual machines within the data centre and accessed over a network  

<mark style="background: #BABD00;">Desktop virtualization benefits:</mark>  
- Flexibility of access due to enablement of thin clients  
- Improved data security  
- Simplified data backup and PC maintenance

![](https://i.imgur.com/wCCm6Ov.png)

### <mark style="background: #BABD00;">Virtualisation Extended:</mark>

Virtualisation techniques can be applied to other IT infrastructure layers - including networks, storage, laptop or server hardware, operating systems and applications.  

This blend of virtualisation technologies - or <mark style="background: #BABD00;">virtual infrastructure</mark> - provides a layer of abstraction between computing, storage and networking hardware, and the applications running on it

![](https://i.imgur.com/Vo4SqTc.png)

### <mark style="background: #BABD00;">VM Hardware Components:</mark>

![](https://i.imgur.com/yFpkZVS.png)

### <mark style="background: #BABD00;">Network visualisation:</mark>

![](https://i.imgur.com/v73HTjX.png)

Server virtualisation runs multiple virtual servers on a physical server

Network virtualisation runs multiple virtual networks on a physical network.

### <mark style="background: #BABD00;">Virtualised Infrastructure:</mark>

Using virtual infrastructure solutions enterprise IT managers can address challenges that include:  
- <mark style="background: #BABD00;">Server Consolidation and Containment</mark> – Eliminating ‘server sprawl’ via deployment of systems as virtual machines (VMs) that can run safely and move transparently across shared hardware, and increase server utilisation rates from 5-15% to 60-80%.  
- <mark style="background: #BABD00;">Test and Development Optimisation</mark> – Rapidly provisioning test and development servers by reusing pre-configured systems, enhancing developer collaboration and standardizing development environments.  
- <mark style="background: #BABD00;">Business Continuity</mark> – Reducing the cost and complexity of business continuity (high availability and disaster recovery solutions) by encapsulating entire systems into single files that can be replicated and restored on any target server, thus minimizing downtime.  
- <mark style="background: #BABD00;">Enterprise Desktop</mark> – Securing unmanaged PCs, workstations and laptops without compromising end user autonomy by layering a security policy in software around desktop virtual machines.

### <mark style="background: #BABD00;">What is a Hypervisor?</mark>

Virtualisation is the addition of a software layer (the <mark style="background: #BABD00;">virtual machine monitor</mark> VMM, also known as <mark style="background: #BABD00;">hypervisor</mark>) between the hardware and the existing software that exports an interface at the same level as the underlying hardware.

![](https://i.imgur.com/ZWIP5Uq.png)

Has two components:  
- Kernel  
- Virtual Machine Monitor (VMM)

![](https://i.imgur.com/K4EM52B.png)

### <mark style="background: #BABD00;">Types of Hypervisor (VMM):</mark>

![](https://i.imgur.com/J66toHT.png)

<mark style="background: #BABD00;">Type 1 (or native, bare metal)</mark>  
- Run directly on the host's hardware to control the hardware and to monitor guest operating systems. A guest operating system thus runs on another level above the hypervisor. (Hyper-V, VMWare ESXi Server , Xen etc)  
- Typically the preferred approach because they can achieve higher virtualisation efficiency by dealing directly with the hardware.  
- Type 1 hypervisors provide higher performance efficiency, availability, and security than type 2 hypervisors.  

<mark style="background: #BABD00;">Type 2:</mark>  
- hypervisors run on a host operating system that provides virtualisation services, such as I/O device support and memory management.  
- Used on client systems where efficiency is less critical & support for a broad range of I/O devices is important and can be provided by the host operating system.  
- e.g. Oracle VirtualBox, VMware Server and Microsoft Virtual PC

### <mark style="background: #BABD00;">The Hypervisor:</mark>

![](https://i.imgur.com/rEHtfCm.png)

### <mark style="background: #BABD00;">VM Players:</mark>
  
<mark style="background: #BABD00;">VMWare</mark> is perhaps one of the most well-known virtualisation software makers in the market. VMWare also offers virtual appliances, which are virtual machines for download, sometimes for free. VMWare products are generally compatible with the Windows and Linux platforms. There is also a version that runs on Mac OS X.  

Xen is a lightweight open-source hypervisor which runs on Intel (Nasdaq: INTC) or AMD (NYSE: AMD) x86 and 64-bit processors, with or without virtualisation technologies.  

Microsoft (Nasdaq: MSFT) Virtual Server and Virtual PC are relatively new entrants into this software space. If you run only Windows desktops and servers, you may not need to look any further for virtualisation software.  

Parallels is one of the most widely used options for Mac computers. It was among the first to create commercial virtualisation products that could run non-Apple OSes on Mac hosts. Parallels also runs on Windows and Linux hosts.  

Other free or open-source choices include Qemu.

### <mark style="background: #BABD00;">Virtualisation in the cloud:</mark>

Where everything can be provided as a service.

![](https://i.imgur.com/mspKkg4.png)

### <mark style="background: #BABD00;">Responsibility:</mark>

Local clouds give you the power of cloud computing in your own IT infrastructure.  

Get the benefits of cloud computing behind the security of your own firewall.  

Deploy workloads and have them running immediately.  

Grow or shrink computing capacity to meet your application's needs.  

Get the most out of your existing infrastructure.

![](https://i.imgur.com/w2JqNeV.png)

### <mark style="background: #BABD00;">The main players:</mark>

![](https://i.imgur.com/vk6fgNJ.png)

# <mark style="background: #BABD00;">07 The Virtualised Data Centre</mark>

Transforming a <mark style="background: #BABD00;">Classic Data Centre (CDC)</mark> into a <mark style="background: #BABD00;">Virtualised Data Centre (VDC)</mark> requires virtualising the core elements of the data centre.

Using a phased approach to a virtualized infrastructure enables smoother transition to virtualize core elements.

![](https://i.imgur.com/SWp1MUx.png)

### <mark style="background: #BABD00;">Compute Virtualisation:</mark>

<mark style="background: #BABD00;">Compute Virtualisation:</mark> It is a technique of masking or abstracting the physical compute hardware and enabling multiple operating systems (OSs) to run concurrently on a single or clustered physical machine(s).

Enables creation of multiple virtual machines (VMs), each running an OS and application  
- VM is a logical entity that looks and behaves like physical machine  
- Virtualisation layer resides between hardware and VMs -> Also known as hypervisor  
- VMs are provided with standardized hardware resources

![](https://i.imgur.com/lL4unw0.png)

<mark style="background: #BABD00;">Benefits of Compute Virtualisation:</mark>
- Server consolidation  
- Isolation  
- Encapsulation  
- Hardware independence  
- Reduced cost

### <mark style="background: #BABD00;">Resource Management:</mark>

<mark style="background: #BABD00;">Resource management:</mark> A process of allocating resources from physical machine or clustered physical machines to virtual machines (VMs) to optimize the utilization of resources.

<mark style="background: #BABD00;">Goals of resource management:</mark>  
- Controls utilization of resources  
- Prevents VMs from monopolizing resources  
- Allocates resources based on relative priority of VMs  

Resources must be pooled to manage them centrally

### <mark style="background: #BABD00;">Resource Pool:</mark>

<mark style="background: #BABD00;">Resource Pool:</mark> It is a logical abstraction of aggregated physical resources that are managed  
centrally.

Created from a physical machine or cluster  

Administrators may create child resource pool or virtual machine (VM) from the parent resource pool  

Reservation, limit, and share are used to control the resources consumed by resource pools or VMs.

### <mark style="background: #BABD00;">Resource Pool Example:</mark>

![](https://i.imgur.com/8WZPkl5.png)

### <mark style="background: #BABD00;">Share, Limit and Reservation:</mark>

Parameters that control the resources consumed by a child resource pool or a virtual machine (VM) are as follows:  
- <mark style="background: #BABD00;">Reservation:</mark> Amount of CPU and memory reserved for a VM or a child resource pool 
- <mark style="background: #BABD00;">Limit:</mark> Maximum amount of CPU and memory a VM or a child resource pool can consume  
- <mark style="background: #BABD00;">Share:</mark> Amount of CPU or memory resources a VM or a child resource pool can have with respect to its parent’s total resources

### <mark style="background: #BABD00;">Optimising CPU Resources:</mark>

Modern CPUs are equipped with multiple cores and hyper-threading:
- Multi-core processors have multiple processing units (cores) in a single CPU  
- Hyper-threading makes a physical CPU appear as two or more logical CPUs  

Allocating a CPU resource efficiently and fairly is critical  

Hypervisor schedules virtual CPUs on the physical CPUs  

Hypervisors support multi-core, hyper-threading, and CPU load-balancing features to optimize CPU resources

### <mark style="background: #BABD00;">Multi-core Processors:</mark>

![](https://i.imgur.com/3Hw6zIw.png)

### <mark style="background: #BABD00;">Resource Management Tool:</mark>

Provides ability to manage physical machines running hypervisor  

Enables centralized management of resources from a management server  

Enables pooling of resources and allocates capacity to VMs: Communicates with hypervisors to perform management  

Provides operational automation

![](https://i.imgur.com/lTyR9Kk.png)

### <mark style="background: #BABD00;">Storage Virtualisation:</mark>

<mark style="background: #BABD00;">Storage virtualization:</mark> It is the process of masking the underlying complexity of physical storage resources and presenting the logical view of these resources to compute systems.

Logical to physical storage mapping is performed by virtualization layer.  

Virtualization layer abstracts the identity of physical storage devices: Creates a storage pool from multiple, heterogeneous storage arrays.  

Virtual volumes are created from the storage pools and are assigned to the compute system.

<mark style="background: #BABD00;">Benefits of storage virtualisation:</mark>
- Adds or removes storage without any downtime  
- Increases storage utilization thereby reducing TCO  
- Provides non-disruptive data migration between storage devices  
- Supports heterogeneous, multi-vendor storage platforms  
- Simplifies storage management

### <mark style="background: #BABD00;">Storage for virtual machines:</mark>

VMs are stored as set of files on storage space available to hypervisor  

‘Virtual disk file’ represents a virtual disk used by a VM to store its data  

Size of virtual disk file represents storage space allocated to virtual disk  

<mark style="background: #BABD00;">VMs remain unaware of:</mark>
- Total space available to the hypervisor  
- Underlying storage technologies

![](https://i.imgur.com/ESrjNhO.png)

### <mark style="background: #BABD00;">Virtual Provisioning at Compute:</mark>

Hypervisor performs virtual provisioning to create virtual disks for VMs: Virtual machine sees full logical disk size at all times  

Hypervisor allocates storage space to the virtual disk only when VM requires storage space: Eliminates the need to overprovision virtual disks

![](https://i.imgur.com/cFT9boD.png)

<mark style="background: #BABD00;">Virtual Provisioning Benefits:</mark>  
- Reduces administrative overhead  
- Improves capacity utilization  
- Reduces cost  
- Reduces downtime

### <mark style="background: #BABD00;">Network Virtualization:</mark> 

<mark style="background: #BABD00;">Network Virtualization:</mark> It is a process of logically segmenting or grouping physical network(s) and making them operate as single or multiple independent network(s) called “Virtual Network(s)”.  
 
Enables virtual networks to share network resources  

Allows communication between nodes in a virtual network without routing of frames  

Enforces routing for communication between virtual networks  

Restricts management traffic, including ‘Network Broadcast’, from propagating to other virtual network  

Enables functional grouping of nodes in a virtual network

### <mark style="background: #BABD00;">Network Virtualisation in VDC:</mark>

Involves virtualizing physical and VM networks.

#### <mark style="background: #BABD00;">Physical Network:</mark>

Consists of following physical components: Network adapters, switches, routers, bridges, repeaters, and hubs  

<mark style="background: #BABD00;">Provides connectivity:</mark>  
- Among physical servers running hypervisor  
- Between physical servers and clients  
- Between physical servers and storage systems

![](https://i.imgur.com/kJY6wcy.png)

#### <mark style="background: #BABD00;">VM Network:</mark>
- Resides inside physical server  
- Consists of logical switches called “virtual switches”  
- Provides connectivity among VMs inside a physical server  
- Provides connectivity to Hypervisor kernel  
- Connects to physical network

![](https://i.imgur.com/1B78FqG.png)

### <mark style="background: #BABD00;">Network Connectivity and Traffic Flow: Example:</mark>

![](https://i.imgur.com/HJPqvRD.png)

### <mark style="background: #BABD00;">Benefits of Network Virtualisation</mark>

![](https://i.imgur.com/BqjNl27.png)

### <mark style="background: #BABD00;">Desktop Virtualization</mark>

<mark style="background: #BABD00;">Desktop Virtualization:</mark> Technology which enables detachment of the user state, the Operating System (OS), and the applications from endpoint devices.

Enables organizations to host and centrally manage desktops:
- Desktops run as virtual machines within the VDC, They may be accessed over LAN/WAN  
- Endpoint devices may be thin clients or PCs

![](https://i.imgur.com/w7zwbP4.png)

### <mark style="background: #BABD00;">Virtual Desktop Infrastructure (VDI): Components</mark>

- Endpoint devices  
- VM hosting/execution servers  
- Connection Broker

![](https://i.imgur.com/vJMn1zC.png)

<mark style="background: #BABD00;">Connection Broker:</mark> It is responsible for establishing and managing the connection between the endpoint device and the desktop VM

![](https://i.imgur.com/WxkCRcm.png)

### <mark style="background: #BABD00;">Application Virtualisation:</mark>

<mark style="background: #BABD00;">Application Virtualisation:</mark>  It is the technique of presenting an application to an end user without any installation, integration, or dependencies on the underlying computing platform

Allows application to be delivered in an isolated environment
- Aggregates Operating System (OS) resources and the application into a virtualized container  
- Ensures integrity of Operating System (OS) and applications  
- Avoids conflicts between different applications or different versions of the same application

### <mark style="background: #BABD00;">Cloud Computing: Essential Characteristics</mark>

![](https://i.imgur.com/fndT1WR.png)

### <mark style="background: #BABD00;">Cloud Offering Examples:</mark>

![](https://i.imgur.com/NUoid2H.png)

### <mark style="background: #BABD00;">Cloud Computing Benefits:</mark>

![](https://i.imgur.com/sQg0mcR.png)

### <mark style="background: #BABD00;">Cloud Deployment Model - Public Cloud:</mark>

![](https://i.imgur.com/qB9fvbj.png)

### <mark style="background: #BABD00;">Cloud Deployment Model - Private Cloud:</mark>

![](https://i.imgur.com/qVPWPaX.png)

### <mark style="background: #BABD00;">Cloud Deployment Model - Hybrid Cloud:</mark>

![](https://i.imgur.com/BpcmBVr.png)

### <mark style="background: #BABD00;">Economics of Cloud:</mark>

Cloud has changed the economics of IT  

Cloud enables to move from a CAPEX to an OPEX model  

<mark style="background: #BABD00;">Cloud provides the following key cost savings:</mark>  
- Infrastructure cost  
- Management cost  
- Power and energy cost

![](https://i.imgur.com/orr2QjE.png)

### <mark style="background: #BABD00;">Cloud Challenges – Consumer’s Perspective</mark>

<mark style="background: #BABD00;">Security and Regulation:</mark>  
- Consumers are indecisive to transfer control of sensitive data  
- Regulation may prevent organizations to use Cloud services  

<mark style="background: #BABD00;">Network latency:</mark> Real time applications may suffer due to network latency and limited bandwidth  

<mark style="background: #BABD00;">Supportability:</mark> Legacy or Custom applications may not be compatible with Cloud platform  

<mark style="background: #BABD00;">Interoperability:</mark> Lack of standardization across Cloud-based platforms

### <mark style="background: #BABD00;">Cloud Challenges – Provider’s Perspective:</mark>

<mark style="background: #BABD00;">Service warranty and service cost:</mark>  
- Resources must be kept ready to meet unpredictable demand  
- Hefty penalty, if SLAs are not fulfilled  

<mark style="background: #BABD00;">Huge numbers of software to manage:</mark>  
- Huge number of applications and platform software to purchase  
- ROI is unpredictable  

<mark style="background: #BABD00;">No standard Cloud access interface:</mark>  
- Cloud customers want open APIs  
- Need agreement among Cloud providers for standardisation

# <mark style="background: #BABD00;">08 DAS-NAS-SAN Storage</mark>

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

<mark style="background: #BABD00;">‘sharing protocols’ ? (Common file sharing protocols):</mark>  
- UNIX Network File System (NFS) was developed originally for sharing files between UNIX systems across a LAN.  
- Support expanded to include non-UNIX systems;  
- (but most NFS clients today are computers running some flavour of UNIX/Linux.)  

Windows Common Internet File System (CIFS) created by Microsoft, formerly known as Server Message Block (SMB), developed by IBM in DOS.

### <mark style="background: #BABD00;">NAS I/O Requests:</mark>
  
File I/O is a higher-level type of request that, in essence, specifies the file to be accessed, an offset into the file (as if the file was a set of contiguous bytes), and a number of bytes to read or write beginning at that offset.  

Unlike block I/O, there is no awareness of a disk volume or disk sectors in a file I/O request.  

Inside the NAS product (“appliance”), an operating system or OS kernel tracks where files are located on disk and issues a block I/O request to the disks to fulfil the file I/O read and write requests it receives.

### <mark style="background: #BABD00;">Network Storage Possibilities:</mark>

For small businesses, the solution for managing storage intelligently is consolidation.  

Rather than dispersing data across several PCs, laptops or small servers, consolidating storage into one or two locations makes it much easier to grow, manage and protect.  

When storage is freed from the constraints of individual PCs and file servers, it can be put on the network as a separate, single resource that can be allocated to applications as necessary.

### <mark style="background: #BABD00;">NAS:</mark>

Storage “Appliances” utilise a stripped-down OS that optimises file protocol performance  

Instead of starting with a general-purpose computer and configuring or removing features from that base, NAS designs begin with the bare-bones components necessary to support file transfers and add features “from the bottom up.”  

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
- Replacement of multiple independent storage devices by fewer devices that support capacity sharing - disk and tape pooling.  
- SANs provide the ultimate in scalability - software can allow multiple SAN devices to appear as a single pool of storage accessible to all processors on the SAN.  
- Storage on a SAN can be managed from a single point of control. Controls over which hosts can see which storage (called zoning and LUN masking) can be implemented.

<mark style="background: #BABD00;">Protection:</mark>  
- LAN-free backups occur over the SAN rather than the (slower) LAN, and server-free backups can let disk storage “write itself” directly to tape without processor overhead.  

<mark style="background: #BABD00;">Data Sharing:</mark>  
- sharing data, as noted earlier, offers benefits such as reducing the number of copies of files, increasing accessibility to current data and reducing the need to transfer copies of data between servers over the network.

### <mark style="background: #BABD00;">SAN - Different Technologies:</mark>

Multiple technologies can be used when building a SAN  

Traditionally the dominant technology is Fibre Channel, but IP based solutions are also quite popular for specific applications (due to costs!)  
  
The concept of SAN is also independent from the devices that are attached to it:
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

# <mark style="background: #BABD00;">09 Cloud Migration Considerations:</mark>


<mark style="background: #BABD00;">Upon completion of this lesson, you should be able to:</mark>  
- Discuss the considerations for migration to Cloud  
- Discuss the Cloud models suitable for different categories of users  
- List the considerations for choosing applications suitable for Cloud  
- Discuss different phases to adopt the Cloud

<mark style="background: #BABD00;">Topics covered in this lesson:</mark>  
- Considerations for Cloud model and suitable application for Cloud  
- Criteria for Cloud vendor selection  
- Service Level Agreements (SLAs) and performance issues  
- Cloud vendor lock-in  
- Cloud open standards

### <mark style="background: #BABD00;">Cloud Migration – Key Questions</mark>  

<mark style="background: #BABD00;">CIOs/IT Managers seeking to move to Cloud face several questions.</mark>
- How does Cloud fit into the organization’s requirements? (Financial advantage, convenience, etc. )
- Which are the applications suitable for Cloud?  
- How do I choose the Cloud Vendor?  
- Is the Cloud infrastructure capable of providing the required Quality of Service (QoS)?(Performance, availability, and security)  
- How will I address Change Management concerns?  
- What can Cloud provide? (Application, platform and infrastructure)

### <mark style="background: #BABD00;">How does Cloud fit to your requirements?</mark>  

Current infrastructure and requirements: Consider from application, network, and security perspectives.  

‘Risk vs. Convenience’ profile: Based on this profile, choose ‘Cloud model’ for your organization.

![](https://i.imgur.com/qq4VTWs.png)

### <mark style="background: #BABD00;">What Model Fits for You?</mark>

![](https://i.imgur.com/15IZYu6.png)

### <mark style="background: #BABD00;">Choosing Applications for Public Cloud:</mark>

<mark style="background: #BABD00;">Proprietary and mission-critical application:</mark>  
- Proprietary applications provide competitive advantage  
- Organization perceives high risk to move this application to Cloud  
- These applications are typically maintained in-house  

<mark style="background: #BABD00;">Non-proprietary but mission-critical application:</mark>  
- Organization perceives high risk to move this application to Cloud  
- It can be moved to Cloud if the organization does not have adequate resources to maintain the application  

<mark style="background: #BABD00;">Non-proprietary and non-mission critical application:</mark>  
- Perceived as good candidate for Cloud, unless it is performance sensitive

### <mark style="background: #BABD00;">Selecting a Cloud Service Provider:</mark>  

<mark style="background: #BABD00;">Some key questions to ask before selecting a Cloud Service provider:</mark>  
- How long has the provider been providing the services?  
- How well does the provider meet the organization’s current and future requirements?  
- How easy is it to relinquish resources not in use and to reduce cost?  
- What tools does the provider offer (like virtual machine images) that would make it easy to move to another provider when required?  
- How easy is it to add/remove services?  
- Does the provider have good customer service support?  
- What happens when the provider upgrades their software? Is it forced on everyone? Can you upgrade on your own schedule?  
- Does the provider offer required security services?  
- Does the provider meet your legal and privacy requirements?

### <mark style="background: #BABD00;">Service Level Agreement (SLA):</mark>  

SLA is an agreement between the Cloud provider and the consumer that defines the quality and reliability of service  

SLA also defines the penalty for not meeting the agreement  

SLAs include factors such as network availability, performance, etc.

### <mark style="background: #BABD00;">Cloud Performance:</mark>  

<mark style="background: #BABD00;">Two key performance considerations:</mark>  
- <mark style="background: #BABD00;">Infrastructure performance:</mark> Saturation of Cloud infrastructure may impact performance. Right amount of resources should be allocated to the application to ensure performance  
- <mark style="background: #BABD00;">Network latency:</mark> Network latency typically arises due to large data sets being sent to and from the Cloud provider

### <mark style="background: #BABD00;">Cloud Vendor Lock-in:</mark>

Cloud vendor (service provider) may lack open standards or use proprietary software/APIs.  

Rigid agreements prevent the consumer from moving without penalties.  

Cloud vendors may prevent a consumer from moving one service model to another (i.e. application built on a PaaS moving to an IaaS model).  

Application may require significant rework/redesign before deploying in different Cloud.

### <mark style="background: #BABD00;">Cloud Open Standards:</mark>
- Use proven and widely accepted technologies  
- Prevent lock-in issues  
- Open Virtual Machine Format (OVF) - an example of open standard

### <mark style="background: #BABD00;">Cloud Adoption Phases:</mark>

![](https://i.imgur.com/52roJ3L.png)

### <mark style="background: #BABD00;">Phase 1 - Assessment:</mark>

The assessment phase involves consideration of various factors  

Besides Cloud migration considerations discussed earlier, other key assessments are:  
- Financial  
- Security and compliance  
- Technical  
- Issues with licensed products

### <mark style="background: #BABD00;">Financial Assessment:</mark>

Provides cost comparison of in-house vs. service provider (TCO and ROI)  

Requires cost consideration of the following elements:

![](https://i.imgur.com/HsN7crB.png)

### <mark style="background: #BABD00;">Security and Compliance Assessment:</mark>

Involves security advisor early in the process  

<mark style="background: #BABD00;">Enables organizations to:</mark>  
- Identify risk tolerance and security threats for an application  
- Understand regulatory/contractual obligations to store data in specific jurisdictions  
- Explore whether the Cloud vendor offers: Choice of selecting geographic location to store the data. Guarantee that data does not move unless organization decides to move 
- Explore options to retrieve all data back from the Cloud when required  
- Identify the download or delete option of data, if required  
- Identify the choice of encryption of data when in transit and at rest

### <mark style="background: #BABD00;">Technical Assessment:</mark>

<mark style="background: #BABD00;">Enables organizations to:</mark>  
- Identify whether Cloud service provider offers the required infrastructure  
- Identify whether an application is compatible with Cloud infrastructure  
- Identify the dependencies of an application on other components and services  
- Identify the component that must be local (on-premise) and components that can move to the Cloud 
- Identify the latency and bandwidth requirements  
- Estimate the effort required to migrate the application

### <mark style="background: #BABD00;">Assessment of License Issues:</mark>  

<mark style="background: #BABD00;">Use existing license:</mark>  
- Identify whether the organization can move its existing licensed software into the Cloud  
- Cloud providers have partnered with software vendors to permit the use of existing software license in the Cloud  

<mark style="background: #BABD00;">Use SaaS based Cloud service:</mark>  
- Some software vendors offer their software as a service apart from installable option 
- If a software vendor does not offer its software as a service, explore an equivalent offering by different Cloud vendor

### <mark style="background: #BABD00;">Phase 2: Proof of Concept</mark>  

Goal of this phase is to verify that an application runs as expected in the Cloud  

<mark style="background: #BABD00;">Proof of Concept enables organizations to:</mark>  
- Explore the capabilities of the Cloud  
- Explore the different business continuity and disaster recovery options offered by the Cloud vendor  
- Estimate the effort required to roll out the application  
- Identify applications that can be immediately moved after proof of concept

### <mark style="background: #BABD00;">Phase 3: Migration</mark>

![](https://i.imgur.com/eyDmzju.png)

### <mark style="background: #BABD00;">Phase 4: Optimisation</mark>

Test the application after migration is complete  

Understand the usage pattern and optimize resource consumption  

Relinquish idle resources

### <mark style="background: #BABD00;">Summary:</mark>

<mark style="background: #BABD00;">Key points covered in this module:</mark>  
- Considerations for migration to Cloud  
- Cloud models suitable for different categories of users  
- Guidelines for selecting a suitable application for Cloud  
- Phases to adopt the Cloud

### <mark style="background: #BABD00;">Check Your Knowledge:</mark>  
1. What are the key concerns that organizations have while adopting the Cloud?  
2. Describe the guidelines for choosing the right application for the Cloud.  
3. What are the two options available for migrating licensed software to the Cloud?  
4. Describe the two migration strategies.  
5. What should be considered to avoid Cloud vendor lock-in?

# <mark style="background: #BABD00;">10 Data Protection RAID</mark>


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

# <mark style="background: #BABD00;">11 Snapshots</mark>

Snapshots (or Checkpoints) is like capturing an image of your virtual machine at a moment in time

Easier when machine is powered off, like downloading a file.

A transaction in a database is not complete until all components of the transaction have been completed.

Snapshots often need to be taken of production machines that cannot be brought down, this is complicated

Useful when you need to perform a complicated upgrade to an application in a VM and want a quick way to roll back the changes if something goes wrong.

PowerPoint and word docs compile down to XML. Microsoft chose XML because it is extensible, promoting forward and backward compatibility.

A mark-up language is a language with annotations.

<mark style="background: #BABD00;">Do not ever use snapshots in place of backups!</mark>

### <mark style="background: #BABD00;">Creating a Snapshot:</mark>

Two types of checkpoints:
- Production Checkpoints
- Standard Checkpoints

### <mark style="background: #BABD00;">Introduction:</mark>

<mark style="background: #BABD00;">Scenario:</mark>  
- Need to perform a complicated upgrade to an application in a VM and want a quick way to roll back the changes if something goes wrong.  
- The company is building a demo or class lab and a quick way is needed to reset the virtual machines to their starting point.  
- You are testing software and need to repeat a set of tests very quickly without re-deploying virtual machines.

### <mark style="background: #BABD00;">Why Snapshots?</mark>

Keep multiple captures of a single virtual machine over time  

Could snapshot a virtual machine with just the operating system, service pack, and patches.  

Then create a second snapshot with SQL Server, service pack, and update rollup.  

Then a third snapshot with an application installed in the virtual machine.  

Can roll back the virtual machine (by applying a snapshot) to any of these 3 points in time to redo an install for the purposes of demo, testing, documentation, or training.  

A hierarchy of snapshots will be created for you

### <mark style="background: #BABD00;">Creating a Snapshot:</mark>

Two types of checkpoints  

<mark style="background: #BABD00;">Production Checkpoints:</mark>  
- Use backup technology in the Guest OS to create data-consistent checkpoints that do not include information about running applications.  
- uses Volume Shadow Copy Service or File System Freeze on a Linux virtual machine to create a data-consistent backup of the virtual machine. No snapshot of the virtual machine memory state is taken.  

<mark style="background: #BABD00;">Standard Checkpoints:</mark>
- Creates application-consistent checkpoints that capture the current state of the applications.  
- Takes a snapshot of the virtual machine and virtual machine memory state at the time the checkpoint is initiated.  
- A snapshot is not a full backup and can cause data consistency issues with systems that replicate data between different nodes such as Active Directory.  
- Hyper-V only offered standard checkpoints (formerly called snapshots) prior to Windows 10.

### <mark style="background: #BABD00;">Volume Shadow Copy Service (VSS):</mark>

Backing up and restoring critical business data can be very complex  

The data usually needs to be backed up while the applications that produce the data are still running. This means that some of the data files might be open or they might be in an inconsistent state  

If the data set is large, it can be difficult to back up all of it at one time  

Correctly performing backup and restore operations requires close coordination between  
- between the backup applications,  
- and the line-of-business applications that are being backed up,  
- and the storage management hardware and software.

Volume Shadow Copy Service (VSS) facilitates the  
conversation between these components to allow them to work better together.  

When all the components support VSS, you can use them to back up your application data without taking the applications offline.  

VSS coordinates the actions that are required to create a consistent shadow copy (also known as a snapshot or a point-in-time copy) of the data that is to be backed up.

The shadow copy can be used as-is, or it can be used in scenarios such as the following:  
- You want to back up application data and system state information, including archiving data to another hard disk drive, to tape, or to other removable media.  
- You're data mining.  
- You're performing disk-to-disk backups.  
- You need a fast recovery from data loss by restoring data to the original Logical Unit Number (LUN) or to an entirely new LUN that replaces an original LUN that failed

### <mark style="background: #BABD00;">How are snapshots stored?</mark>

When you take a snapshot of a running VM, Hyper-V briefly pauses the VM to create a new automatic virtual hard disk (AVHD) which is <mark style="background: #BABD00;">essentially a differencing disk</mark>, attaches it to the VM to store changes to the VM data, saves the processor state into a file (.bin), then resumes the VM.  

Hyper-V also makes a copy of the VM configuration file, and saves the contents of the VM memory and processor state.  

Snapshots can also be created when a VM is turned-off, in which case Hyper-V does not need to capture VM memory or processor state data.

Snapshot data files are stored as .avhd files (with Hyper-V).  

Taking multiple snapshots can quickly consume storage space!  

Files usually are located in the same folder (or a sub folder) as the virtual hard disk.  

Do not delete .avhd files directly from the storage location. Instead, use Hyper-V Manager to select the virtual machine, and then delete the snapshots from the snapshot tree.

### <mark style="background: #BABD00;">Virtual Disk File Formats:</mark>

<mark style="background: #BABD00;">VMDK:</mark> An open format developed by VMWare.  Most common format (used by Oracle VirtualBox)

<mark style="background: #BABD00;">VHD:</mark> A native format from Microsoft (Hyper-V and Microsoft Virtual PC)

<mark style="background: #BABD00;">VHDX:</mark> Next Generation VHD:
- VHDX has 64TB disk limit; VHD has 2TB disk limit.  
- VHDX supports large block sizes (sometimes better performance)  
- VHDX protects against file corruption, VHD does not.  
- Two way conversion between VHD and VHDX is possible.  
- VHDX works in Windows Server 2012 and later (not earlier).  
- VHDX is supported in Microsoft Azure (as of 2021).

<mark style="background: #BABD00;">AVHD:</mark> A VHD differencing disk.  

<mark style="background: #BABD00;">AVHDX:</mark> A VHDX differencing disk.

<mark style="background: #BABD00;">OVF:</mark>  
- The OVF Specification provides a means of describing the properties of a virtual system.  
- It is an XML based format.  
- It supports extendibility.  
- An OVF file is used to describe a single virtual machine or single virtual appliance.  

<mark style="background: #BABD00;">OVA:</mark> An OVA file is an OVF file packaged together with all of its supporting files (disk images, metadata, etc).

![](https://i.imgur.com/VUWGvD2.png)

### <mark style="background: #BABD00;">Snapshot considerations:</mark>

Taking a snapshot (also known as checkpoint) reduces the performance of the virtual machine while the snapshot is created. You should not use these snapshots on virtual machines that provide  
services in a production environment.  
[Microsoft Learning Link](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/best-practices-analyzer/avoid-using-checkpoints-on-a-virtual-machine-server-workload-production)  

MS do not recommend using snapshots on virtual machines that are configured with fixed virtual hard disks because they reduce the performance benefits that are otherwise gained by using fixed virtual hard disks. (Why?)

[Link 1 - Winsows 2012](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn818483(v=ws.11) "https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn818483(v=ws.11)")

[Link2 - Fixed vs dynamic disks](https://learn.microsoft.com/en-us/answers/questions/560255/fixed-vs-dynamic-disks "https://learn.microsoft.com/en-us/answers/questions/560255/fixed-vs-dynamic-disks")

[Azure managed disks overview](https://learn.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview "https://learn.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview")

[hyper v guest design fixed vs dynamic vhd](https://www.altaro.com/hyper-v/hyper-v-guest-design-fixed-vs-dynamic-vhd/ "https://www.altaro.com/hyper-v/hyper-v-guest-design-fixed-vs-dynamic-vhd/")

Presence of a VM snapshot reduces the disk performance of the virtual machine. Creating more snapshots will increase that degradation. Hyper-V snapshots should not to be used as a VM backup.  

Taking multiple snapshots can quickly consume a large amount of storage space. When you use Hyper-V Manager to delete a snapshot, the snapshot is removed from the snapshot tree but the ``.avhd`` file is not deleted until you turn off the virtual machine.

### <mark style="background: #BABD00;">Automatic Virtual Hard Disk:</mark>

Each virtual hard disk of the virtual machine is also treated by the snapshot. This is done using a special kind of differential virtual hard disk called the <mark style="background: #BABD00;">Automatic Virtual Hard Disk (AVHD)</mark>:

![](https://i.imgur.com/bHrMMLM.png)

A differencing disk is the disk created the moment you begin a snapshot.

Each <mark style="background: #BABD00;">VHD</mark> file will become a parent to an AVHD file. The virtual machine will start using the AVHD file for reads and writes after the snapshot, and the VHD file for reads older than the snapshot.  

Each <mark style="background: #BABD00;">VHDX</mark> file will become a parent to an AVHDX file. The virtual machine will start using the AVHDX file for reads and writes after the snapshot, and the VHDX file for reads older than the snapshot.  

With each new snapshot that is taken, the active AVHD is detached from the VM, and becomes the parent of a new child AVHD that is attached to the VM and captures changes to the VM data until the next snapshot is  created. Note: Hierarchy!

### <mark style="background: #BABD00;">Reverting/Applying Snapshots:</mark>

Revert feature can be thought of as a single-level undo feature! Previous snapshot state.  

During the Revert process, the VM is stopped, the current AVHD is deleted, and a new AVHD is created. (new ‘fork’ for progress)  

When a Revert is performed, all configuration modifications made to the running VM since the snapshot was taken are discarded.  

Apply option may be used to return to a snapshot that is higher than one level up from the running VM. Fully flexible.

### <mark style="background: #BABD00;">Deleting Snapshots:</mark>

Deleting a single snapshot will not affect other snapshots (at the same level), but it will immediately delete the configuration file and save state files associated with the snapshot. 

<mark style="background: #BABD00;">NB:</mark> In a snapshot hierarchy, the snapshot AVHD may be related to other snapshot AVHDs through a parent-child relationship. A snapshot AVHD is only immediately deleted if it is not the parent of a child AVHD.  

If there is only one child AVHD, it is merged into the parent AVHD the next time that the VM is powered-off.

Deleting a snapshot subtree immediately deletes the configuration and save state files associated with all the snapshots in the subtree. If the running virtual machine AVHD is not a child of any snapshot in the subtree, then all of the AVHDs in the subtree will also be deleted.  

(If the running virtual machine AVHD depends on a chain of AVHDs in the subtree that is deleted, then the AVHD chain will be merged into the AVHD that is one level above the deleted subtree, the next time that the VM is powered-off.)

### <mark style="background: #BABD00;">Common snapshot mistakes:</mark>

There are several mistakes that one can make with snapshots:  

<mark style="background: #BABD00;">Swap the parent VHD/X files:</mark> There is a link between the AVHD/X and the VHD/X file. Do not attempt to break and recreate this link.  

<mark style="background: #BABD00;">Delete the VHD/X files:</mark> Data older than the snapshot, such as the guest operating system, are stored in the parent disks. Do not delete the virtual hard disks.  

<mark style="background: #BABD00;">Delete the AVHD/X files:</mark> Doing this will delete all the data of the virtual machine since the snapshot was created. Do not do this.  

<mark style="background: #BABD00;">Leave a snapshot in place for a long time:</mark> Differential disks, and therefore AVHD/X files, are intended for short-term usage. Performance will degrade as the files will continue to grow over time.

### <mark style="background: #BABD00;">Archival Backups?</mark>

Export the virtual machine.  

Takes some time, but you can make an importable copy of many virtual machines at once by using the Hyper-V Manager. What you end up with is a set of files that can be copied to a new location and easily imported.  

Use PowerShell and it’s support of WMI to administer Hyper-V. So, a script could automate:  
- Shutting down the virtual machine  
- Exporting the virtual machine and/or Copy the .VHD files  
- Starting the virtual machine  

Or treat it as if it were a physical server – complete with backup agents installed into it, and using some enterprise class backup and archiving solution. It all depends upon the purpose of the server, the business applications and/or data housed therein, the ease with which you want to be able to recreate the server, etc. Altaro, VEEAM, etc.

# <mark style="background: #BABD00;">12 Introduction to Docker</mark>

### <mark style="background: #BABD00;">What is Docker?</mark>

Docker is an open-source project that automates the deployment of applications inside software containers, by providing an additional layer of abstraction and automation of operating system–level virtualisation on Linux.  - [Source: en.wikipedia.org]  

Docker allows you to package an application with all of its dependencies into a standardised unit for software development.  - [www.docker.com]

### <mark style="background: #BABD00;">The challenge:</mark>

![](https://i.imgur.com/bQAjcRU.png)

<mark style="background: #BABD00;">Results in NXM compatibility nightmare:</mark>

![](https://i.imgur.com/XMT3k90.png)

### <mark style="background: #BABD00;">Docker is a shipping container for code:</mark>

![](https://i.imgur.com/Vx0INie.png)

<mark style="background: #BABD00;">Solves the NXM matrix problem:</mark>

![](https://i.imgur.com/ic5kEeb.png)

### <mark style="background: #BABD00;">Docker Containers:</mark>

Docker container wrap a piece of software in a complete file system that contains everything needed to run:  
- Code, runtime, system tools, system libraries  
- Anything that can be installed on a server  

This guarantees that the software will always run the same, regardless of the environment it is running in.

![](https://i.imgur.com/ByKnuRX.png)

### <mark style="background: #BABD00;">Why containers matter:</mark>

![](https://i.imgur.com/Bjkok23.png)

### <mark style="background: #BABD00;">Docker containers</mark>

<mark style="background: #BABD00;">Lightweight:</mark>
- Containers running on one machine all share the same OS kernel  
- They start instantly and make more efficient use of RAM  
- Images are constructed from layered file systems  
- They can share common files, making disk usage and image downloads much more efficient

<mark style="background: #BABD00;">Open:</mark>
- Based on open standards  
- Allowing containers to run on all major Linux distributions and Microsoft OS with support for every infrastructure

<mark style="background: #BABD00;">Secure:</mark>
- Containers isolate applications from each other and the underlying infrastructure while providing an added layer of protection for the application

### <mark style="background: #BABD00;">Containers vs VMs:</mark>

Containers have similar resource isolation and allocation benefits as VMs but a different architectural approach allows them to be much more portable and efficient

<mark style="background: #BABD00;">Docker Container:</mark>
- It includes the application and all of its dependencies, but share the kernel with other containers.  
- They run as an isolated process in userspace on the host operating system.  
- Docker containers run on any computer, on any infrastructure and in any cloud

![](https://i.imgur.com/Avz94PV.png)

<mark style="background: #BABD00;">VM:</mark>
- Each virtual machine includes the application, the necessary binaries and libraries and an entire guest operating system - all of which may be tens of GBs in size

![](https://i.imgur.com/3roZxCc.png)

### <mark style="background: #BABD00;">Why are docker containers lightweight?</mark>

<mark style="background: #BABD00;">VMs:</mark> Every app, every copy of an app, and every slight modification of the app requires a new virtual server
![](https://i.imgur.com/OW9QmZP.png)

<mark style="background: #BABD00;">Containers:</mark>

![](https://i.imgur.com/7ukDqSv.png)

### <mark style="background: #BABD00;">What are the basics of the Docker system?</mark>

![](https://i.imgur.com/nVGc81q.png)

### <mark style="background: #BABD00;">Changes and Updates:</mark>

![](https://i.imgur.com/YQ9LHL1.png)

### <mark style="background: #BABD00;">How does this help you build better software?</mark>

<mark style="background: #BABD00;">Accelerate Developer Onboarding:</mark>
- Stop wasting hours trying to setup developer environments  
- Spin up new instances and make copies of production code to run locally  
- With Docker, you can easily take copies of your live environment and run on any new endpoint running Docker.

<mark style="background: #BABD00;">Empower Developer Creativity:</mark>
- The isolation capabilities of Docker containers free developers from the worries of using “approved” language stacks and tooling  
- Developers can use the best language and tools for their application service without worrying about causing conflict issues

<mark style="background: #BABD00;">Eliminate Environment Inconsistencies:</mark>
- By packaging up the application with its configs and dependencies together and shipping as a container, the application will always work as designed locally, on another machine, in test or production  
- No more worries about having to install the same configs into a different environment


### <mark style="background: #BABD00;">Easily Share and Collaborate on Applications:</mark>

Docker creates a common framework for developers and sysadmins to work together on distributed applications.

<mark style="background: #BABD00;">Distribute and share content:</mark>
- Store, distribute and manage your Docker images in your Docker Hub with your team  
- Image updates, changes and history are automatically shared across your organization.  

<mark style="background: #BABD00;">Simply share your application with others:</mark>  
- Ship your containers to others without worrying about different environment dependencies creating issues with your application.  
- Other teams can easily link to or test against your app without having to learn or worry about how it works

### <mark style="background: #BABD00;">Getting started with Docker:</mark>

- install Docker  
- run a software image in a container  
- browse for an image on Docker Hub  
- create your own image and run it in a container  
- create a Docker Hub account and an image repository  
- create an image of your own  
- push your image to Docker Hub for others to use

### <mark style="background: #BABD00;">Example: a health and fitness Mobile App:</mark>

You’ve been tasked with creating the REST API for a mobile app for tracking health and fitness  

You code the first endpoint using the development environment on your laptop  

After running all the unit tests and seeing that they passed, you check your code into the Git repository and let the QA engineer know that the build is ready for testing  

The QA engineer dutifully deploys the most recent build to the test environment, and within the first few minutes of testing discovers that your recently developed REST endpoint is broken  

After spending a few hours troubleshooting alongside the QA engineer, you discover that the test environment is using an outdated version of a third-party library, and this is what is causing your REST endpoints to break

<mark style="background: #BABD00;">Slight differences between development, test, stage, and production environments can wreak mayhem on an application</mark>

<mark style="background: #BABD00;">Solution:</mark>
- Traditional approaches for dealing with this problem, such as change management processes, are too cumbersome for today’s rapid build and deploy cycles  
- What is needed instead is a way to transfer an environment seamlessly from development to test, eliminating the need for manual and error prone resource provisioning and configuration.  
- You can create Docker images from a running container. For example, one could launch a container, install a bunch of software packages using a package manager like APT or yum, and then commit those changes to a new Docker image.

<mark style="background: #BABD00;">Solution in Example:</mark>
- First, define a Docker image for launching a container for running the REST endpoint  
- Use this to test our code on a laptop, and the QA engineer can use this to test the code in Google Compute Engine/AWS EC2/Azure VM.  
- The REST endpoints are going to be developed using Ruby and the Sinatra framework, so these will need to be installed in the image  
- The back end will use Google Firestore/Amazon DynamoDB/Azure CosmosDB

![](https://i.imgur.com/rjSx09H.png)

# <mark style="background: #BABD00;">13 Required Reading CA 1</mark>

# <mark style="background: #BABD00;">Week 2:</mark>

### <mark style="background: #BABD00;">NIST Definition of Cloud Computing:</mark>

<mark style="background: #BABD00;">NIST:</mark> National Institute of Standards and Technology (USA)

<mark style="background: #BABD00;">Cloud computing</mark> is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.  

This cloud model is composed of five essential characteristics, three service models, and four deployment  models.  

#### <mark style="background: #BABD00;">Essential Characteristics:</mark>  

<mark style="background: #BABD00;">On-demand self-service.</mark> A consumer can unilaterally provision computing capabilities, such as server time and network storage, as needed automatically without requiring human interaction with each service provider.  

<mark style="background: #BABD00;">Broad network access.</mark> Capabilities are available over the network and accessed through standard  mechanisms that promote use by heterogeneous thin or thick client platforms (e.g., mobile phones, tablets, laptops, and workstations).  

<mark style="background: #BABD00;">Resource pooling.</mark> The provider’s computing resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand. There is a sense of location independence in that the customer generally has no control or knowledge over the exact location of the provided resources but may be able to specify location at a higher level of abstraction (e.g., country, state, or datacenter). Examples of resources include storage, processing, memory, and network bandwidth.  

<mark style="background: #BABD00;">Rapid elasticity.</mark> Capabilities can be elastically provisioned and released, in some cases automatically, to scale rapidly outward and inward commensurate with demand. To the consumer, the capabilities available for provisioning often appear to be unlimited and can be appropriated in any quantity at any time.  

<mark style="background: #BABD00;">Measured service.</mark> Cloud systems automatically control and optimize resource use by leveraging a metering capability<sup>1</sup> at some level of abstraction appropriate to the type of service (e.g., storage, processing, bandwidth, and active user accounts). Resource usage can be monitored, controlled, and reported, providing transparency for both the provider and consumer of the utilized service.  

#### <mark style="background: #BABD00;">Service Models:</mark>  

<mark style="background: #BABD00;">Software as a Service (SaaS).</mark> The capability provided to the consumer is to use the provider’s applications running on a cloud infrastructure<sup>2</sup>. The applications are accessible from various client devices through either a thin client interface, such as a web browser (e.g., web-based email), or a program interface. The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems, storage, or even individual application capabilities, with the possible exception of limited user-specific application configuration settings. 

<mark style="background: #BABD00;">Platform as a Service (PaaS).</mark> The capability provided to the consumer is to deploy onto the cloud infrastructure consumer-created or acquired applications created using programming languages, libraries, services, and tools supported by the provider<sup>3</sup>. The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems, or storage, but has control over the deployed applications and possibly configuration settings for the application-hosting environment.  

<mark style="background: #BABD00;">Infrastructure as a Service (IaaS).</mark> The capability provided to the consumer is to provision processing, storage, networks, and other fundamental computing resources where the consumer is able to deploy and run arbitrary software, which can include operating systems and applications. The consumer does not manage or control the underlying cloud infrastructure but has control over operating systems, storage, and deployed applications; and possibly limited control of select networking components (e.g., host firewalls).

#### <mark style="background: #BABD00;">Deployment Models:</mark>  

<mark style="background: #BABD00;">Private cloud.</mark> The cloud infrastructure is provisioned for exclusive use by a single organization comprising multiple consumers (e.g., business units). It may be owned, managed, and operated by the organization, a third party, or some combination of them, and it may exist on or off premises.

<mark style="background: #BABD00;">Community cloud.</mark> The cloud infrastructure is provisioned for exclusive use by a specific community of consumers from organizations that have shared concerns (e.g., mission, security requirements, policy, and compliance considerations). It may be owned, managed, and operated by one or more of the organizations in the community, a third party, or some combination of them, and it may exist on or off premises.  

<mark style="background: #BABD00;">Public cloud.</mark> The cloud infrastructure is provisioned for open use by the general public. It may be owned, managed, and operated by a business, academic, or government organization, or some combination of them. It exists on the premises of the cloud provider.  

<mark style="background: #BABD00;">Hybrid cloud.</mark> The cloud infrastructure is a composition of two or more distinct cloud infrastructures (private, community, or public) that remain unique entities, but are bound together by standardized or proprietary technology that enables data and application portability (e.g., cloud bursting for load balancing between clouds).

<mark style="background: #BABD00;">Footnotes:</mark>
1. 1 Typically this is done on a pay-per-use or charge-per-use basis.  
2. A cloud infrastructure is the collection of hardware and software that enables the five essential characteristics of cloud computing. The cloud infrastructure can be viewed as containing both a physical layer and an abstraction layer. The physical layer consists of the hardware resources that are necessary to support the cloud services being provided, and typically includes server, storage and network components. The abstraction layer consists of the software deployed across the physical layer, which manifests the essential cloud characteristics. Conceptually the abstraction layer sits above the physical layer.
3. This capability does not necessarily preclude the use of compatible programming languages, libraries, services, and tools from other sources.

### <mark style="background: #BABD00;">CONTENT DELIVERY NETWORK:</mark>
#### <mark style="background: #BABD00;">What is a Content Delivery Network (CDN)?</mark>

[Source](https://www.cloudflare.com/en-gb/learning/cdn/what-is-a-cdn/)

A content delivery network (CDN) is a geographically distributed group of servers that caches content close to end users. A CDN allows for the quick transfer of assets needed for loading Internet content, including HTML pages, JavaScript files, stylesheets, images, and videos.

The popularity of CDN services continues to grow, and today the majority of web traffic is served through CDNs, including traffic from major sites like Facebook, Netflix, and Amazon.

A properly configured CDN may also help protect websites against some common malicious attacks, such as [Distributed Denial of Service (DDOS) attacks](https://www.cloudflare.com/learning/ddos/what-is-a-ddos-attack/).

#### <mark style="background: #BABD00;">Is a CDN the same as a web host?</mark>

While a CDN does not host content and can’t replace the need for proper web hosting, it does help [cache](https://www.cloudflare.com/learning/cdn/what-is-caching/) content at the [network edge](https://www.cloudflare.com/learning/serverless/glossary/what-is-edge-computing/), which improves website performance. Many websites struggle to have their [performance](https://www.cloudflare.com/learning/cdn/performance/) needs met by traditional hosting services, which is why they opt for CDNs.

By utilizing caching to reduce hosting bandwidth, [helping to prevent interruptions in service](https://www.cloudflare.com/learning/cdn/cdn-load-balance-reliability/), and [improving security](https://www.cloudflare.com/learning/cdn/cdn-ssl-tls-security/), CDNs are a popular choice to relieve some of the major pain points that come with traditional web hosting.

#### <mark style="background: #BABD00;">What are the benefits of using a CDN?</mark>

Although the benefits of using a CDN vary depending on the size and needs of an Internet property, the primary benefits for most users can be broken down into four different components:

1. <mark style="background: #BABD00;">Improving website load times</mark> - By distributing content closer to website visitors by using a nearby CDN server (among other optimizations), visitors experience faster page loading times. As visitors are more inclined to click away from a slow-loading site, a CDN can reduce bounce rates and increase the amount of time that people spend on the site. In other words, a faster a website means more visitors will stay and stick around longer.

2. <mark style="background: #BABD00;">Reducing bandwidth costs</mark> - Bandwidth consumption costs for website hosting is a primary expense for websites. Through caching and other optimizations, CDNs are able to reduce the amount of data an origin server must provide, thus reducing hosting costs for website owners.

3. <mark style="background: #BABD00;">Increasing content availability and redundancy</mark> - Large amounts of traffic or hardware failures can interrupt normal website function. Thanks to their distributed nature, a CDN can handle more traffic and withstand hardware failure better than many origin servers.

4. <mark style="background: #BABD00;">Improving website security</mark> - A CDN may improve security by providing [DDoS mitigation](https://www.cloudflare.com/learning/ddos/ddos-mitigation/), improvements to security certificates, and other optimizations.

#### <mark style="background: #BABD00;">How does a CDN work?</mark>

At its core, a CDN is a network of servers linked together with the goal of delivering content as quickly, cheaply, reliably, and securely as possible. In order to improve speed and connectivity, a CDN will place servers at the exchange points between different networks.

These [Internet exchange points (IXPs)](https://www.cloudflare.com/learning/cdn/glossary/internet-exchange-point-ixp/) are the primary locations where different Internet providers connect in order to provide each other access to traffic originating on their different networks. By having a connection to these high speed and highly interconnected locations, a CDN provider is able to reduce costs and transit times in high speed data delivery.

![](https://i.imgur.com/p4FOzjp.png)

Beyond placement of servers in IXPs, a CDN makes a number of optimizations on standard client/server data transfers. CDNs place Data Centres at strategic locations across the globe, enhance security, and are designed to survive various types of failures and Internet congestion.

#### <mark style="background: #BABD00;">Latency - How does a CDN improve website load times?</mark>

When it comes to websites loading content, users drop off quickly as a site slows down. CDN services can help to reduce load times in the following ways:
- The globally distributed nature of a CDN means reduce distance between users and website resources. Instead of having to connect to wherever a website’s [origin server](https://www.cloudflare.com/learning/cdn/glossary/origin-server/) may live, a CDN lets users connect to a geographically closer [data centre](https://www.cloudflare.com/learning/cdn/glossary/internet-exchange-point-ixp/). Less travel time means faster service.
- Hardware and software optimizations such as efficient load balancing and solid-state hard drives can help data reach the user faster.
- CDNs can reduce the amount of data that’s transferred by reducing file sizes using tactics such as [minification](https://www.cloudflare.com/learning/performance/why-minify-javascript-code/) and file compression. Smaller file sizes mean quicker load times.
- CDNs can also speed up sites which use [TLS](https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/)/[SSL](https://www.cloudflare.com/learning/ssl/what-is-ssl/) certificates by optimizing connection reuse and enabling TLS false start.

[Explore all the ways a CDN helps websites load faster](https://www.cloudflare.com/learning/cdn/performance/)

#### <mark style="background: #BABD00;">Reliability and redundancy - How does a CDN keep a website always online?</mark>

Uptime is a critical component for anyone with an Internet property. Hardware failures and spikes in traffic, as a result of either malicious attacks or just a boost in popularity, have the potential to bring down a web server and prevent users from accessing a site or service. A well-rounded CDN has several features that will minimize downtime:

- Load balancing distributes network traffic evenly across several servers, making it easier to scale rapid boosts in traffic.
- Intelligent failover provides uninterrupted service even if one or more of the CDN servers go offline due to hardware malfunction; the failover can redistribute the traffic to the other operational servers.
- In the event that an entire data centre is having technical issues, [Anycast](https://www.cloudflare.com/learning/cdn/glossary/anycast-network/) routing transfers the traffic to another available data centre, ensuring that no users lose access to the website.

[Learn more about how a CDN helps keep websites online](https://www.cloudflare.com/learning/cdn/cdn-load-balance-reliability/)

#### <mark style="background: #BABD00;">Data security - How does a CDN protect data?</mark>

Information security is an integral part of a CDN. a CDN can keep a site secured with fresh [TLS/SSL certificates](https://www.cloudflare.com/learning/ssl/what-is-an-ssl-certificate/) which will ensure a high standard of authentication, [encryption](https://www.cloudflare.com/learning/ssl/what-is-encryption/), and integrity. Investigate the security concerns surrounding CDNs, and explore what can be done to securely deliver content. [Learn about CDN SSL/TLS security](https://www.cloudflare.com/learning/cdn/cdn-ssl-tls-security/)

#### <mark style="background: #BABD00;">Bandwidth expense - How does a CDN reduce bandwidth costs?</mark>

Every time an origin server responds to a request, bandwidth is consumed. See how a CDN, like the [Cloudflare CDN](https://www.cloudflare.com/application-services/products/cdn/), cuts down on origin requests and [reduces bandwidth costs](https://www.cloudflare.com/learning/cdn/how-cdns-reduce-bandwidth-cost/).

### <mark style="background: #BABD00;">Serverless Computing:</mark>

#### <mark style="background: #BABD00;">What is serverless computing?</mark>

Serverless computing is a method of providing backend services on an as-used basis. A serverless provider allows users to write and deploy code without the hassle of worrying about the underlying infrastructure. A company that gets backend services from a serverless vendor is charged based on their computation and do not have to reserve and pay for a fixed amount of bandwidth or number of servers, as the service is auto-scaling. Note that despite the name serverless, physical servers are still used but developers do not need to be aware of them.

In the early days of the web, anyone who wanted to build a web application had to own the physical hardware required to run a server, which is a cumbersome and expensive undertaking.

Then came [cloud computing](https://www.cloudflare.com/learning/cloud/what-is-the-cloud/), where fixed numbers of servers or amounts of server space could be rented remotely. Developers and companies who rent these fixed units of server space generally over-purchase to ensure that a spike in traffic or activity will not exceed their monthly limits and break their applications. This means that much of the server space that gets paid for can go to waste. Cloud vendors have introduced auto-scaling models to address the issue, but even with auto-scaling an unwanted spike in activity, such as a [DDoS Attack](https://www.cloudflare.com/learning/ddos/what-is-a-ddos-attack/), could end up being very expensive.

![](https://i.imgur.com/Gtd4R3y.png)

Serverless computing allows developers to purchase backend services on a flexible ‘pay-as-you-go’ basis, meaning that developers only have to pay for the services they use. This is like switching from a cell phone data plan with a monthly fixed limit, to one that only charges for each byte of data that actually gets used.

The term ‘serverless’ is somewhat misleading, as there are still servers providing these backend services, but all of the server space and infrastructure concerns are handled by the vendor. Serverless means that the developers can do their work without having to worry about servers at all.

#### <mark style="background: #BABD00;">What are backend services? What’s the difference between frontend and backend?</mark>

[Source](https://www.cloudflare.com/en-gb/learning/serverless/what-is-serverless/)

Application development is generally split into two realms: the frontend and the backend. The frontend is the part of the application that users see and interact with, such as the visual layout. The backend is the part that the user doesn’t see; this includes the server where the application's files live and the database where user data and business logic is persisted.

![](https://i.imgur.com/yZlc8Zm.png)

For example, let’s imagine a website that sells concert tickets. When a user types a website address into the browser window, the browser sends a request to the backend server, which responds with the website data. The user will then see the frontend of the website, which can include content such as text, images, and form fields for the user to fill out. The user can then interact with one of the form fields on the frontend to search for their favorite musical act. When the user clicks on ‘submit’, this will trigger another request to the backend. The backend code checks its database to see if a performer with this name exists, and if so, when they will be playing next, and how many tickets are available. The backend will then pass that data back to the frontend, and the frontend will display the results in a way that makes sense to the user. Similarly, when the user creates an account and enters financial information to buy the tickets, another back-and-forth communication between the frontend and backend will occur.

#### <mark style="background: #BABD00;">What kind of backend services can serverless computing provide?</mark>

Most serverless providers offer database and storage services to their customers, and many also have [Function-as-a-Service (FaaS)](https://www.cloudflare.com/learning/serverless/glossary/function-as-a-service-faas/) platforms, like [Cloudflare Workers](https://www.cloudflare.com/developer-platform/workers/). FaaS allows developers to execute small pieces of code on the [network edge](https://www.cloudflare.com/learning/serverless/glossary/what-is-edge-computing/). With FaaS, developers can build a modular architecture, making a codebase that is more scalable without having to spend resources on maintaining the underlying backend. [Learn more about FaaS >>](https://www.cloudflare.com/learning/serverless/glossary/function-as-a-service-faas/)

#### <mark style="background: #BABD00;">What are the advantages of serverless computing?</mark>

- <mark style="background: #BABD00;">Lower costs</mark> - Serverless computing is generally very cost-effective, as traditional cloud providers of backend services (server allocation) often result in the user paying for unused space or idle CPU time.
- <mark style="background: #BABD00;">Simplified scalability</mark> - Developers using serverless architecture don’t have to worry about policies to scale up their code. The serverless vendor handles all of the scaling on demand.
- <mark style="background: #BABD00;">Simplified backend code</mark> - With FaaS, developers can create simple functions that independently perform a single purpose, like making an API call.
- <mark style="background: #BABD00;">Quicker turnaround</mark> - Serverless architecture can significantly cut time to market. Instead of needing a complicated deploy process to roll out bug fixes and new features, developers can add and modify code on a piecemeal basis.

Learn more about [the benefits of serverless computing.](https://www.cloudflare.com/learning/serverless/why-use-serverless/)

#### <mark style="background: #BABD00;">How does serverless compare to other cloud backend models?</mark>

A couple of technologies that are often conflated with serverless computing are Backend-as-a-Service and Platform-as-a-Service. Although they share similarities, these models do not necessarily meet the requirements of serverless.

<mark style="background: #BABD00;">Backend-as-a-service (BaaS)</mark> is a service model where a cloud provider offers backend services such as data storage, so that developers can focus on writing front-end code. But while serverless applications are event-driven and run on the edge, BaaS applications may not meet either of these requirements. [Learn more about BaaS >>](https://www.cloudflare.com/learning/serverless/glossary/backend-as-a-service-baas/)

<mark style="background: #BABD00;">Platform-as-a-service (PaaS)</mark> is a model where developers essentially rent all the necessary tools to develop and deploy applications from a cloud provider, including things like operating systems and middleware. However PaaS applications are not as easily scalable as serverless applications. PaaS also don’t necessarily run on the edge and often have a noticeable start-up delay that isn’t present in serverless applications. [Learn more about PaaS >>](https://www.cloudflare.com/learning/serverless/glossary/platform-as-a-service-paas/)

<mark style="background: #BABD00;">Infrastructure-as-a-service (IaaS)</mark> is a catchall term for cloud vendors hosting infrastructure on behalf of their customers. IaaS providers may offer serverless functionality, but the terms are not synonymous. [Learn more about IaaS >>](https://www.cloudflare.com/learning/cloud/what-is-iaas/)

#### <mark style="background: #BABD00;">What is next for serverless?</mark>

Serverless computing continues to evolve as serverless providers come up with solutions to overcome some of its drawbacks. One of these drawbacks is cold starts.

Typically when a particular serverless function has not been called in a while, the provider shuts down the function to save energy and avoid over-provisioning. The next time a user runs an application that calls that function, the serverless provider will have to spin it up fresh and start hosting that function again. This start-up time adds significant latency, which is known as a ‘cold start’.

Once the function is up and running it will be served much more rapidly on subsequent requests (warm starts), but if the function is not requested again for a while, the function will once again go dormant. This means the next user to request that function will experience a cold start. Up until fairly recently, cold starts were considered a necessary trade-off of using serverless functions.

Cloudflare Workers has addressed this problem by spinning up serverless functions in advance, during the [TLS handshake](https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/). Since Workers functions spin up at the edge in a very short amount of time, even shorter than the time required to complete the handshake, the result is an [FaaS platform with zero cold starts](https://blog.cloudflare.com/eliminating-cold-starts-with-cloudflare-workers/). To get started with Cloudflare Workers, see our [Developer documentation](https://developers.cloudflare.com/workers/).

As more and more of the drawbacks of using serverless get addressed and the popularity of edge computing grows, we can expect to see serverless architecture becoming more widespread.

# <mark style="background: #BABD00;">Week 3:</mark>

### <mark style="background: #BABD00;">Network Physical Components:</mark>

<mark style="background: #BABD00;">Network Adapter:</mark> A network adapter is the component of a computer’s internal hardware that is used for communicating over a network with another computer. It enable a computer to connect with another computer, server or any networking device over an LAN connection. A network adapter can be used over a wired or wireless network.  

<mark style="background: #BABD00;">Network Router:</mark> Resides at the Network Layer. Data Transmission Form is a Packet. Uses IP address. Used for connecting two or more networks. A router is a networking device that connects a local network to other local networks. Routers connect two or more logical subnets, which do not necessarily map one-to-one to the physical interfaces of the router.  

<mark style="background: #BABD00;">Network Bridge:</mark> A network bridge is a computer networking device that creates a single  aggregate network from multiple communication networks or network segments. This function is called network bridging. Bridging is distinct from routing. Routing allows multiple networks to communicate independently and yet remain separate, whereas bridging connects two separate networks as if they were a single network. In the OSI model, bridging is performed in the data link layer (layer 2).  

<mark style="background: #BABD00;">Network Switch:</mark> Resides at the Data Link Layer. Data transmission form is a Frame. Uses MAC address. Used for connecting two or more nodes in the same network (L2) or different network (L3). A network switch is a computer networking device that is used to connect many devices together on a computer network. A switch is considered more advanced than a hub because a switch will send on a msg to device that needs or request it. Allow connections to multiple devices, manage ports, manage VLAN security settings.  

<mark style="background: #BABD00;">Network Hub (or Repeater):</mark> Also called repeaters — are even less advanced that switches; while a hub broadcasts the same data to all its ports, a network switch forwards data only to those devices that the data is intended for. Network hubs do not manage any traffic coming through them; they only broadcast — or repeat — packets from an incoming port to all other ports.

# <mark style="background: #BABD00;">How HTTPS works:</mark>

[Source for Comic](https://howdns.works/)

Computers and other devices communicate using IP addresses to identify each other on the internet.

Humans can't remember IP addresses, so they use words. e.g. google.com

The domain name system (DNS) brings the two together and gets you to your destination.

The resolver server is usually your <mark style="background: #BABD00;">ISP</mark> (Internet service provider). All resolvers must know where to locate the root server.

The root server knows where to locate the .COM TLD server. TLD stands for Top-Level Domain.

There are 13 root servers that exist today. Root servers sit at the top of the DNS hierarchy.

![](https://i.imgur.com/PNkgGG2.png)

The root servers are scattered around the globe and operated by 12 independent organisations. They are named [letter].root-servers.net where [letter] ranges from A to M.

```
a.root-servers.net 
b.root-servers.net 
.... 
m.root-servers.net
```

This doesn't mean that we have only 13 physical servers to support the whole internet! Each organisation provides multiple physical servers distributed around the globe.

The coordination of most top-level domains (TLDs) belong to the Internet Corporation for Assigned Names and Numbers (ICANN). It is the largest TLD on the internet.

The .COM TLD was one of the first created in 1985.

<mark style="background: #BABD00;">When a user types something into the browser:</mark>
1. The browser checks its cache
2. If the url is not there, it asks the OS
3. The OS checks its cache
4. If the OS does not have the url cached, it asks the resolver to search for the url
5. The resolver checks its cache
6. If the resolver does not have the url cached, it asks the root server
7. The root server does not cache urls but it does know where to find the TLD server and passes this to the resolver
8. The resolver asks the TLD server for the ip address of the server
9. The TLD server will return either the ip address or the nameservers of the url
10. The resolver asks the name server for the ip address it resolves to 

### <mark style="background: #BABD00;">How HTTPS works:</mark>

<mark style="background: #BABD00;">HTTPS:</mark> HyperText Transfer Protocol Secure
[Source for Comic](https://howhttps.works/why-do-we-need-https/)

<mark style="background: #BABD00;">We need HTTPs for 3 reasons:</mark>
- Privacy
- Integrity
- Innovation

When you browse to a website without HTTPS, anyone on your network can sniff your traffic

Integrity is needed so that your traffic cannot be changed by malicious actors. This is often called a man-in-the-middle attack. Integrity means that the message is not manipulated on the way to its destination.

Identification means that I can check that this message is coming from the correct entity. A digital signature attached to a message can identify the sender.

And when you are browsing the web, identification means that the site that you are visiting is indeed the one you think it is.

HTTPS, via SSL certificates, ensures you are connected exactly with the receiver you would expect.

HTTPS needs a way to provide privacy, integrity, and identification on the web. That mechanism is called 'encryption'.

<mark style="background: #BABD00;">Symmetric encryption:</mark>
- One key used to encrypt data
- Anyone with the key can open the box
- the data is scrambled through a series of steps.
- It was transformed and spread out multiple times. Each time obfuscating the message further.
- To decrypt a message, we just need to apply the same steps, but in reverse order.
- The encryption key is mixed in with the message, so even if you know the encryption algorithm, without the key, the message is still nonsense.
- One main issue with symmetric keys is that they are hard to share safely.

![](https://i.imgur.com/0mXDfah.png)

![](https://i.imgur.com/owCsIMt.png)

<mark style="background: #BABD00;">Asymmetric keys:</mark>
- you have 2 keys.
- One key is public, the other one is private. They are paired and work together.
- Only the private key can open a box locked with the public key pair.
- This is great not only for privacy, but also for identification since we know for sure that only the owner of the 2 keys can open the message.

When you view a website with https, your browser will display a lock on the address bar.
- Your browser communicated with a server, where the website is hosted, and they both established a secure connection to transmit messages.
- They needed to agree on how to communicate securely. If the negotiation is not successful, your browser lets you know by showing an error or warning.
- If an agreement is reached, your browser is happy to display a padlock on the address bar.

This process, the negotiation between a browser and a server, is called 'the handshake'.

<mark style="background: #BABD00;">The handshake:</mark>
1. <mark style="background: #BABD00;">Client Hello:</mark> The client sends a list of SSL/TLS versions and encryption algorithms that it can work with to the server.
2. <mark style="background: #BABD00;">Server Hello:</mark> The server chooses the best SSL/TLS version and encryption algorithm among the ones the client sent it, and based on its preferences. The server replies with its certificate, which includes its public key, so the client can verify who the server is.
3. <mark style="background: #BABD00;">Client Key Exchange:</mark> The client checks the server's certificate to make sure they are legit. The client generates a 'pre-master key' so they can both use it later when they generate a unique key. The client encrypts that pre-master key with the server's public key and then sends it.
4. <mark style="background: #BABD00;">Change cipher spec.</mark> The server uses its private key to decrypt the pre-master key. Now they both generate the same 'shared secret' that they are going to use as a symmetric key. The client sends a test and the server responds.

When the exchange of data is encrypted with SSL/TLS, then we call it HTTPS. The 'S' stands for Secure.

<mark style="background: #BABD00;">SSL</mark> stands for 'Secure Sockets Layer'. A protocol created by Netscape in 1995.

Netscape gave control of SSL protocol to the IETF: Internet Engineering Task Force. Before 1999 ended, IETF released TLS version 1.0 (Which was really SSL 3.1).

SSL was renamed to <mark style="background: #BABD00;">TLS:</mark> Transport Layer Security.

<mark style="background: #BABD00;">A certificate authority (CA) is a third-party organization with 3 main objectives:</mark>
1. Issuing certificates.
2. Confirming the identity of the certificate owner.
3. Providing proof that the certificate is valid.

Becoming a CA is an intense task of security requirements and audits. You need to be trusted to be accepted into a root store - a database of trusted CAs

Apple, Windows, and Mozilla run their own root stores that they pre-install in your computer or device.

<mark style="background: #BABD00;">Three types of CA:</mark>
- <mark style="background: #BABD00;">Domain validated:</mark> The certificate just verifies the domain name, and nothing else. 
- <mark style="background: #BABD00;">Organization validated:</mark> The certificate requires the validation and manual verification of the organization behind the certificate.
- <mark style="background: #BABD00;">Extended validation.</mark> The certificate requires an exhaustive verification of the business.

All valid certificates result in the browser displaying a secure badge in the browser bar. EV certificates generally display the company name as well.

When a CA issues a certificate, they sign the certificate with their root certificate pre-installed in the root store. Most of the time it's an intermediate certificate signed with a root certificate.

![](https://i.imgur.com/2t8fp3E.png)

If the root certificate is compromised, it's easier to revoke the intermediate certificates, since the root certificates are installed on each device.

### <mark style="background: #BABD00;">SAN: What is LUN?</mark>

[Source](https://www.purestorage.com/knowledge/what-is-lun-storage.html)

It’s common for servers to have multiple storage devices. A logical unit number (LUN) assigns a unique value to each drive. A LUN can be assigned to a group of drives configured as a single volume, a partition on a drive, or the entire drive itself. A LUN value can be automatically assigned or manually assigned by an administrator. In this article, we take a look at how LUNs work and the benefits and downsides of using them.  

#### <mark style="background: #BABD00;">What Is a LUN in Storage?</mark>

A LUN (logical unit number) is a unique identifier that defines a storage partition in a [storage area network (SAN)](https://www.purestorage.com/knowledge/what-is-storage-area-network.html) environment for data organization and access. It’s important to note that a LUN is a component in storage organization and not a type of storage device itself. A LUN is a numeric value that points to a physical disk or a logical set of disks. Storage LUNs can also point to a logical set of partitions.

The purpose of a LUN is for clients to make requests from storage space and retrieve data. Usually, LUNs refer to SAN storage, so client computers can map network drives, request data from network storage, or store data on the SAN. Users do not address a LUN when mapping a drive, so only administrators manage LUN identifiers.

#### <mark style="background: #BABD00;">How Does a LUN Work?</mark>

When you build a new server or add a drive to a server, you must partition it. Partitioning forces you to choose a file system. You can choose to make the entire drive space a part of the partition, use only some of the drive space for a partition, or create a logical volume from a group of drives. A LUN can be assigned to the new partition or a set of partitions.

When a server has several disks configured as a RAID (redundant array of independent disks) on SCSI (Small Computer System Interface) ports, the server uses a LUN to communicate with the right storage unit. LUN assignment is common with SCSI disks, but a storage area network (SAN) with other storage ports (e.g., SATA or SAS) could be configured as a RAID and connected via a Fibre Channel where a LUN is assigned.

For a user, the LUN is seen as a single-mounted storage device even if several partitions or a RAID of disks represent a single LUN. A server accessing internal storage needs the LUN to identify the right disk to read to or write from. LUNs assigned to a SAN are necessary for client computers to mount the right disk and assign it a name (e.g., X or Z as a drive letter).

It’s possible for a single LUN to identify thousands of logical volumes, especially in a SAN environment. Administrators can assign a LUN to SAN volumes or the SAN unit can automatically assign a LUN to storage. LUNs can be reassigned by administrators later after bootup to customize configurations to meet certain setup requirements.

#### <mark style="background: #BABD00;">Alternatives and Implementations of LUN Storage</mark>

Every server or network storage device has a LUN so that operating systems can identify a volume to read or write to disks. For many enterprise environments, large network storage devices use RAID storage, which means that several disks could be represented by a single LUN. A large SAN with several disks configured as a single volume could also have a single LUN.

Unless you use older [SCSI technology](https://blog.purestorage.com/purely-technical/iscsi-setup-with-flasharray/) on your personal computer, you only find LUN storage in older SAN or server hardware. Newer SATA (Serial Advanced Technology Attachment) drives are used in servers and personal computers, but SCSI was replaced with SAS (Serial Attached SCSI) or [iSCSI](https://blog.purestorage.com/purely-informational/iscsi-vs-fc-vs-fcoe-choosing-the-right-storage-protocol-for-your-business/) (Internet Small Computer System Interface). Enterprise systems may use SATA or SAS depending on the type of storage and speeds necessary to support a large volume of read and write requests.

#### <mark style="background: #BABD00;">Benefits of Using LUN Storage</mark>

Although a LUN represents some or all of a disk’s storage capacity, it does not always represent a single disk. LUN management software lets administrators choose LUN values for specific disks or volumes, but counting the number of LUN storage values does not represent the total number of disks. The operating system on the remote computer using the LUN can mount it as a drive, so the storage can be given a user-friendly name, usually a letter (e.g., Z drive or X drive).

LUN management lets administrators better control SAN disks and capacity. Enterprise networks use several large-capacity drives to hold petabytes of data, and a LUN lets a workstation mount a single LUN as a user-friendly drive letter. These drive letters often have logical organization (e.g., storage for accounting or sharing documents company-wide) with user-friendly volume letters that most employees know when they transfer documents to network drives.

Although a LUN enables mounting drives and resource sharing on a local device, it does not offer any security. Administrators are still responsible for creating user groups and assigning appropriate permissions to each user group for data access control. Most organizations assign a different drive letter to each user group so there’s no confusion for employees about the purpose of each mounted drive. For example, the X drive might be used for sharing files with anyone within the organization, while the Z drive might represent a link to personal file spaces that only a single employee can access.

#### <mark style="background: #BABD00;">Potential Downsides of a LUN</mark>

A LUN is a numeric assignment for SCSI or a Fibre Channel, but a LUN is often associated with a SAN using a RAID system. A standard user will not run into LUN assignments, but administrators working with legacy hardware might find LUN management challenging. Remember that a LUN represents a slice of storage in a SAN, but it does not always represent a single disk or partition. LUN assignments can be manual or automatic, but most administrators use SAN software to manage LUN values.

Any downsides to LUN are management related. Initial setup might be somewhat convenient, but any new space added to the SAN must be given a LUN or added to existing volumes so that current storage capacity can be expanded. Some administrators might struggle to add new disks to a LUN depending on the operating system and SAN configuration. Most operating systems have an interface to make it somewhat convenient to add storage to current capacity, but administrators might find that they need to troubleshoot when new disks aren’t recognized by the system.

LUNs aren’t always assigned in a SAN or NAS environment. RAID volumes can also exist on a physical server where administrators can assign a LUN. An operating system running on a virtual machine can also use a LUN. Administrators should create a LUN strategy to ensure that reads and writes are optimized for performance. Too many applications and users writing to the same LUN can cause performance degradation, so ensure that LUNs are assigned with performance in mind.

#### <mark style="background: #BABD00;">Conclusion</mark>

Logical unit numbers (LUNs) play an indispensable role in the realm of block storage, serving as a pivotal link between physical storage resources and the data they hold. As we've explored, LUNs facilitate the efficient and flexible allocation of storage space, allowing for the dynamic management of data in various environments, from small-scale setups to large data centres. 

Administrators working with enterprise solutions might find themselves working with LUN management, typically in a large SAN environment. For systems that use SCSI RAID environments, LUN assignment is a component in mounting drives on servers and client workstations. 

Understanding LUNs is just one piece of knowledge crucial for anyone involved in storage administration or data management as it provides the foundational knowledge required for efficient storage utilization and data retrieval. The management and support of your storage infrastructure can consume precious IT resources. Learn how [Pure Professional Services](https://www.purestorage.com/services.html) can help reduce the administrative overhead of managing your storage arrays.