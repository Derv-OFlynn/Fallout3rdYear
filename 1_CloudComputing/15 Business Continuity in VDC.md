### <mark style="background: #BABD00;">Overview:</mark>

BC planning should include end-to-end protection of both physical and virtual resources at Compute, storage, and network layers

Ensuring BC mainly involves redundancy of components at each layer

BC technology for data protection includes Backup and replication of data (similar to CDC environment)

Besides traditional approaches, VDC environment has additional BC solutions typically implemented at the compute layer.

In a VDC environment, technology solutions that enable the Business Continuity (BC) process need to protect both physical and virtualized resources. This protection should include resources at all the layers including compute, storage, and network. Ensuring BC in a VDC environment involves consistent copies of data and redundant infrastructure components.  

BC solutions for physical network and storage are the same as those for the Classic Data Centre (CDC) environment. This module focuses on the BC solutions for virtual resources built upon compute infrastructure including VMs and their data.

Whole point is to provide robustness no matter what disaster occurs.

### <mark style="background: #BABD00;">Advantages of Compute Virtualisation in BC:</mark>

Hardware independence

Cross platform compatibility

Mutual isolation. Different BC policies may be applied to different VMs, even if they are running on the same physical server

Encapsulation of complete computing environment

Relatively robust BC processes. Comparatively easier to maintain VM copies in diverse geographic locations

Higher data availability

Virtualization considerably simplifies the implementation of a BC solution in a VDC environment. For example, VMs have inherent properties that facilitate the planning and implementation of a BC strategy:  
- VMs are compatible with standard x86 architectures and run independent of the underlying x86 hardware configurations. Therefore, BC solutions for VMs need not consider the details of the x86 hardware available at the failover site. In this module, the term compute hardware term is used to represent x86 hardware.  
- VMs are isolated from each other, as if physically separated, even if they run on a single physical server. This isolation prevents failure of one VM from spreading over to other VMs. Different DR policies may be applied to different VMs, even if they are running on the same physical server.  
- VMs encapsulate a complete computing environment. Therefore, they can be moved and restarted easily, compared to recovery of physical servers in a CDC.  

It is also comparatively easier to maintain VM copies in diverse geographic locations, which makes the BC process robust. Similarly, data maintained within a VDC has higher availability.  

Restoring of data after an outage in a VDC is faster and more reliable, compared to CDC.

### <mark style="background: #BABD00;">Single point of failure in a VDC:</mark>

Most important thing is to eliminate all single points of failure.

<mark style="background: #BABD00;">SPOF in Compute Infrastructure:</mark>
- Physical server and hypervisor
- VM and guest OS

<mark style="background: #BABD00;">SPOF in Storage Infrastructure:</mark>
- Storage Array and its components
- Virtual disks

<mark style="background: #BABD00;">SPOF in Network Infrastructure:</mark>
- Network Components
- Virtual network

<mark style="background: #BABD00;">Site:</mark>

To plan for an effective BC solution in a VDC, administrators need to identify potential single point of failure (SPOF). In a VDC, the SPOF includes the following:  

<mark style="background: #BABD00;">SPOF in Compute Infrastructure:</mark>  
- Physical Server: Failure of a physical server would result in the failure of complete virtualised infrastructure running on it. Similarly, failure of a hypervisor can cause all the running VMs and virtual network, which are hosted on it, to halt.  
- VM: Failure of a VM might result in the failure of the critical applications running on it. If there are (distributed) applications running across multiple VMs (for example an electronic banking application), failure of a VM might cause disruptions in the execution of distributed or dependent applications on other VMs. Similarly, the failure of a Guest OS might cause critical applications to stop executing, which would consequently cause disruptions in the client services.  

SPOF in Storage Infrastructure: 
- Failure of a storage array and its components might cause disruptions in the operations of hypervisor, VMs, and applications accessing data from that array.  
- Apart from physical storage, virtual disks are also subject to potential failure. However failures in virtual disks are often due to errors in VMFS, which would be either due to incorrect operation of an hypervisor or a security attack on the file system itself. Failure in VMFS or virtual disk would impact all the applications in the associated VMs.  
- SPOF in Network Infrastructure: Based upon the underlying network infrastructure – SAN, NAS, or converged network type (for example, FCoE, IP SAN, etc.) – the supporting components (NICs, communication paths, interconnect device, etc.) might fail and thus disrupt communication between the devices. Apart from physical network component, virtual network is also subject to potential failures. These failures in a virtual network could be due to incorrect design, the configuration of the applications realizing these virtual components, or due to security attacks on these applications.  
- Failure in a virtual network component results in the disruption of communication between the VMs using that component for their communication.  

