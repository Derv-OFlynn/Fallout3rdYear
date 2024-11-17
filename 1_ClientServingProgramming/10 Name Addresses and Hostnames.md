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