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