<mark style="background: #BABD00;">Site:</mark> 
- Failure of a VDC site due to a disaster could have significant impact on business operations and thus need special consideration in terms of detailed disaster recovery planning and testing.

### <mark style="background: #BABD00;">Eliminating Single Point of Failure:</mark>

![](https://i.imgur.com/CpWNb8a.png)

To mitigate SPOFs identified before, VDC components are often designed with redundancy so that the system fails only if all the components, including the redundant components, fail simultaneously. Such a failure is very unlikely to happen except during catastrophic disasters.  

Redundancy ensures that the failure of a single component does not affect the availability of the corresponding operations.  

Because of the large number of components involved in the overall operation of a VDC and their underlying complexity and interactions with each other, a careful analysis need to be performed to eliminate every SPOF. In the diagram, critical enhancements in the infrastructure of a VDC to mitigate SPOF is illustrated. Note that many of the employed mechanisms are similar to a CDC environment:  
- Configuration of multiple HBAs to mitigate single HBA failure.  
- Configuration of multiple fabrics to account for a switch failure.  
- Configuration of multiple storage array ports to enhance the storage array’s accessibility.  
- RAID configuration to ensure continuous operation in the event of disk failure.  
- Implementation of a storage array at a remote site to replicate data for mitigating the effect of local site failure.  
- Configuration of multiple copies of virtual disks and VM configuration files.  
- Implementation of server clustering.  
- A fault-tolerance mechanism whereby two VMs in a cluster access the same set of storage volumes. If one of the VMs fails, the other takes up the complete workload.

### <mark style="background: #BABD00;">Protecting Compute: Clustering:</mark>

![](https://i.imgur.com/eU8bROe.png)

<mark style="background: #BABD00;">Clustered Servers:</mark>
- Groups Of physical servers are combined and managed as an aggregated compute resource pool
- Provides protection from server and hypervisor failures

One of the important techniques to protect compute infrastructure, for providing high availability of VMs and their data in a VDC environment, is clustering.  

<mark style="background: #BABD00;">Clustered Servers:</mark> Virtual Infrastructure provides the technology to combine groups of physical servers and manage them as an aggregated compute resource pool. These resource pools are an ideal way to abstract the underlying physical servers and present only the logical capacity to the user. Additionally, clustered servers provide an effective way to ensure compute resource availability in the event of a physical server or hypervisor failure. For example, as depicted in the diagram on this slide, if a server fails, all the VMs running on it are failed over (moved) to other servers, which are operational (active) at that time.  

Clustered servers use a clustered file system, such as VMFS, to enable failover.  

VMFS provides multiple VMs with shared access to a consolidated pool of clustered storage. A VM sees the (virtual) disks in a VMFS as local targets, where as are actually just files on the VMFS volume. Additionally, a VMFS encapsulates the entire VM state in a single directory, making the tasks of backup, replication, and migration of VMs easy. VMFS is implemented over CS and allows each hypervisor in the cluster to store its VM files in a specific subdirectory on the VMFS. When a VM is operating, VMFS locks those files so that other hypervisors cannot update them. VMFS, thus ensures that a VM cannot be opened by more than one hypervisor at the same time. VMFS also provides each VM a separate isolated directory structure for storing its files so that files belonging to one VM cannot be accessed by other VMs.

### <mark style="background: #BABD00;">Proctecting Compute: VM Fault Tolerance:</mark>

Uses a secondary VM running on another physical machine as a live copy of the primary VM

<mark style="background: #BABD00;">The two VMS remain in synchronisation:</mark>
- Event logs of the primary are transmitted to the secondary
- Received event logs are replayed by the secondary

![](https://i.imgur.com/YztHP1J.png)

The VM Fault Tolerance (VMFT) technique ensures that in the event of a VM failure, there is no disruption in business operations. The VMFT technique ensures that individual VMs are functioning well and are responding to failures without interruption in service. VMFT creates hidden duplicate copies of each VM so that when it detects that a VM has failed due to hardware failure, the duplicate VM can be used for failover.  

VMFT creates a live instance of the primary VM that runs on another physical machine. The two VMs are kept in synchronization with each other. The logs of the event executions by the primary VM are transmitted over a high speed network to the secondary VM. 

Secondary VM replays them to bring its own state same as of the primary VM. The hypervisor running on the primary server captures the sequence of events for the primary VM, including instructions from the virtual I/O devices, virtual NICs, user inputs, etc. And transfers them to the secondary server. The hypervisor running on the secondary server receives these event sequences and sends them to the secondary VM for execution. The primary and the secondary VMs share the same virtual disk using VMFS, but all output (for example, write) operations are performed only by the primary VM. A special locking mechanism ensures that the secondary VM does not perform write operations on the shared virtual disks. Any other output instructions from the secondary VM are also not allowed. The hypervisor posts all events to the secondary VM at the same execution point as they occurred on the primary VM. This way, the two VMs play exactly the same set of events and their states are synchronized with each other.

### <mark style="background: #BABD00;">Protecting Storage:</mark>

<mark style="background: #BABD00;">RAID:</mark> Provides data protection against drive failures

<mark style="background: #BABD00;">Hot spare:</mark> 
- Is a standby disk drive in a RAID array
- Temporarily replaces a failed disk drive without disrupting the compute access

<mark style="background: #BABD00;">Redundant components:</mark>
- Array controllers
- Ports in a storage array
- Storage arrays

The key techniques for protecting storage in a VDC are similar to the ones used in CDC, including:  
- <mark style="background: #BABD00;">RAID:</mark> As explained earlier, RAID is an enabling technology that leverages multiple drives as part of a set to provide data protection against drive failures. For example, RAID uses mirroring and parity techniques to rebuild the data after a disk drive fails.  
- <mark style="background: #BABD00;">Hot spare:</mark> A hot spare refers to a spare disk drive in a RAID array that temporarily replaces a failed disk drive of a RAID set. A hot spare takes the identity of the failed disk drive in the array. When the failed disk drive is replaced with a new disk drive, either the hot spare replaces the new disk drive permanently, or the data from the hot spare is copied to it. The hot spare returns to its idle state and is used to replace the next failed drive. Multiple hot spares can be used to provide higher data availability.  

<mark style="background: #BABD00;">In addition to RAID architecture and hot spares, high availability design for storage infrastructure is achieved by using: </mark> 
- Redundant array controllers to address primary array controller failures  
- Redundant ports in a storage array if one of the currently active port fails  
- Redundant storage array when the whole array goes down

### <mark style="background: #BABD00;">Protect Network:</mark>

Protecting physical network by using redundancy
- Interconnect devices with redundant hot swappable components
- Redundant links and multipathing
- Redundant NICs and NIC teaming

<mark style="background: #BABD00;">Protecting virtual network: Failure in a virtual network on a hypervisor may be the result of:</mark>
- Software error or security attack
- Physical server failures

Virtual network failure is not common

The following are the techniques to protect external physical network:  
- <mark style="background: #BABD00;">Interconnect devices with redundant hot swappable components:</mark> Allows the user to add or remove components while the interconnect device is operational.  
- <mark style="background: #BABD00;">Redundant links and multipathing:</mark> A technique to enable multiple paths for accessing the same storage device for I/O operations so that in case of a failure of one path, dynamic failover to an alternate path is possible.  
- <mark style="background: #BABD00;">NIC teaming:</mark> Grouping of two or more physical NICs into a single logical device.  

Apart from the protection of external physical network, another important aspect is to protect the virtual network (running on a single server or hypervisor) from failure. A virtual network failure may be caused either by an incorrect operation of the software components (for example, virtual NIC, virtual Switch) or because of the failures in the compute infrastructure, for example, physical server going down, or hypervisor, or VM crashes. 

In general, failures due to software errors or security attacks require software patches from hypervisor vendors. The second reason is more often a cause for the failure in a virtual network. 

Therefore, the methods to protect compute infrastructure, as discussed earlier, equally apply for protecting such virtual network as well.  

The discussion in this lesson will focus on protecting physical network infrastructure using the techniques mentioned above.

### <mark style="background: #BABD00;">Protecting Network: NIC Teaming:</mark>

Enables failover in case of physical NIC failures/link
outages. Supports the IEEE 802.1AX-2008 link aggregation standard

<mark style="background: #BABD00;">VMS unaware of the underlying physical NICs:</mark>
- Packets sent to the logical NIC team are dispatched to one of the physical NICs
- Packets arriving at any of the physical NICs are automatically directed to the appropriate virtual NIC

![](https://i.imgur.com/GzGMp0Z.png)

NIC teaming allows grouping of two or more physical NICs - which may be of different types—into a single logical device called the NIC team. After an NIC team is configured, the VM will not be aware of the underlying physical NICs. 

Packets sent to the NIC team are dispatched to one of the physical NICs in the group. Packets arriving at any of the physical NICs are automatically directed to the NIC team, which consequently redirects them to the designated virtual NIC.  

Apart from load balancing, which was discussed earlier, NIC teaming enables fault tolerance such that if one of the underlying physical NICs fails or its cable is unplugged, the traffic is redirected to another physical NIC in the team. 

Thus, NIC teaming eliminates the SPOF associated with a single physical NIC. Such failover remains totally transparent to the VMs and applications may experience performance degradation during this process.  

In a VDC environment, with the hypervisor’s support for NIC teaming, a guest OS or a VM need not install separate drivers for NICs or configure NIC teaming. NIC teaming implementations in most of the hypervisors support the IEEE 802.1AX-2008 link aggregation standard.

### <mark style="background: #BABD00;">Protection from Site Failure:</mark>

In case of a regional disaster, the whole VDC site requires recovery

<mark style="background: #BABD00;">Automatic site failover capability is highly desirable:</mark>
- Manual steps are often error prone
- Reduces RTO (Recovery Time Objective)

"Bare-metal" (Type l) hypervisor running directly on the physical compute is the preferred choice of configuration

Offers greater levels of performance, reliability, and security during site failover

<mark style="background: #BABD00;">Site failover depends upon:</mark>
- VM migration capability, 
- reliable network infrastructure,
- data backup
- replication functionality

In case of a regional disaster, the whole VDC site requires recovery. To ensure error-free execution of BC solutions during a disaster, a non disruptive testing of Disaster Recovery (DR) plan is often required to be carried out beforehand.  

To ensure a robust and consistent failover in case of a site failure or during testing, automatic site failover capabilities are highly desirable. This is because manual steps are often error prone. RTO <mark style="background: #BABD00;">(Recovery Time Objective)</mark> with automated failover is significantly less compared to the manual process. However, the DR product that automates setup, failover, and testing of DR plans must be compatible with the guest OS.  

A hypervisor provides robust, reliable, and secure virtualisation platform that isolates applications and OSs from their underlying hardware. This considerably reduces the complexity of implementing and testing DR strategies. 

Among the different types of hypervisors for BC, the “bare-metal” (Type 1) hypervisor provides a robust DR. During the DR process, the bare-metal approach offers greater levels of performance, reliability, and security; and is better equipped to leverage the power of x86 server architectures found in the datacentres.  

A VDC site failover process also depends upon other capabilities, including VM replication and migration capabilities, reliable network infrastructure between primary (production) site and the secondary (recovery or DR) site, and data backup capabilities

### <mark style="background: #BABD00;">Backup in a VDC: An overview:</mark>

<mark style="background: #BABD00;">VM backup includes:</mark>
- Virtual disks containing system and application data
- Configuration data including network and power state

<mark style="background: #BABD00;">Backup options:</mark>
- File based
- Image based

<mark style="background: #BABD00;">Backup optimisation:</mark>
- Deduplication

De-duplication is when a backup software identifies duplicate files and stores only one copy of it in order to minimise storage use.

A backup operation in a VDC environment often requires backing up the VM state. The VM state includes the state of its virtual disks, memory (i.e. RAM), network configuration, as well as the power state (on, off, or suspended). A virtual disk includes all the information typically backed up (OS, applications, and data.) As with physical machines, a VM backup needs to be periodically updated with respect to its source, in order to recover from human or technical errors.  

A VM backup may be performed either as a “set of files” retaining the directory structure or as a complete image. File-level backup provides a way to access individual files, whereas image level backup does not. Another important difference between file based and image based backup is that an image based backup is independent of the guest OS running on the VM, whereas file based backup may have guest OS dependency, owing to file system structure. In the case of an image based backup, recovery of individual files requires additional operations to be performed.  

Owing to the increased capacity requirements in a VDC environment, backup optimization methods are necessary. Deduplication, which aims to reduce duplication of backup data, is one of the important techniques towards achieving optimum backup.

### <mark style="background: #BABD00;">Backup in a VDC:</mark>

<mark style="background: #BABD00;">Compute based - Backup VM as a physical server:</mark>
- Requires installing a backup agent on a VM
- Can only backup virtual disk data

<mark style="background: #BABD00;">Backup VM files:</mark>
- Requires installing backup agent on hypervisor
- Cannot backup LUNS directly attached to a VM

<mark style="background: #BABD00;">Array based:</mark> Uses snapshot and cloning techniques

![](https://i.imgur.com/CyMzrRm.png)

Traditional approaches for backup in a VDC environment use the same technologies as are used in a CDC, with minor modifications. These approaches often treat a VM as a set of files while creating its backup. The approaches are as following:  
- <mark style="background: #BABD00;">First approach:</mark> A VM is treated as if it were a physical server. A backup agent is installed on the VM that streams the VM data to the backup server. Management of the backup operation is similar to that of CDC, and hence, creating application consistent backups is easy. It is also possible to restore specific files to the guest OS. However, this solution requires the management of agents on all VMs. Note that the solution does not capture the VM files (i.e., Virtual BIOS file, VM swap file, Virtual disk file, Log file, and Configuration file). So, in the event of a restore, a user should manually recreate the VM and then restore data into it.  
- <mark style="background: #BABD00;">Second approach:</mark> Since a VM’s virtual disks are nothing but a collection of files, it is possible to simply back them up by performing a file system backup from a hypervisor.  This is a relatively simple method because it requires only an agent on the hypervisor, and that backs up all the VM files. However, LUNs assigned directly to a VM (using RDM) cannot be backed up using this approach.  
- <mark style="background: #BABD00;">Third approach:</mark> It uses array based technologies to backup a VM and utilizes the storage subsystem for backup operations. These technologies often use snapshot and cloning techniques to capture and backup a VM. Snapshot and cloning of a VM will be discussed in the next lesson.

### <mark style="background: #BABD00;">Backup Considerations in a VDC:</mark>

<mark style="background: #BABD00;">Reduced computing resources:</mark> Existence Of multiple VMS running on the same physical machine leaves fewer resources available for backup process

<mark style="background: #BABD00;">Complex VM configurations:</mark>
- A backup agent running on VM has no access to VM configuration files
- Not possible for a backup agent running on hypervisor level to access storage directly attached to a VM using RDM

In a VDC environment, a single physical machine can run multiple VMs, that increases server utilisation. This results into reduced compute resources available for backup and recovery tasks.  

Apart from the increased capacity requirements and reduced computing resources, backing up a VM is more complex than backing up a physical machine. With a physical machine, the OS manages all the files on the machine. In a virtual environment, the guest OS is encapsulated in a VM that is managed by the hypervisor. Because of this architecture, there are files related to a VM; however, the VM does not have any direct access to these files; for example, the VM configuration files. In the case of RDM (Raw Device Mapping), where storage is directly attached to a VM, an application running on the hypervisor level will have difficulty while accessing that LUN.  

These factors render backup processing more challenging in a VDC as compared to CDC (Classic Data Centre).

### <mark style="background: #BABD00;">Restoring a VM:</mark>

Restore VM to a required state using the backup Selection of the restore point depends upon RPObjective

Steps for restore process
- Selection of VM and virtual disks to restore from backup
- Selection Of the destination
- Configuration settings

Restoring a VM may take significantly fewer steps, compared to recovering a physical machine.

![](https://i.imgur.com/mu3dvbL.png)

A restore process returns a VM to a selected previous state using the backup copies.  

Selection of the restore point actually depends upon the choice of the RPO.  

<mark style="background: #BABD00;">The key steps involved in the restore process include:</mark>  
1. Selection of the VM and virtual disks to be restored from the backup.  
2. Selection of the destination location for the restoration: In case of an actual VM failure, the original physical machine itself is selected as a destination, whereas for restore rehearsal purposes, some alternate physical machine is selected.  
3. Configuration settings: This includes deciding VM configuration settings either by using the existing backup or by applying new settings.  

Restoring a VM may take significantly fewer steps, compared to the recovery of physical machines. Therefore, recovery time requirements for a VM and consequently for the whole VDC are relatively shorter, compared to the CDC environment.

### <mark style="background: #BABD00;">VM Replication in VDC:</mark>

VM replication is a critical requirement for successful BC

VM replication is performed at the hypervisor level Relies upon replication software to propagate changes made to a VM's virtual disk

To ensure data integrity, quiescing of VM is necessary before replication process starts
- Quiescing pauses currently running applications within a VM and forcibly flushes all data in the memory to the disk
- To achieve application-level consistency, is performed at the application level
- Applications complete any pending transactions and write the pending data to the disk

VM replication is a critical requirement for successful BC and DR processes in a VDC. This is because, in a VDC environment, to restart operations, a user needs to primarily restart VMs on the secondary (backup) site. VM replication makes this possible by making the copies of these VMs available at the backup site. VM replication is performed at the hypervisor level and relies on replication software that can copy all the changes made to a VM disk to another server. VM replication requires a secondary site which is up and a network connectivity linking these sites.  

A virtual disk snapshot taken at the hypervisor level temporarily redirects incoming writes to a separate delta file. The delta file maintains these I/Os to be written to the virtual disk after the snapshot is taken. The virtual disk is then mounted by the replication software and any updates since the last replication cycle are copied to another identical virtual disk on a VM at the secondary site.  

To ensure data integrity, quiescing of VM is necessary before the replication process starts. Quiescing pauses currently running applications within a VM and forcibly flushes all data in the memory to the disk. To ensure application-level consistency, applications (for example, Microsoft Exchange or SQL Server) are instructed to complete any pending transactions and write the pending data to the disk.

### <mark style="background: #BABD00;">VM Replication Methods:</mark>

<mark style="background: #BABD00;">Compute based replication:</mark>
- Enables replicating VMS between dissimilar storage; for example, from a local disk drive to a storage array in a different location
- Creates VM snapshot, or VM Template.

There are two main methods to replicate VMs. The first approach uses compute based replication. In this method, replication happens between similar/dissimilar storage devices.  

For example, using compute based replication, a VM is replicated from a local disk drive to a storage array in a different location. Compute based replication creates either a VM snapshot, or a VM clone, or a VM template – these will be discussed next.  

Another method is to use storage array to replicate the VM either to an array at the primary site itself or to a remote array (for example, iSCSI, or Fibre channel, or NAS storage array) at the secondary site. This method is similar to the traditional array based replication method used in a CDC. It works by copying LUNs of the source VM to the target array. Replication to a remote array may be either synchronous or asynchronous.

### <mark style="background: #BABD00;">VM Snapshot:</mark>

Preserves the state and data of a VM at a specific point-in-time State includes VM configuration files as well as its power state (on, Off, suspended)

Data includes all the files that makeup the VM including memory, and other devices, such as virtual NIC

A log file captures the changes to the virtual disk after snapshot is taken

![](https://i.imgur.com/MAyLCcF.png)

A snapshot preserves both the state and data of a VM at a specific point in time. State includes VM files such as BIOS, network configuration, and its power state (powered-on, powered-off, or suspended). Data includes all the files that makeup the VM, including virtual disks, memory, and other devices. In this method, instead of making a copy of the entire virtual disk of the VM, which may be very large in size, a snapshot is created. A snapshot includes a separate log file which captures the changes to the virtual disk of the VM since the snapshot was taken.  

Referring to the diagram on this slide, the first snapshot of the VM is taken at time-point  13:00 (on date dd/mm/yyyy) and the second snapshot is taken after two hours at time-point 15:00. These snapshots are saved with unique names and details of the points-in-time, when they are created.

### <mark style="background: #BABD00;">VM Template:</mark>

A master copy to create and provision new VMS

A reusable image created from a VM Includes virtual hardware components, an installed guest OS, and software applications

<mark style="background: #BABD00;">Created in two ways:</mark>
- Convert a powered-off VM into a template
- Clone a VM into a template

<mark style="background: #BABD00;">Increase efficiency, consistency, and standardisation:</mark>
- Repetitive installation and configuration tasks can be avoided
- Deploying VMS from VM templates helps to enforce standards

A VM template is a reusable image created from a VM. The VM template works like a master copy of a VM to be used for creating and provisioning new copies of the VM. The template typically includes virtual hardware components, an installed guest OS (with any applicable patches), and software applications.  

Templates can be created in two ways, either by converting a powered-off VM into a template or by cloning a VM to a template. The advantage of converting a VM to a template is that the conversion is instantaneous. However, the template will not be used immediately.  

Cloning a VM to a template leaves the original VM intact, but will require waiting for the entire capacity of the VM to be duplicated into the template’s files.  

A template differs from a clone because new VMs are deployed from templates. From a clone, only additional cloning can be done to create new VMs. However the new VMs which are created out of a Clone will reflect the changed state of the clone as compared to a VM  
template which preserves the original state.  

<mark style="background: #BABD00;">Key advantages of the VM template include the following:</mark>
- VM templates increase efficiency; for example, with templates, many repetitive installation and configuration tasks can be avoided.  
- VM templates are also used to enforce consistency and standards. Deploying from templates helps to enforce standards such as including antivirus and management software in any machine connected to the network.

### <mark style="background: #BABD00;">VM Migration:</mark>

Moving a VM from one hypervisor to another hypervisor
- For example: hypervisor failure or scheduled hypervisor or storage array maintenance

<mark style="background: #BABD00;">Migration process:</mark>
- Involves movement of entire active state of a VM
- In case of server-to-server migration, virtual disks are not moved within clustered servers
- VM in the source hypervisor needs to be deleted after migration is complete

There are many situations where moving a VM from one hypervisor to another is necessary.  

The primary purpose is to achieve BC in case of hypervisor failure. Another situation might involve load balancing when one hypervisor is running many VMs but another hypervisor is relatively less occupied. Yet another reason might involve facilitating scheduled hypervisor or storage array maintenance.  

The process of moving VMs from one (source) hypervisor to another (target) is known as VM Migration. There are primarily two different types of VM migrations:  
- <mark style="background: #BABD00;">Server-to-server migration:</mark> This type of VM migration involves moving a VM from one hypervisor to another using a client (migration agent software) running on these hypervisors. The receiving hypervisor may be remotely located in a different data center.  
- <mark style="background: #BABD00;">Array-to-array migration:</mark> This type of VM migration involves moving VMs or virtual disks across multiple physical servers using storage array based methods. 

VM migration involves moving the entire active state of a VM from the source hypervisor to the target. The state information includes memory contents and all other information which identifies the VM. VM identification information includes data, which maps the VM hardware elements such as BIOS, Devices, CPU, and MAC address for Ethernet cards. When a VM is migrated to another hypervisor on a clustered server, virtual disks of the VM are not migrated because these can be accessed from another hypervisor as well. However, in situations where a VM needs to be migrated to a hypervisor on a remote server, virtual disks are also moved. In case of array-to-array migration, virtual disks are always moved from the source array to the target array. After migration, VM in the source hypervisor is deleted.  

Virtual disks are also deleted if they were actually moved. For example, in the case of server-to-server remote migration and array-to-array based migration, virtual disks are deleted after their copies are saved at the target.

### <mark style="background: #BABD00;">VM Migration: Server-to-Server:</mark>

- <mark style="background: #BABD00;">Hot-On:</mark> Migrate a VM that is powered on. VM needs to be quiesced before migration
- <mark style="background: #BABD00;">Cold:</mark> Migrate a VM that is powered off
- <mark style="background: #BABD00;">Hot-Suspended:</mark> Migrate a VM that is suspended
- <mark style="background: #BABD00;">Concurrent:</mark> Migrate multiple VMS simultaneously

There are primarily four major modes of VM migration between servers:  
- Hot-On migration: VM remains in a powered-on state (currently running). Shared storage and CPU compatibility might be necessary between the source and destination servers. VM also needs to be quiesced during migration so that the state of the VM after migration remains consistent. After migration, client accesses are directed to the VM on the target hypervisor. Hot on migration is useful in scenarios where a server or hypervisor is overloaded or requires maintenance and/or repair soon because it might be underperforming.  
- <mark style="background: #BABD00;">Cold migration:</mark> VM is in a power off state. Cold migration is typically used when a VM needs to be moved to another remote location or VDC.  
- <mark style="background: #BABD00;">Hot-Suspended migration:</mark> VM is in a suspended state. In a suspended state, all virtual machine activities are paused until the resume command is issued. This kind of migration could be useful when a VM needs to be migrated from a failing server to another operational server.  
- <mark style="background: #BABD00;">Concurrent migration:</mark> Multiple VMs are migrated simultaneously to one or more hypervisors. The maximum number of concurrent sessions is generally dependent upon the available network bandwidth. Concurrent migration can be performed when VM is on a power on/off/suspended state. Concurrent migrations are useful for continuously optimising VM placement across the entire IT environment.

<mark style="background: #FF5582A6;">Don't include VMware info as it is software-specific.</mark>