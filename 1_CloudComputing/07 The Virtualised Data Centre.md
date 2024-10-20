#CloudComputing

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