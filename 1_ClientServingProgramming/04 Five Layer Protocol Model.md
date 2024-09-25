### <mark style="background: #FF5582A6;">The ISO OSI Model</mark>

![](https://i.imgur.com/t70Q8KL.png)

<mark style="background: #FF5582A6;">The Application Layer:</mark> 
- Contains a <mark style="background: #FF5582A6;">variety</mark> of protocols commonly used on the Internet
- E.g. HTTP (HyperText Transfer Protocol) is the underlying protocol for the World Wide Web
- Other protocols include FTP, E-mail etc.

<mark style="background: #FF5582A6;">The Presentation Layer:</mark> 
- Concerned with the <mark style="background: #FF5582A6;">syntax</mark> and semantics of the information transmitted
- Facilitates communication between <mark style="background: #FF5582A6;">big-endian</mark> computers e.g. Sun Sparcs and <mark style="background: #FF5582A6;">little-endian</mark> computers e.g. Windows machines

<mark style="background: #FF5582A6;"> The Session Layer:</mark>  
- Facilitates the use of sessions between end stations. During a session the user and the computer system engage in a <mark style="background: #FF5582A6;">dialogue</mark>
- The session layer establishes and maintains dialogues

It also determines: 
- The type of control to be used i.e. two-way simultaneous communication, two-way alternate comm. or one-way comm.
- <mark style="background: #FF5582A6;">Re-synchronisation</mark> of the dialogue after a crash

<mark style="background: #FF5582A6;">The Transport Layer:</mark> 
- This is a key layer. It is a true <mark style="background: #FF5582A6;">end-to-end</mark> layer
- Its function is to isolate the applications from the underlying network hardware technology
- It splits the source data into manageable chunks and passes them to the network layer 
- It uses the network as a reliable ‘deliverer’ of data

<mark style="background: #FF5582A6;">The Network Layer:</mark> 
- Concerned with controlling the operation of the <mark style="background: #FF5582A6;">sub-network</mark> (subnet)
- Deals with the routing of <mark style="background: #FF5582A6;">packets</mark> from the <mark style="background: #FF5582A6;">source</mark> station towards the <mark style="background: #FF5582A6;">destination</mark> station across sub-nets 
- It handles the different sub-net addressing formats 
- Essentially this layer is responsible for interconnecting <mark style="background: #FF5582A6;">heterogeneous</mark> networks 

<mark style="background: #FF5582A6;">The Data Link Layer:</mark> 
- Concerned with getting data across an individual link 
- Essentially it transforms a <mark style="background: #FF5582A6;">raw</mark> transmission facility into a <mark style="background: #FF5582A6;">data communications channel</mark> that appears free of transmission errors
- Breaks up the data into <mark style="background: #FF5582A6;">data frames</mark>. Also deals with flow control, controlling access to a <mark style="background: #FF5582A6;">shared</mark> channel etc.

<mark style="background: #FF5582A6;">The Physical Layer:</mark> 
- Concerned with transmitting <mark style="background: #FF5582A6;">raw</mark> bits over a <mark style="background: #FF5582A6;">communication channel</mark>. Must ensure that when a binary 1 is sent it is received as such by the <mark style="background: #FF5582A6;">receiver</mark>
- Deals with voltage levels used, bit duration etc. 
- Design issues deal with <mark style="background: #FF5582A6;">mechanical</mark>, <mark style="background: #FF5582A6;">electrical</mark>, and <mark style="background: #FF5582A6;">timing interface</mark>s, and the physical <mark style="background: #FF5582A6;">transmission medium</mark>

![](https://i.imgur.com/XBAKdJr.png)


### <mark style="background: #FF5582A6;">TCP/IP Reference Model:</mark>

![](https://i.imgur.com/VYOqIHX.png)

The protocols upon which this model is based (<mark style="background: #FF5582A6;">TCP and IP</mark>) fuelled the early growth of the <mark style="background: #FF5582A6;">Internet</mark>:
- TCP and IP were adapted because there were available 
- The ISO protocols on the other hand were still being developed

The <mark style="background: #FF5582A6;">TCP/IP Reference Model</mark> was developed <mark style="background: #FF5582A6;">after</mark> the protocols. 

Specific design goals of this <mark style="background: #FF5582A6;">Reference Model</mark> included: 
- Ability to survive the loss of subnet hardware
- Ability to handle multiple types of data including files and real-time speech

These requirement led to the adoption of a connectionless packet-switching network within the <mark style="background: #FF5582A6;">internet</mark> layer

<mark style="background: #FF5582A6;">The Internet Layer:</mark> This layer is key to the whole architecture
- It facilitates hosts injecting packets into any network 
- It ensures correct routing of packets to the Destination station 

<mark style="background: #FF5582A6;">The Transport Layer:</mark> 
- Facilitates <mark style="background: #FF5582A6;">end-to-end</mark> communication between the Source and Destination hosts

Two end-to-end transport protocols have been defined:
- <mark style="background: #FF5582A6;">TCP (Transmission Control Protocol):</mark> This is a <mark style="background: #FF5582A6;">reliable</mark>, <mark style="background: #FF5582A6;">connection-oriented</mark> protocol that allows a byte stream originating on one machine to be delivered <mark style="background: #FF5582A6;">without</mark> error to any other machine in the internet. 
- <mark style="background: #FF5582A6;">UDP (User Datagram Protocol):</mark> This is an <mark style="background: #FF5582A6;">unreliable</mark>, <mark style="background: #FF5582A6;">connectionless</mark> protocol for applications that provide their own <mark style="background: #FF5582A6;">sequencing</mark> and <mark style="background: #FF5582A6;">flow control</mark> functionality

<mark style="background: #FF5582A6;">The Application Layer:</mark> 
- This layer contains all of the higher-level protocols including FTP, E-mail, the Domain Name System (DNS) and HTTP.

<mark style="background: #FF5582A6;">The Host-to-Network or Network Interface Layer:</mark>
- This layer is meant to deal with hosts connecting to the network - similar to the ISO OSI Data Link layer.

<mark style="background: #FF5582A6;">The Physical Layer:</mark>
- Similar to the Physical layer of the ISO OSI model.

These lower two layers are not well defined within the TCP/IP reference model

### <mark style="background: #FF5582A6;">Relationship between TCP, UDP and IP</mark>
![](https://i.imgur.com/w1mpP9I.png)
