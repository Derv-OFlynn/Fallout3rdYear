#CloudComputing

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
