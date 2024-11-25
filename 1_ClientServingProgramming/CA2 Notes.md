# <mark style="background: #FF5582A6;">10. Name Address and Hostnames</mark>

### <mark style="background: #FF5582A6;">IP Addresses and Hostnames:</mark>

<mark style="background: #FF5582A6;">The applications developed thus far have used explicit IP addresses:</mark>
- Typically an IP address is passed from the command line to be used by a client application to establish a connection to a remote server,
- Practically, however, end-users rarely know the IP address of the remote server applications,
- Instead, end-users use human-readable <mark style="background: #FF5582A6;">hostnames</mark>.

<mark style="background: #FF5582A6;">Advantages for using hostnames:</mark>
- Using <mark style="background: #FF5582A6;">hostnames</mark> instead of IP addresses is easier for end-users,
- A host’s IP address can change without affecting its <mark style="background: #FF5582A6;">hostname</mark>. For instance, www.example.com currently resides at 93.184.216.34. This IP address could easily be changed.

### <mark style="background: #FF5582A6;">Hostname-to-IP Address Mappings:</mark>

Whilst hostnames are preferable, the client applications connecting to remote server applications still require an IP address to initiate communications:

There is a service that stores mappings for hostnames and their IP addresses: the <mark style="background: #FF5582A6;">Name Service</mark>

The process of mapping a hostname to a numeric quantity such as, an IP address or, Port Number, is called <mark style="background: #FF5582A6;">resolution</mark>,

When an IP address for a particular hostname is obtained from a <mark style="background: #FF5582A6;">name service</mark>, the hostname is said to be <mark style="background: #FF5582A6;">resolved</mark>.

<mark style="background: #FF5582A6;">Two primary name service sources are:</mark>
- The <mark style="background: #FF5582A6;">Domain Name System (DNS)</mark>. This is a distributed name service requiring the use of the DNS protocol. and,
- Local configuration databases which are operating-system specific.

Fortunately from a programming perspective the details of the name service are hidden: We only need to know how to ask for a name to be <mark style="background: #FF5582A6;">resolved</mark>.

### <mark style="background: #FF5582A6;">Resolvers and Name Servers:</mark>

Organizations often run one or more name servers a.k.a. DNS (Domain Name System) servers.

Applications interact with DNS servers using functions imported from a library known as a <mark style="background: #FF5582A6;">resolver</mark>: The resolver code is contained in a system library and is link-edited into the application during the <mark style="background: #FF5582A6;">build</mark> process,

Calls to the resolver code are made using functions such as ``getaddrinfo( )`` and ``getnameinfo( )``

The former maps a hostname into its IP address, and the
latter does the reverse mapping

### <mark style="background: #FF5582A6;">Operation of Resolvers:</mark>

Prior to contacting a name server, the resolver code refers to a local <mark style="background: #FF5582A6;">configuration</mark> file to determine the IP Address of the name server(s):

The file ``/etc/resolv.conf`` normally contains the IP address of the <mark style="background: #FF5582A6;">local</mark> name servers

The resolver then sends a query to a local name server for a resource record:
- Entries in the DNS are known as <mark style="background: #FF5582A6;">resource records</mark> (RRs)
- If necessary, the local name server may query another name server (starting at the Root DNS server) for the RR.

### <mark style="background: #FF5582A6;">Resolvers and Name Servers:</mark>

