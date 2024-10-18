### <mark style="background: #FF5582A6;">Daytime Server Code:</mark>

![](https://i.imgur.com/GHC3NQ3.png)

### <mark style="background: #FF5582A6;">Overview of the daytime server:</mark>

Refer to the Daytime server code presented in class. 

The operation of the Daytime application is as follows:
- Client calls ``CONNECT`` to connect to the server,
- Server calls ``ACCEPT`` to accept the connection request,
- Server returns a formatted string using the ``SEND`` primitive 
- Server application calls ``CLOSE`` to close the connection,
- Client calls ``RECV`` to retrieve the data from the connection,
- Client closes the connection using the ``CLOSE`` primitive,
- The Client application terminates using ``exit(0)``;

Key points to note in the Daytime server code:
- Server address structure,
- Calls to ``bind()``, ``listen()`` and ``accept()``.

### <mark style="background: #FF5582A6;">The echo client-server:</mark>

Having explored the <mark style="background: #FF5582A6;">Daytime</mark> application, the next application to examine is the <mark style="background: #FF5582A6;">Echo</mark> Client and Server.

The essence of this application is as follows:
- The Client application sends (``send()``) a string (from the command-line) to the server across an open connection,
- The Server application reads (``recv()``) the string and returns it to the Client application (``send()``)exactly as it came in,
- Both applications call for the connection to be closed (``close()``).

#### <mark style="background: #FF5582A6;">The recv() primitive:</mark>

To complete this task it is necessary to understand the operation of the recv() primitive.

```JAVA
while ((numBytes = recv(sock, recvbuffer, BUFSIZE - 1, 0)) >0) 
{
	recvbuffer[numBytes] = '\0'; 
	fputs(recvbuffer, stdout); 
}
```

The while loop is necessary as the data may not arrive across the connection in a single transfer:
- Recall that data arriving from the remote socket is stored in the RECV-Q buffer within the local TCP entity,
- Repeated calls to ``recv()`` are needed to transfer this data from TCP (the Transport layer) into the application (the Application layer).

``numBytes`` is the return value from ``recv()``:
- It represents the <mark style="background: #FF5582A6;">number of bytes</mark> read from the socket,
- It returns one of three values: 
	- ``<1`` represents an error condition,
	- ``0`` represents a closed connection i.e. remote application has called close(), 
	- ``>1`` represents an open connection with potentially more data to be received.


### <mark style="background: #FF5582A6;">Breaking from recv():</mark>

If the ``recv()`` primitive is used as above in the <mark style="background: #FF5582A6;">Echo</mark> ``Client`` and ``Server`` applications it will cause problems:
- Either or both applications will remain inside the loop,
- Refer to the solution discussed in class.

### <mark style="background: #FF5582A6;">Addressing:</mark>

A key aspect of Networked Applications, such as Daytime and Echo, is <mark style="background: #FF5582A6;">Addressing</mark>.

In order for the Client and Server applications to communicate with each other, some form of explicit addressing is required.

The Destination Server application requires an <mark style="background: #FF5582A6;">unambiguous (unique)</mark> address in order for the Source Client application to initiate a connection request:

Uniqueness can only be achieved using <mark style="background: #FF5582A6;">both IP and TCP addressing</mark>

Recall that the IP layer is responsible for delivering datagrams/packets to remote hosts across an internetwork: It uses IP addressing to achieve this host-to-host delivery.

However, the data encapsulated inside these datagrams/packets is typically destined for an <mark style="background: #FF5582A6;">application</mark> in the Application Layer.

With potentially many applications residing in the Application layer, how does the data get to the correct application?

<mark style="background: #FF5582A6;">Transport Layer</mark> addressing plays a vital role in this task

### <mark style="background: #FF5582A6;">Transport Addressing:</mark>

Recall that transport protocols such as TCP provide services to the application layer.

To ensure unambiguous (unique) addressing of individual applications, the Transport layer provides its own addressing schema separate to the IP layer:
- These are generally known as Transport Service Access Points (TSAPs),
- These TSAPs uniquely identify entities in the Transport layer known as end points,
- In TCP parlance these end points are known as <mark style="background: #FF5582A6;">port numbers</mark> or more simply <mark style="background: #FF5582A6;">ports</mark>.

<mark style="background: #FF5582A6;">Port numbers are used by:</mark>
- Server applications to advertise their services and, to listen for Connection Requests,
- Client applications to uniquely identify a Server application when making a Connection Request.
- The <mark style="background: #FF5582A6;">network layer</mark> also defines <mark style="background: #FF5582A6;">end points</mark>. These are known as Network Service Access Points (NSAPs):
- IP addresses are examples of NSAPs.

The following slide illustrates the relationship between the NSAPs, TSAPs and transport connections.

### <mark style="background: #FF5582A6;">TSAPs, NSAPs and transport connections:</mark>

![](https://i.imgur.com/UHKnTOj.png)

### <mark style="background: #FF5582A6;">The TCP Port Number Range:</mark>

TCP Port numbers are sixteen bits long.

This creates a port number address space comprising approx. 65K addresses (16 bits implies 2<sup>16</sup> addresses) as follows:

![](https://i.imgur.com/bkuGzrP.png)

<mark style="background: #FF5582A6;">Reserved</mark> addresses are for well known applications such as HTTP (port 80), FTP (ports 20 and 21), Telnet (port 23) etc.
- These can only be allocated by users with SU privileges.

<mark style="background: #FF5582A6;">Ephemeral</mark> addresses are allocated by TCP to <mark style="background: #FF5582A6;">Client</mark> applications:
- It is not immediately obvious that Client applications require a port number,
- However, there needs to be a return address for data from the Server application.

Non-privileged addresses are for any other applications: This is the range that will be used in the lab exercises. 

It is important to note that the Ephemeral and <mark style="background: #FF5582A6;">Non-privileged</mark> ranges differ on different OS’s:
- Your home host may use different ranges depending on the OS used.
- On the Virtual Machines used in the labs, us the following command to view the range:
- ``sudo sysctl net.ipv4.ip_local_port_range``

### <mark style="background: #FF5582A6;">Socket Identifiers:</mark>

The concept of a ``socket`` or, ``end-point`` is complicated by the manner with which it is referenced within each of the Application and Transport layers:

Recall that from an Application layer perspective, sockets are referenced using a <mark style="background: #FF5582A6;">file descriptor</mark>:
- This is an ``integer`` descriptor similar to a <mark style="background: #FF5582A6;">file descriptor</mark> or <mark style="background: #FF5582A6;">file handle</mark>,
- Recall the ``int`` variable names used in the applications developed in lab: ``sock``, ``servSock``, ``clntSock`` etc.

From a TCP layer perspective, a ``socket`` is identified by a combination of an NSAP and TSAP separated by a colon (:)

Even though both layers are referencing the same entity – the ``socket``, the descriptors used are very different.

This difference is further complicated by the fact that the call to ``accept()`` returns a new socket:
- The <mark style="background: #FF5582A6;">listening</mark> socket and,
- The <mark style="background: #FF5582A6;">connected</mark> socket.

Referencing the connected socket from within the application is straightforward:
- A separate and unique ``int`` descriptor is returned,
- All interactions with the listening and connected sockets are obvious.

Referencing the <mark style="background: #FF5582A6;">connected</mark> socket from within the TCP layer is complicated:
- Each of the sockets will use the same NSAP:TSAP combination.
- To differentiate between the sockets, the <mark style="background: #FF5582A6;">socket-pair</mark> needs to be considered.

### <mark style="background: #FF5582A6;">Examining Socket Details:</mark>

<mark style="background: #FF5582A6;">Socket-pairs</mark> are used to identify TCP connections:

TCP connections can be viewed using the netstat utility:
- From the command-line prompt type: ``netstat –ntap``
- This returns details of active TCP connections within the host OS.

An explanation of the flags:
- ``‘n’`` reveals IP addresses in dotted-decimal notation, 
- ``‘t’`` filters on TCP addresses only, 
- ``‘a’`` shows all connections,
- ``‘p’`` reveals the process id details for each connection.

The following slide shows a sample output when the  <mark style="background: #FF5582A6;">netstat</mark> command is used.

### <mark style="background: #FF5582A6;">Examining Addressing Details:</mark>

<mark style="background: #FF5582A6;">From the server end:</mark>
![](https://i.imgur.com/hWjM6La.png)

<mark style="background: #FF5582A6;">From the client end:</mark>
![](https://i.imgur.com/9E4LwEe.png)

This shows:
- A server with listening and connected sockets on port 1022, 
- A client on an ephemeral port 4136.

Note the columns <mark style="background: #FF5582A6;">Local Address</mark> and <mark style="background: #FF5582A6;">Remote Address</mark>: These contain details of the <mark style="background: #FF5582A6;">socket</mark> at <mark style="background: #FF5582A6;">each</mark> end of a connection.

Notice how TCP refers to a <mark style="background: #FF5582A6;">socket</mark> using a NSAP:TSAP combination.

### <mark style="background: #FF5582A6;">Socket Pairs:</mark>

Each row in the output from <mark style="background: #FF5582A6;">netstat</mark> relates to a connection:
- A TCP connection can be considered as a connection between two sockets; a <mark style="background: #FF5582A6;">local</mark> socket and a <mark style="background: #FF5582A6;">remote</mark> socket. 
- The columns labelled <mark style="background: #FF5582A6;">Local Address</mark> and <mark style="background: #FF5582A6;">Remote Address</mark> contain details of the socket at <mark style="background: #FF5582A6;">each</mark> end of a connection.
- Notice how TCP refers to a <mark style="background: #FF5582A6;">socket</mark> using a NSAP:TSAP combination.

The combination of <mark style="background: #FF5582A6;">Local Address</mark> and <mark style="background: #FF5582A6;">Remote Address</mark> is the <mark style="background: #FF5582A6;">identifier</mark> for a connection:
- It is known as a <mark style="background: #FF5582A6;">Socket Pair</mark>.
- An example socket pair: {147.252.30.9:1022, 147.252.234.34:4136}

<mark style="background: #FF5582A6;">Socket Pairs</mark> are how TCP views connections:

For each connection, the detail contained in each row is reversed depending on which end of the connection the ``netstat`` command is run.

Using socket-pair identifiers enables TCP to separately and unique identify a server’s <mark style="background: #FF5582A6;">listening</mark> and potentially multiple <mark style="background: #FF5582A6;">connected</mark> sockets.

This is important when incoming data (incoming to the TCP layer) needs to be passed to a local socket.

How connections are established from a Socket Pair perspective: It assumes the following primitive calls have been made within each of the client an server applications:

![](https://i.imgur.com/sVKDmN8.png)

### <mark style="background: #FF5582A6;">Socket Pairs before Connection Establishment:</mark>

Before Connection Establishment

![](https://i.imgur.com/kGI8o6v.png)

A Client Connection Request is now sent to : ``206.62.226.35``, Port 21

The following slide shows the socket pairs relating to the connection after Connection Establishment.

### <mark style="background: #FF5582A6;">Sockets pairs after Connection Establishment:</mark>

![](https://i.imgur.com/LDPmYOB.png)
