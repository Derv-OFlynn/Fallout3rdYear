Having examined the TCP/IP Protocol Reference the focus now shifts to the TCP layer.

This layer is the heart of the whole protocol hierarchy.

It sits below the Application Layer providing a ‘Transport’ service to the applications that wish to communicate across a Network.

![](https://i.imgur.com/vzkY477.png)

TCP provides a reliable, cost-effective end-to-end data transport service <mark style="background: #FF5582A6;">independently</mark> of the physical network(s).

It is important to realise that a <mark style="background: #FF5582A6;">service</mark> is very different to a <mark style="background: #FF5582A6;">protocol</mark>, although they are frequently confused.

The next slide shows how the Transport Layer views the lower network interface layers.

### <mark style="background: #FF5582A6;">The Transport Layer's view of the Network:</mark>

![](https://i.imgur.com/id8kaxc.png)

### <mark style="background: #FF5582A6;">Services:</mark>

Each layer of the reference model provides a set of functionality to the layer immediately above:
- This set of functionality is known as <mark style="background: #FF5582A6;">The Services</mark>.
- The layer below is known as the <mark style="background: #FF5582A6;">Service Provider</mark> and the layer above is known as the <mark style="background: #FF5582A6;">Service User</mark>.

The Services are accessed through the interface between the layers.

### <mark style="background: #FF5582A6;">Protocols:</mark>

<mark style="background: #FF5582A6;">Protocols</mark> on the other hand are how the Services are implemented.

Typically a Protocol specifies a <mark style="background: #FF5582A6;">framing structure</mark> which will include a number of fields containing  Control data:
- Generically this framing structure is known as a Protocol Data Unit (<mark style="background: #FF5582A6;">PDU</mark>)
- Examples include Data Link Frame, IP Datagram etc.

The <mark style="background: #FF5582A6;">Protocol</mark> will also typically specify a procedure for interpreting and responding to the Control data within the PDU:
- For instance, if a service provides for reliable transfer of data then there must be some means specified within the protocol for tracking and recovering from data loss.
- In this instance part of the PDU Control field will include numbering e.g. byte numbers, frame numbers etc.

The Protocol will also specify how data in the Control Fields are to be interpreted and responded to if necessary.
- e.g. for missing frame return a REJ message.

### <mark style="background: #FF5582A6;">The TCP Transport Service Offering:</mark>

The TCP Transport Service has the following characteristics:
- <mark style="background: #FF5582A6;">Connection Orientation:</mark> Before two applications entities can communicate they must first establish a connection.
- <mark style="background: #FF5582A6;">Point-To-Point Communication:</mark> Each TCP connection has exactly two endpoints. 
- <mark style="background: #FF5582A6;">Complete Reliability:</mark> TCP guarantees that the data will be delivered exactly as sent i.e. no data missing or out of sequence 
- <mark style="background: #FF5582A6;">Full Duplex Communication:</mark> A TCP connection allows data to flow in either direction
	- TCP buffers outgoing and incoming data 
	- This allows applications to continue executing other code whilst the data is being transferred

<mark style="background: #FF5582A6;">Stream Interface:</mark> The <mark style="background: #FF5582A6;">source</mark> application sends a continuous sequence of octets across a connection
- The data is passed en-bloc to TCP for delivery
- TCP does not guarantee to deliver the data in the same size pieces that it was transferred by the source application. 

<mark style="background: #FF5582A6;">Reliable Connection Startup:</mark> TCP both applications to <mark style="background: #FF5582A6;">agree</mark> to any new connection

<mark style="background: #FF5582A6;">Graceful Connection Shutdown:</mark> Either can request a connection to be shut down. TCP guarantees to deliver all the data reliably before closing the connection

### <mark style="background: #FF5582A6;">The Transport Service:</mark>

The TCP transport service is offered to a <mark style="background: #FF5582A6;">user process</mark> that exists within the application layer:
- This user process is considered a <mark style="background: #FF5582A6;">Transport Service User</mark>,
- The service is typically offered through a set of <mark style="background: #FF5582A6;">primitives</mark> across the interface between the layers,
- Calls to these primitives cause the transport service provider to perform some action. 

### <mark style="background: #FF5582A6;">The Transport Entity:</mark>

The TCP software within the transport layer that implements the service will be referred to as the <mark style="background: #FF5582A6;">Transport Entity</mark>: This is the “Transport Service Provider”.

The <mark style="background: #FF5582A6;">Transport Entity</mark> can be located in any number of places including:
- Within the operating system (OS) kernel,
- As a separate user process,
- Within a library package bound to the network application,
- On the network interface card.

If the <mark style="background: #FF5582A6;">protocol stack</mark> is located within the OS the <mark style="background: #FF5582A6;">primitives</mark> are implemented as <mark style="background: #FF5582A6;">system calls</mark>:
- These calls turn control of the machine over to the OS to send and receive the necessary PDUs.
- The next diagram shows the Transport Entity in context.
- As can be seen it shows the Transport Layer sitting between the Application and Network layers.

![](https://i.imgur.com/RigRyEM.png)

It has a connection to each of the layers above and below:
- It is the <mark style="background: #FF5582A6;">Service Provider</mark> to the Application Layer and,
- A <mark style="background: #FF5582A6;">Service User</mark> of the Network Layer.

The TPDU represents the framing structure that is exchanged between <mark style="background: #FF5582A6;">Peer Entities</mark>:
- The PDU does NOT move <mark style="background: #FF5582A6;">horizontally</mark> between the Transport layers as depicted,
- Instead it moves <mark style="background: #FF5582A6;">up-and-down</mark> through the Protocol Stack.

### <mark style="background: #FF5582A6;">Transport Service Primitives:</mark>

What do these primitives look like?

Consider a generic transport interface as shown in  the next diagram: 
- Here can be seen a list of Primitives.
- These primitives allow application programs to establish, use and release connections.

Typically there is a very precise sequence of calls to these primitives: The exact sequence differs for clients and servers.

![](https://i.imgur.com/M0GOvvv.png)

![](https://i.imgur.com/OcYQYDU.png)

### <mark style="background: #FF5582A6;">Managing Connections:</mark>

Before explaining the sequence of primitive calls it is important to understand the Phases of Communication.

Recall from previous discussions on HDLC that there are generally three phases of communication associated with a connection-oriented service:
- Phase 1: Connection Establishment,
- Phase 2: Data Transfer, and,
- Phase 3: Connection Release.

During each phase a variety of PDUs are exchanged between the <mark style="background: #FF5582A6;">client</mark> and <mark style="background: #FF5582A6;">server</mark>:
- Each PDU contains a message destined for the peer entity on the remote end of the channel.
- The following slides explain the interaction for each phase.

### <mark style="background: #FF5582A6;">Connection interactions per phase:</mark>

<mark style="background: #FF5582A6;">Connection Establishment Phase:</mark>
1. The server application executes a LISTEN primitive (aka a <mark style="background: #FF5582A6;">call to Listen</mark>).
2. The server’s <mark style="background: #FF5582A6;">transport entity</mark> responds to this primitive call by: <mark style="background: #FF5582A6;">Blocking</mark> the server until a client request arrives.
3. The client application <mark style="background: #FF5582A6;">then</mark> executes a CONNECT primitive (aka <mark style="background: #FF5582A6;">call to Connect</mark>).
4. The client’s transport entity responds to this call by <mark style="background: #FF5582A6;">blocking</mark> the client <mark style="background: #FF5582A6;">and</mark> sending a CONNECTION REQUEST TPDU to the Server.
5. Upon receipt of the CONNECTION REQUEST TPDU the server’s <mark style="background: #FF5582A6;">transport entity</mark>: Unblocks the server <mark style="background: #FF5582A6;">and</mark> returns a CONNECTION ACCEPTED TPDU to the Client,
6. The client’s transport entity then unblocks the client.
7. The connection is now deemed <mark style="background: #FF5582A6;">established</mark>

<mark style="background: #FF5582A6;">Data Transfer Phase:</mark>
- With an <mark style="background: #FF5582A6;">active</mark> connection now established data can be exchanged between the client and server using the <mark style="background: #FF5582A6;">SEND</mark> and <mark style="background: #FF5582A6;">RECEIVE</mark> primitives,
- Each side must take turns using (blocking) <mark style="background: #FF5582A6;">RECEIVE</mark> and <mark style="background: #FF5582A6;">SEND</mark>.

<mark style="background: #FF5582A6;">Release Phase:</mark>
- Either the client or the server application can call a DISCONNECT primitive:
- This causes a DISCONNECT TPDU to be sent to the remote transport entity.
- Once the DISCONNECT TPDU has been received and acknowledged the connection is deemed <mark style="background: #FF5582A6;">released</mark>.

### <mark style="background: #FF5582A6;">Berkeley Sockets:</mark>

The basic transport primitives discussed above are <mark style="background: #FF5582A6;">not</mark> standardised.

Instead most OS designers have adopted the <mark style="background: #FF5582A6;">socket 
primitives</mark>:
- These originated from the Berkeley University of California’s UNIX OS which contained the original <mark style="background: #FF5582A6;">TCP/IP</mark> suite of internetworking protocols.

Consequently the socket API has become the <mark style="background: #FF5582A6;">de facto</mark> standard for interfacing to TCP/IP

### <mark style="background: #FF5582A6;">Origins of the socket concept:</mark>

Coming from a UNIX background <mark style="background: #FF5582A6;">sockets</mark> use many concepts found in UNIX: An application communicates through a <mark style="background: #FF5582A6;">socket</mark> in the same way that it transfers data to or from a file 

For File I/O UNIX uses an <mark style="background: #FF5582A6;">open-read-write-close</mark> paradigm, an application makes the following calls in strict order:
- <mark style="background: #FF5582A6;">open</mark> to prepare a file for reading/writing,
- <mark style="background: #FF5582A6;">read</mark> or <mark style="background: #FF5582A6;">write</mark> to retrieve or send data to/from the file,
- <mark style="background: #FF5582A6;">close</mark> to release the file.

When open is first called a <mark style="background: #FF5582A6;">descriptor</mark> is returned:
- All calls to the file use this <mark style="background: #FF5582A6;">descriptor</mark>,
- Socket communication also uses this <mark style="background: #FF5582A6;">descriptor</mark> approach.

### <mark style="background: #FF5582A6;">Socket Communication in UNIX:</mark>

Applications that need to use the TCP/IP protocols to communicate must request the OS to create a <mark style="background: #FF5582A6;">socket</mark>: This is an abstract concept which will be explained in detail later.

Similar to File I/O the OS returns a descriptor that uniquely identifies the socket:
- As with File I/O this descriptor must be used in all interactions with the socket.

The following slides lists the Socket API primitives and illustrates an example of how these primitives are used by a client and server application

![](https://i.imgur.com/20vSvhc.png)

### <mark style="background: #FF5582A6;">An Example Client-Server Interaction using sockets:</mark>

![](https://i.imgur.com/AZHFzWK.png)


### <mark style="background: #FF5582A6;">The Socket Primitives - Explained:</mark>

<mark style="background: #FF5582A6;">The following primitives are executed by servers:</mark>
- <mark style="background: #FF5582A6;">SOCKET:</mark> This primitive creates a new <mark style="background: #FF5582A6;">end point</mark> within the Transport Entity:
	- Table space is allocated within the transport entity,
	- A file descriptor is returned which is used in all future calls
- <mark style="background: #FF5582A6;">BIND:</mark> This primitive binds a socket to a network address. This allows remote clients to connect to it
- <mark style="background: #FF5582A6;">LISTEN:</mark> This primitive allocates a queuing space within the transport entity for incoming call requests.
- <mark style="background: #FF5582A6;">ACCEPT:</mark> This primitive blocks the server waiting for an incoming connection:
	- Upon receipt of a connection request the <mark style="background: #FF5582A6;">transport entity</mark> creates a <mark style="background: #FF5582A6;">new</mark> socket identical to the original one and returns a file descriptor to the server.
	- The server <mark style="background: #FF5582A6;">forks off</mark> a new process or service thread to handle the <mark style="background: #FF5582A6;">connection</mark> on the new socket
	- The server <mark style="background: #FF5582A6;">also</mark> continues to wait for more connections on the original socket.

<mark style="background: #FF5582A6;">The following primitives are executed by clients:</mark> 
- SOCKET: As before 
- CONNECT: This primitive blocks the client and actively starts the connection process

<mark style="background: #FF5582A6;">The following primitives are executed by clients and 
servers:</mark> 
- <mark style="background: #FF5582A6;">SEND and RECV:</mark> These primitives are used to transmit and receive data over the full-duplex connection 
- <mark style="background: #FF5582A6;">CLOSE:</mark> This primitive releases the transport connection

### <mark style="background: #FF5582A6;">Sockets and Socket Libraries:</mark>

In most systems the socket functions are part of the OS.

Some systems, however, require a socket library to provide the interface to the transport entity:
- These operate differently to a native socket API, 
- The code for the library socket procedures are linked into the application program and resides in its address space, 
- Calls to a socket library pass control to the library routine as opposed to the OS.

Both implementations provide the same semantics from a programmer's perspective 

Applications using either implementation can be ported to other computer systems.

### <mark style="background: #FF5582A6;">Example use of Sockets:</mark>

The next slide shows an example Client application using the Sockets API.

It is a simple Daytime Client which connects to a Daytime Server for the purpose of retrieving the current date and time from the Server Host.

This application is written in ‘C’.

Lines 24, 41, 44 and 57 show four of the socket primitives being called. 

This programme will be explained in class and you will have a chance to compile and run it against a pre-compiled server.

![](https://i.imgur.com/fdrIRNq.png)
![](https://i.imgur.com/nXFqp8T.png)