![](https://i.imgur.com/Fm9yhkU.png)

### <mark style="background: #FF5582A6;">Name and Address Conversions:</mark>

There are a number of different <mark style="background: #FF5582A6;">resource records</mark>:
- <mark style="background: #FF5582A6;">A</mark> records map hostnames to a 32-bit IPv4 address,
- <mark style="background: #FF5582A6;">AAAA</mark> records map hostnames to a 128-bit IPv6 address,
- <mark style="background: #FF5582A6;">PTR</mark> records map <mark style="background: #FF5582A6;">IP addresses into hostnames</mark>,
- <mark style="background: #FF5582A6;">MX</mark> records specifies a host to act as a <mark style="background: #FF5582A6;">mail exchanger</mark>,
- CNAME records map common services, such as <mark style="background: #FF5582A6;">ftp</mark> and <mark style="background: #FF5582A6;">www</mark> to the actual host providing the service
- e.g. www.tudublin.ie has the <mark style="background: #FF5582A6;">canonical</mark> name tudublin.ie.

The RRs that we are interested in is the <mark style="background: #FF5582A6;">A record</mark>.

### <mark style="background: #FF5582A6;">The getaddrinfo() function:</mark>

The ``getaddrinfo( )`` function performs a query for an <mark style="background: #FF5582A6;">A</mark> record. It is defined as follows:

```C
int getaddrinfo (const char *hostStr, const char *serviceStr,
const struct addrinfo *hints, struct addrinfo **results);
```

e.g. ``getaddrinfo(“www.google.com”, 0, NULL, &addrList);``

<mark style="background: #FF5582A6;">Returns:</mark> NULL if OK and a non-null error code if unsuccessful.

The function returns one, or more, ``addrinfo`` structures, each of which contains an Internet address that can be specified in subsequent calls to ``bind()`` or ``connect()``.

### <mark style="background: #FF5582A6;">getaddrinfo() parameters:</mark>

<mark style="background: #FF5582A6;">hostStr:</mark> Points to a null-terminated character string representing a host <mark style="background: #FF5582A6;">name</mark> such as aisling, or, a fully qualified domain name (<mark style="background: #FF5582A6;">FQDN</mark>) such as: aisling.student.tudublin.ie

<mark style="background: #FF5582A6;">serviceStr</mark>: A service name which is translated to the corresponding port number. This is ignored for the moment

<mark style="background: #FF5582A6;">hints:</mark> filters to be used to restrict the information returned

<mark style="background: #FF5582A6;">results:</mark> the address of a pointer (``type struct addrinfo``) to hold the first address of a <mark style="background: #FF5582A6;">linked list</mark> of results i.e. the protocol addresses

### <mark style="background: #FF5582A6;">addrinfo structure:</mark>

Each entry in the linked list is an ``addrinfo`` structure which is defined as follows:

```C
struct addrinfo {
int ai_flags; // Flags to control information resolution
int ai_family; // Family: AF_INET, AF_UNSPEC etc.
int ai_socktype; // Socket type: SOCK_STREAM,
SOCK_DGRAM
int ai_protocol; // Protocol: 0 (default) or IPPROTO_XXX
socklen_t ai_addrlen; // Length of socket address ai_addr
struct sockaddr *ai_addr; // Socket address for socket
char *ai_canonname; // Canonical name
struct addrinfo *ai_next; // Next addrinfo in linked list
} ;
```

### <mark style="background: #FF5582A6;">addrinfo members of interest:</mark>

<mark style="background: #FF5582A6;">here are five members of interest:</mark>
- <mark style="background: #FF5582A6;">ai_family:</mark> Specifies the address family supported by the hostname. Recall we are interested in AF_INET which is the TCP/IP stack.
- <mark style="background: #FF5582A6;">ai_socktype:</mark> Specifies the type of socket supported by the hostname. Recall we are interested in SOCK_STREAM i.e. a streaming socket.
- <mark style="background: #FF5582A6;">ai_protocol:</mark> Specifies the specific protocol supported by the hostname. Recall we are interested in IPPROTO_TCP i.e. TCP
- <mark style="background: #FF5582A6;">*ai_addr:</mark> Points to a structure that holds the full TCP/IP address for the hostname. The next slide refers to this structure.
- <mark style="background: #FF5582A6;">ai_addrlen:</mark> The length of the socket address.

### <mark style="background: #FF5582A6;">ai_addr and sockaddr_in:</mark>

``*ai_addr`` points to a socket address structure of type
sockaddr. Recall this is the <mark style="background: #FF5582A6;">generic</mark> address structure.

TCP applications use the <mark style="background: #FF5582A6;">family-specific</mark> address structure (``sockaddr_in`` – members shown below) which is then typecast to the generic address structure in any calls to the socket primitives.

```C
struct sockaddr_in {
	uint8_t sin_len; // length of structure (16)
	sa_family_t sin_family; // AF_INET
	in-port_t sin_port; // 16-bit TCP or UDP port number
	network byte ordered
	struct in_addr sin_addr; // 32-bit IPv4 address
	network byte ordered
	char sin_zero[8]; // unused
};
```

Fortunately, it is not necessary to access individual members of the <mark style="background: #FF5582A6;">generic</mark> socket address structure:
- Calls to socket primitives that need addressing information only require a pointer to the structure.
- For instance a typical call to ``connect()`` is as follows: ``connect(sock, (struct sockaddr *) &servAddr, sizeof(servAddr))``,
- Where ``servAddr`` is a struct of type ``sockaddr_in``

To use information returned by ``getaddrinfo()`` we can use:
``connect(sock, addr->ai_addr, addr->ai_addrlen)``

Where ``addr`` is a pointer to a structure of type ``addrinfo`` and, ``ai_addr`` (a member of ``addr``) is a pointer to a generic address structure

### <mark style="background: #FF5582A6;">getaddrinfo() and freeaddrinfo():</mark>

Eventually the <mark style="background: #FF5582A6;">linked list</mark> of results returned by ``getaddrinfo()`` must be deallocated:
- This requires the use of the auxiliary function, ``freeaddrinfo()``
- Given a pointer to the head of the linked list, ``freeaddrinfo()`` frees all the storage allocated for the list.
- Failure to call this function can result in a memory leak

The following example program (``GetAddrInfo.c``) illustrates the use of ``getaddrinfo()`` and ``freeaddrinfo()``:

The program takes two command-line parameters, a hostname and a service name (or port number), and prints the IP address(es)

``./GetAddrInfo www.tudublin.ie http``

### <mark style="background: #FF5582A6;">A sample program using getaddrinfo():</mark>

![](https://i.imgur.com/i7WaVIq.png)

### <mark style="background: #FF5582A6;">Code Explained:</mark>

Line 16 is a <mark style="background: #FF5582A6;">struct</mark> that is used to restrict the type of information to be returned:
- In this case we are only interested in TCP/IP addresses
- The address of this struct is passed as the third argument (<mark style="background: #FF5582A6;">hints</mark>) to ``getaddrinfo( )``

Line 25 is the call to ``getaddrinfo( )``

Lines 30 iterates over each node of the linked list

Line 31 prints the IP address and Port number from the ``ai_addr`` member of the current linked list node:
- ``ai_addr`` points to a struct of type ``sockaddr``, the generic address structure.
- The addresses are then taken from the ``sa_data`` member.
- Recall we used a structure of type ``sockkaddr_in`` which has members: ``sin_addr`` and ``sin_por``

# <mark style="background: #FF5582A6;">11. TCP Flow Error Control Operation</mark>

### <mark style="background: #FF5582A6;">Where TCP and IP Operate:</mark>

![](https://i.imgur.com/evfK3Lh.png)

### <mark style="background: #FF5582A6;">The complete TCP Transport Service offering:</mark>

Recall that the TCP Transport Service has the following characteristics:

<mark style="background: #FF5582A6;">Connection Orientation:</mark> This aspect has been examined through a variety of lab exercises.

<mark style="background: #FF5582A6;">Point-To-Point Communication:</mark> Each TCP connection has exactly two endpoints. Also examined through the lab exercises.

<mark style="background: #FF5582A6;">Complete Reliability:</mark> TCP guarantees that the data will be delivered exactly as sent i.e. no data missing or out of sequence. To be examined later.

<mark style="background: #FF5582A6;">Full Duplex Communication:</mark> A TCP connection allows data to flow in either direction

TCP buffers outgoing and incoming data (recall RECVQ and SENDQ buffers) allowing applications to continue executing other code whilst the data is being transferred.

<mark style="background: #FF5582A6;">Stream Interface:</mark> The <mark style="background: #FF5582A6;">source</mark> application sends a continuous sequence of octets across a connection
- The data is passed en-bloc to TCP for delivery. Recall use of send() primitive containing a pointer to the local App-buffer.
- TCP does not guarantee to deliver the data in the same size pieces that it was transferred by the source application. Recall use of ``recv()`` primitive which is always placed inside a ``while()`` structure.

<mark style="background: #FF5582A6;">Reliable Connection Startup:</mark> TCP both applications to agree to any new connection. To be examined.

<mark style="background: #FF5582A6;">Graceful Connection Shutdown:</mark> Either can request a connection to be shut down. To be examined.

### <mark style="background: #FF5582A6;">TCP’s Reliability service offering</mark>

The following slides explore TCP’s <mark style="background: #FF5582A6;">Complete Reliability</mark>, <mark style="background: #FF5582A6;">Full Duplex Communication</mark> and <mark style="background: #FF5582A6;">Stream Interface</mark> service offerings.

Central to the provision of these services are the concepts of Flow Control and Error Control, both of which were explored previously from the perspective of the Data Link layer:

### <mark style="background: #FF5582A6;">Recap of Flow Control in the Data Link layer:</mark>

Recall the use of the Sliding Windows Flow Control
technique:
- This technique allows multiple <mark style="background: #FF5582A6;">Frames</mark> to be in transit in quick succession,
- This provides for more efficient <mark style="background: #FF5582A6;">Link Utilisation</mark>.

<mark style="background: #FF5582A6;">Characteristics of the technique are:</mark>
- Both stations use extended buffers to hold <mark style="background: #FF5582A6;">multiple</mark> frames.
- The Sending/Receiving stations maintain a list of frames already sent/received.
- The transmission link is effectively treated as a <mark style="background: #FF5582A6;">pipeline</mark> that can be <mark style="background: #FF5582A6;">filled</mark> with many frames in transit,
- Allows for Full Duplex communications (unlike Stop & Wait)

### <mark style="background: #FF5582A6;">Example Sliding Windows Flow Control:</mark>

Consider two Stations, A and B exchanging data. Assume Station A is sending data to Station B:

Station A is the <mark style="background: #FF5582A6;">Sender</mark> and Station B is the <mark style="background: #FF5582A6;">Receiver</mark>.

Before any data is exchanged, each station allocates buffer space for W frames (for example consider <mark style="background: #FF5582A6;">W=8</mark>)

This means that Station B can accept up to W (8) frames and, Station A can send up to W (8) frames, without individual frame acknowledgements (ACKs) being sent or received.

<mark style="background: #FF5582A6;">All frames contain a sequence number:</mark>
- All frames from Station A to Station B contain a sequence number for the <mark style="background: #FF5582A6;">current frame</mark>,
- All acknowledgements from Station B contain the sequence number of the <mark style="background: #FF5582A6;">next frame</mark> expected.
- Frames leaving Station A are stored in an <mark style="background: #FF5582A6;">outgoing</mark> buffer on Station A until an ACK is <mark style="background: #FF5582A6;">received</mark>.
- Frames arriving at Station B are stored in an <mark style="background: #FF5582A6;">incoming</mark> buffer on Station B until an ACK is <mark style="background: #FF5582A6;">sent</mark>

### <mark style="background: #FF5582A6;">Example Sliding Windows:</mark>

![](https://i.imgur.com/HTb4iFg.png)

### <mark style="background: #FF5582A6;">Sliding Windows Flow Control:</mark>

<mark style="background: #FF5582A6;">Multiple</mark> frames can be <mark style="background: #FF5582A6;">acknowledged</mark> using a single control message (<mark style="background: #FF5582A6;">implicit</mark> ACK):

e.g. Receipt of ACK for frame 2 (RR3) followed later by ACK for frame 6 (RR7) implies acknowledgement of frames 4 and 5.

Station A maintains a list of frame numbers it is allowed to send and, Station B maintains a list of frame numbers it is prepared to <mark style="background: #FF5582A6;">receive</mark>:
- Each list cannot extend beyond the window size.
- These lists can be considered as windows.

![](https://i.imgur.com/aaY2kIx.png)

### <mark style="background: #FF5582A6;">Error Control:</mark>

Recall the purpose of Error Control: Sender and Receiver stations co-ordinate activities to recover from <mark style="background: #FF5582A6;">Lost</mark> or <mark style="background: #FF5582A6;">Damaged</mark> Frames etc.

Error Control involves enhancing Flow Control techniques with additional functionality such as:
- <mark style="background: #FF5582A6;">Transmission Timers:</mark> Sender stations set a timer for each frame transmitted and takes action when a timer expires.
- <mark style="background: #FF5582A6;">Negative ACKs:</mark> A Receiver station can reject an out-of- sequence/damaged frame with a REJ(5) or SREJ(4) message.

Example Error Control techniques include: <mark style="background: #FF5582A6;">Go-Back-N</mark> and <mark style="background: #FF5582A6;">Selective Reject</mark>: Both techniques are based on the Sliding Windows Flow Control technique.

### <mark style="background: #FF5582A6;">TCP Error/Flow Control:</mark>

TCP also uses Flow Control and Error Control techniques.

Whilst similar to the <mark style="background: #FF5582A6;">Sliding Window Flow Control</mark> technique used in the Data Link layer, it differs in the following ways:
- Data is sent in <mark style="background: #FF5582A6;">Segments</mark> not <mark style="background: #FF5582A6;">Frames</mark>.
- Sequence numbers relate to <mark style="background: #FF5582A6;">Bytes</mark> not Segments. Each byte in a segment is numbered:
	- Each Segment identifies the <mark style="background: #FF5582A6;">first byte</mark> in the data field.
	- ACKs contain the number of the <mark style="background: #FF5582A6;">next byte</mark> expected.
- There are no <mark style="background: #FF5582A6;">Negative</mark> ACKs.

### <mark style="background: #FF5582A6;">TCP Flow Control:</mark>

For the effective operation of Flow Control:
- TCP Senders and Receivers maintain lists of bytes sent/received <mark style="background: #FF5582A6;">not</mark> segments.
- TCP Buffers used to hold incoming segments are measured in bytes <mark style="background: #FF5582A6;">not</mark> segments.

The next slide shows the operation of TCP’s Sliding Windows Flow Control technique.

### <mark style="background: #FF5582A6;">TCP Sliding Windows:</mark>

Here it can seen that the available buffer space decreases as data is stored in the buffer and increases as data leaves the buffer:

![](https://i.imgur.com/jamIxlK.png)

### <mark style="background: #FF5582A6;">TCP Segment Format:</mark>

![](https://i.imgur.com/nHZivQp.png)

### <mark style="background: #FF5582A6;">TCP Flow Control – Buffers and Windows:</mark>

Recall that TCP creates two buffers per socket:

<mark style="background: #FF5582A6;">These can be viewed with the netstat utility:</mark>
- One for incoming data (known as RECV-Q in netstat)
- One for outgoing data (known as SEND-Q in netstat)

Incoming buffers can easily overflow.

To prevent this, the <mark style="background: #FF5582A6;">receiving</mark> TCP entity uses a <mark style="background: #FF5582A6;">Window Mechanism</mark>.

<mark style="background: #FF5582A6;">TCP Internal Data Buffers:</mark>
![](https://i.imgur.com/R05mzTz.png)

<mark style="background: #FF5582A6;">Each end of the connection allocates a window (RECVQ buffer) to hold incoming data:</mark>
- The size of the initial window, in bytes, is set using the Window Size field during Phase 1 (Connection Initialization) when both sides exchange SYN messages.
- This is known as a <mark style="background: #FF5582A6;">Window Advertisement</mark>.

<mark style="background: #FF5582A6;">Thereafter, throughout Phase 2 (Data Exchange), all ACKs messages include a Window Advertisement:</mark>
- Again using the <mark style="background: #FF5582A6;">Window Size field</mark>.
- The window advertisement can be <mark style="background: #FF5582A6;">positive</mark> or <mark style="background: #FF5582A6;">zero</mark> depending on the available space in <mark style="background: #FF5582A6;">RECV-Q</mark>.

### <mark style="background: #FF5582A6;">Operation of Window Advertisements:</mark>

![](https://i.imgur.com/LLDxwDx.png)

### <mark style="background: #FF5582A6;">Achieving Reliability -Error Control:</mark>

In addition to Flow Control, TCP must address the following reliability problems:
- Unreliable delivery by the underlying communication system: Segments can be <mark style="background: #FF5582A6;">lost</mark>, <mark style="background: #FF5582A6;">duplicated</mark>, <mark style="background: #FF5582A6;">delayed</mark>, or delivered <mark style="background: #FF5582A6;">out-of-order</mark> by the underlying communication system (IP Layer).
- <mark style="background: #FF5582A6;">Computer reboot:</mark> During an active connection, either side may re-boot unexpectedly. Segments arriving after re-boot need to be dealt with.

### <mark style="background: #FF5582A6;">TCP Error Control:</mark>

This requires the use of some form of error control.

Interestingly to implement <mark style="background: #FF5582A6;">flow</mark> and <mark style="background: #FF5582A6;">error control</mark>, TCP is only equipped with two elements:
- Positive ACKs and Timers,
- Significantly TCP does not have a <mark style="background: #FF5582A6;">Negative ACK</mark>.

The following slide shows the operation of TCP during normal <mark style="background: #FF5582A6;">Data Exchange</mark> without error.

### <mark style="background: #FF5582A6;">TCP Data Flow – Normal Operation:</mark>

![](https://i.imgur.com/rX1UbTD.png)
![](https://i.imgur.com/Pf7fm76.png)
![](https://i.imgur.com/86FNuWq.png)

### <mark style="background: #FF5582A6;">TCP Error Control - Segment Loss:</mark>

To deal with lost or out-of-sequence segments, TCP implements a <mark style="background: #FF5582A6;">Retransmission</mark> scheme: This involves the retransmission of ACKs and/or lost segments.

<mark style="background: #FF5582A6;">For the Sender, timers play a key role in error control:</mark>
- Upon expiry of a timer (relating to an unacknowledged segment) the Sender simply re-transmits the segment,
- A key question is “How long should TCP wait before retransmitting?”

For the Receiver, sequence numbers play a key role in detecting <mark style="background: #FF5582A6;">lost</mark> or <mark style="background: #FF5582A6;">out-of-sequence</mark> segments: A previous ACK is re-transmitted in response until the situation is rectified.

![](https://i.imgur.com/gzEfkz0.png)

### <mark style="background: #FF5582A6;">Factors affecting TCP’s Retransmission scheme:</mark>

How long should a Sending TCP entity wait before re-transmitting a segment?

The answer depends upon two factors:
- The underlying network architecture, and,
- Traffic levels across the network.

TCP takes a measure of the delay between sending a segment and receiving an ACK. This is known as Round-Trip Time (RTT).

TCP uses the value for RTT to determine an appropriate value for the re-transmission timer (RTO - Retransmission Timeout).

### <mark style="background: #FF5582A6;">Calculation of Retransmission Timeout (RTO):</mark>

For each active connection, the RTT is continuously monitored: It represents the <mark style="background: #FF5582A6;">network latency</mark>.

TCP <mark style="background: #FF5582A6;">adapts</mark> its RTO timer to match the varying RTT values across the network:
- It uses a <mark style="background: #FF5582A6;">weighted</mark> average of <mark style="background: #FF5582A6;">RTT</mark> and a variance factor,
- It continuously re-calculates a value for RTO.

### <mark style="background: #FF5582A6;">TCP’s Adaptive Retransmission Scheme:</mark>

This is known as an <mark style="background: #FF5582A6;">adaptive retransmission</mark> scheme and is the key to TCP’s success.

This adaptability helps TCP to react <mark style="background: #FF5582A6;">quickly</mark> to changes in traffic levels and to <mark style="background: #FF5582A6;">maximise</mark> throughput on each connection.