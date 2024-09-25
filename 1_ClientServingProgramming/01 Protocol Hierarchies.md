### <mark style="background: #FF5582A6;">Protocol Hierarchies:</mark>

Computer Networks are generally comprised of numerous pieces of hardware and software.

Recall the previous attempt to 'model' how these components interconnect and interact with each other

Source -> Transmitter -> Transmission System -> Receiver -> Destination

Whilst the horizontal model is useful when looking at hardware components, the reality is it does not explain everything

From previous discussions on: <mark style="background: #FF5582A6;">Data Link Control</mark>, <mark style="background: #FF5582A6;">LANs technologies</mark>, <mark style="background: #FF5582A6;">Internetworking</mark> etc. much of the functionality required to provide communications between host machines is not necessarily provided on individual hardware components:

For instance the transmission/reception of MAC frames requires sending and receiving binary ones and zeroes on a variety of transmission media using a variety of access techniques. 

This mixture of functionality is provided on <mark style="background: #FF5582A6;">NICs</mark> (one per LAN technology) and in software elsewhere on the host.

 A better model is required to explain these concepts and techniques.

To simplify network design most networking technologies are organized as <mark style="background: #FF5582A6;">layers</mark> of protocol  software:
- The purpose of each layer is to provide <mark style="background: #FF5582A6;">one</mark> component of the overall solution to the “Communications Problem” such as “frame reception/transmission” etc.
- These layers of software can exist on separate hardware components and/or hosts or is some instances multiple layers can exist on a single hardware platform and/or hosts.

This concept is not dissimilar to the approach used 
for software development:
- Objects or libraries are used to perform specific operations.
- Importantly the object/library function keeps details of its internal state and algorithms hidden from the main program.

The same approach is used for network protocol software:
- Each layer of software provides one part of the solution such as: frame transmission/reception or, transmitting one/zeros onto a wire/wireless transmission medium etc.

With networking software, the layers of protocol software are organised into a <mark style="background: #FF5582A6;">Stack</mark>.

Each layer is said to offer <mark style="background: #FF5582A6;">services</mark> to higher layers and to use the services offered by the lower layers.

<mark style="background: #FF5582A6;">Protocol/Protocol Entity:</mark> A software module that performs one sub-task such as: frame transmission/reception etc.

<mark style="background: #FF5582A6;">Protocol suites/stack:</mark> A number of such software modules that work together to perform all of the tasks required to enable two hosts communicate.

<mark style="background: #FF5582A6;">Protocol Architectures/Model:</mark> A model by which we can categorize or view the different protocol layers.

The OSI model deals with connecting open systems, i.e. systems that are open for communication with other systems regardless of who built them or how they were manufactured.

The principles that were applied to arrive at the seven layers are as follows:
- Each layer was created when a different <mark style="background: #FF5582A6;">level of abstraction</mark> was required.
- Each layer performs one well-defined function with each function chosen carefully to facilitate the development of <mark style="background: #FF5582A6;">standardised protocols</mark>.
- The number of layers chosen was sufficient enough to ensure that distinct functions were not <mark style="background: #FF5582A6;">lumped</mark> together to become unwieldy,

The layers of software work together in unison to provide overall solutions to the problems of communicating between host computers across  complex networks.

<mark style="background: #FF5582A6;">Information</mark> flows up-down the stack, across each of 
the interfaces (boundaries) between the layers:
- These boundaries were carefully defined to <mark style="background: #FF5582A6;">minimise</mark> information flow across the interfaces.
- The following slides discuss the functionality of each layer of protocol software. This functionality should be recognisable from previous discussions.

<mark style="background: #FF5582A6;">OSI model:</mark>
1. Application
2. Presentation
3. Session
4. Transport
5. Network
6. Data Link
7. Physical

The role of the <mark style="background: #FF5582A6;">Physical</mark> layer is to act as a medium and transmit pulses that represent 1s and 0s.

The Data Link layer interprets and deals with frames. Flow control, error control and error recovery.

Ethernet cables use Manchester encoding

Have to use an 802.11 protocol to communicate across a wireless mask

TCP/IP is a five layer model, more simplistic than OSI

Data works it's way down from the model.

### <mark style="background: #FF5582A6;">The Physical Layer:</mark>

Concerned with transmitting <mark style="background: #FF5582A6;">raw</mark> bits over a <mark style="background: #FF5582A6;">communication channel</mark>:

Its purpose is to ensure that the transmission of binary 1s and 0s adheres to what is appropriate for the transmission medium and what is expected by the <mark style="background: #FF5582A6;">receiver</mark>.

Primarily it deals with matters such as: What voltage levels are used? What frequencies are used? How long does it take to transmit a bit (Bit Duration)? etc. 

There are certain design issues to address such as: the <mark style="background: #FF5582A6;">mechanical</mark> and <mark style="background: #FF5582A6;">electrical</mark> design of the plugs (RJ-45, BNC etc.) and sockets, timing interfaces, the physical <mark style="background: #FF5582A6;">transmission medium</mark> etc.

### <mark style="background: #FF5582A6;">The Data Link Layer:</mark>

Concerned with the successful transmission of data across an individual link:

Its purpose is to transforms a <mark style="background: #FF5582A6;">raw</mark> transmission facility into a <mark style="background: #FF5582A6;">data communications channel</mark> that <mark style="background: #FF5582A6;">appears</mark> free of transmission errors.

Primarily it deals with matters such as the transmission/reception of <mark style="background: #FF5582A6;">data frames</mark>. 

There are certain design issues to address such as: the creation of localised unique addressing, the creation of a unique framing structure, flow control, error control, controlling access to a <mark style="background: #FF5582A6;">shared</mark> channel etc.

<mark style="background: #FF5582A6;">Example DL functionality:</mark> 
![](https://i.imgur.com/dIX7TeT.png)

### <mark style="background: #FF5582A6;">The Network Layer:</mark>

Concerned with the successful delivery of data between hosts across complex network infrastructures:

Its purpose is to control the operation of the <mark style="background: #FF5582A6;">sub-networks</mark> to achieve host-to-host delivery.

Primarily it deals with matters such as the routing of packets from the source station towards the <mark style="background: #FF5582A6;">destination</mark> station across sub-nets etc. 

There are certain design issues to address such as: the creation a globally unique address space, the creation of a globally unique framing structure.

Essentially this layer is responsible for managing data communications across interconnected <mark style="background: #FF5582A6;">heterogeneous</mark> networks.

![](https://i.imgur.com/CDAKuAq.png)

### <mark style="background: #FF5582A6;">The Transport Layer:</mark>

This is a key layer. 

It is a true <mark style="background: #FF5582A6;">end-to-end</mark> layer responsible for the 
reliable delivery of data between <mark style="background: #FF5582A6;">processes</mark> on end-host machines i.e. process-to-process delivery:

Its purpose is to provide a reliable data transport service to applications.

Primarily it deals with interfacing with applications for the purpose of exchanging data between applications across a network.

There are certain design issues to address such as: multiplexing data streams from/to remote applications, data loss, network latency etc

### <mark style="background: #FF5582A6;">Data Flows:</mark>

The layers work together to provide the complete functionality required to facilitate communications between two remotely connected host machines regardless of how they connect to the internet.

The following slide shows how data flows between the layers (up-and-down):

Note that sometimes it is necessary to break up the data to meet some size restrictions associated with some lower layer protocol software. Recall use of <mark style="background: #FF5582A6;">Fragmentation</mark> at the Network layer.

Encapsulation and Information flow between the layers on an end-host.

![](https://i.imgur.com/FU1KSte.png)

Some of the layers are also implemented on intermediary networking devices such as Routers:
- This is because the functionality associated with these layers is needed for a particular purpose such as: frame reception/transmission, packet routing etc.

The following slide shows how the complete set of layers are implemented on the end-hosts as well as on the intermediary networking devices.

### <mark style="background: #FF5582A6;">Repeater Implementation:</mark>

![](https://i.imgur.com/F4nJIkE.png)

![](https://i.imgur.com/Wk7RgyN.png)

![](https://i.imgur.com/KmI9XwZ.png)
