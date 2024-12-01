The VMs are on Ubuntu Linux 14.04

<mark style="background: #FF5582A6;">Adapter 1 (both machines):</mark>
- Configured as a NAT adapter
- "Network Adapter" is enabled
- "Cable Connected" is enabled
- "Port forwarding" is enabled

<mark style="background: #FF5582A6;">Adapter 2 (both machines):</mark>
- Configured as internal network adapter
- "Network Adapter" is enabled
- "Cable Connected" is enabled

WinSCP is an application for doing file transfer.

To compile using gcc:
```CLI
gcc -c -std=gnu99 filename.c
gcc -o destinationExecutableName filename.o
```

The `".o"` file suffix means object file.

server files do not usually have suffixes

Use ``ls -l`` to view the files and their permissions in your current directory 

Use `chmod xxx filename` to change the permissions (using the numbers 0-7)

The ``netstat`` command displays various network related information such as network connections, routing tables, interface statistics, masquerade connections, multicast memberships etc.,

http is on port 80

sudo is used in linux to run commands safely

<mark style="background: #FF5582A6;">There are four byte ordering functions to consider:</mark>
- ``htons()`` – converts host 16-bit value to network byte order 
- ``htonl()`` – converts host 32-bit value to network byte order
- ``ntohs()`` – converts 16-bit network value to host byte order
- ``ntohl()`` – converts 32-bit network value to host byte order

``ht`` - host (if at the beginning)
`h` - host (if at the end)
`nt` - network (if at the beginning)
`n` - network (if at the end)
``s`` - short (i.e. 16 bits)
`l` - long (i.e. 32 bits)

<mark style="background: #FF5582A6;">Structure of daytimeServer:</mark>
1. Initialise num of connections
2. Main function
3. send buffer
4. check if argc has the correct amount of vars
5. convert port number from ascii to int
6. Initialise servSock and call SOCKET() on it to turn it into a connected socket
7. Initialise the server address structure, zero it out. Tell it to use IPv4. Accept connections on any available interface. Store port num in network byte order.
8. BIND the server socket
9. LISTEN on the server socket
10. begin infinite server loop
11. ACCEPT the client socket.
12. get time
13. print time to sendbuffer
14. Initialise numBytesSent with SEND on clntSock
14. close(clntSock)

<mark style="background: #FF5582A6;">echoServer.c structure:</mark>
1. Initialise num of connections
2. Main function
3. Initialise send buffer and receive buffer
4. Check if argc has correct number of parameters
5. Convert port number from ascii to int
6. initialise servSock
7. SOCKET servSock
8. Initialise the server address structure, zero it out. Tell it to use IPv4. Accept connections on any available interface. Store port num in netowrk byte order.
9. BIND servSock
10. LISTEN on servSock
11. Infinite loop
12. initialise clntSock by calling connect on servSock.
11. While the amount of bytes is in the buffer is smaller than the amount of bytes written, write the byte to screen. 
12. Break when ``"\r\n"`` found -> enter
13. Copy the received message into snedbuffer (snprintf)
14. SEND the sendbuffer to the clntSock
15. close(clntSock)

<mark style="background: #FF5582A6;">httpServer.c structure:</mark>
1. Initialise num of connections
2. Main function
3. Initialise numBytes, recvLoop and totalBytes
4. Check if argc has correct number of parameters
5. Convert port number from ascii to int
6. initialise servSock
7. SOCKET servSock
8. Initialise the server address structure, zero it out. Tell it to use IPv4. Accept connections on any available interface. Store port num in netowrk byte order.
9. BIND servSock
10. LISTEN on servSock
11. infinite server loop
12. Initialise clntSock by calling ACCEPT on servSock
13. Initialise client vars (recvLoop, totalBytes, uri, sendbuffer, recvbuffer)
14. While loop until recvLoop reaches 0
15. initialise numBytes by calling RECV on client sock
16. increment totalBytes by numBytes
17. end loop either if totalBytes >= Bufsize -2 or if it reads "\r\n\r\n"
18. Parse the http request using sscanf on the receive buffer and read the three strings into discard1, uri and discard2
19. compare uri and "/favicon.ico" using strcmp. If the same, print that you found it
20. null complete the recvbuffer and output recbuffer to stdout
21. compare uri and "/index.html" using strcmp. If the same, print the homepage. If different, print error page.
22. initialise numBytesSent by calling SEND on clntSock
23. close(clntSock)

![](https://i.imgur.com/20vSvhc.png)

``"\r\n\r\n"`` signals the end of a HTTP message

<mark style="background: #FF5582A6;">SOCKET:</mark>
```C
int servSock; 
if ((servSock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0)
		DieWithSystemMessage("socket() failed");
```

<mark style="background: #FF5582A6;">BIND:</mark>
```C
if (bind(servSock, (struct sockaddr*) &servAddr, sizeof(servAddr)) < 0)
	DieWithSystemMessage("bind() failed");
```

<mark style="background: #FF5582A6;">LISTEN:</mark>
```C
if (listen(servSock, MAXPENDING) < 0)
	DieWithSystemMessage("listen() failed");
```

<mark style="background: #FF5582A6;">ACCEPT:</mark>
```C
int clntSock = accept(servSock, (struct sockaddr *) NULL, NULL);
```

<mark style="background: #FF5582A6;">RECV:</mark>
```C
while ((numBytes = recv(clntSock, recvbuffer, BUFSIZE - 1, 0)) > 0) {
	recvbuffer[numBytes] = '\0';  // Null-terminate the received string
	fputs(recvbuffer, stdout);
}
```

<mark style="background: #FF5582A6;">SEND:</mark>
```C
ssize_t numBytesSent = send(clntSock, sendbuffer, strlen(sendbuffer), 0);
```

<mark style="background: #FF5582A6;">CLOSE:</mark>
```C
close(clntSock);
```

### <mark style="background: #FF5582A6;">daytimeServer.c</mark>
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include "Practical.h"
#include <unistd.h>
#include	<time.h>

static const int MAXPENDING = 5;

int main(int argc, char *argv[]) {
	time_t	ticks;  
	char sendbuffer[BUFSIZE];  
	
	if (argc != 2) 
		DieWithUserMessage("Parameter(s)", "<Server Port>");
	
	in_port_t servPort = atoi(argv[1]); 

	int servSock; 
	if ((servSock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0)
		DieWithSystemMessage("socket() failed");
	
	
	struct sockaddr_in servAddr;
	memset(&servAddr, 0, sizeof(servAddr));       
	servAddr.sin_family = AF_INET;                
	servAddr.sin_addr.s_addr = htonl(INADDR_ANY); 
	servAddr.sin_port = htons(servPort);          
	
	
	if (bind(servSock, (struct sockaddr*) &servAddr, sizeof(servAddr)) < 0)
		DieWithSystemMessage("bind() failed");
	
	
	if (listen(servSock, MAXPENDING) < 0)
		DieWithSystemMessage("listen() failed");
	
	for (;;) { 
    
    
    int clntSock = accept(servSock, (struct sockaddr *) NULL, NULL);
    if (clntSock < 0)
      DieWithSystemMessage("accept() failed");
	
    
    snprintf(sendbuffer, sizeof(sendbuffer), "%.24s\r\n", ctime(&ticks));
    ssize_t numBytesSent = send(clntSock, sendbuffer, strlen(sendbuffer), 0);  
    if (numBytesSent < 0)
      DieWithSystemMessage("send() failed");
	
	close(clntSock);

  }   
  
}
```

### <mark style="background: #FF5582A6;">daytimeServer.c COMMENTED:</mark>

```C
#include <stdio.h>          // For standard I/O functions
#include <stdlib.h>         // For general-purpose functions like atoi
#include <string.h>         // For string handling functions like memset
#include <sys/types.h>      // For data types used in socket programming
#include <sys/socket.h>     // For socket API functions
#include <netinet/in.h>     // For Internet address structures
#include <arpa/inet.h>      // For functions like htonl and htons
#include "Practical.h"      // Custom utility functions for error handling
#include <unistd.h>         // For close() to terminate socket connections
#include <time.h>           // For time-related functions like ctime

// Maximum number of pending connections in the queue
static const int MAXPENDING = 5;

int main(int argc, char *argv[]) {
    time_t ticks;                          // Variable to hold the current time
    char sendbuffer[BUFSIZE];              // Buffer to store the formatted time string

    // Ensure the correct number of arguments are provided (1 parameter: the server port)
    if (argc != 2) 
        DieWithUserMessage("Parameter(s)", "<Server Port>");

    // Convert the port number from string to integer
    in_port_t servPort = atoi(argv[1]);

    // Create a socket for the server
    // Creates a TCP socket in the IPv4 domain
    int servSock; 
    if ((servSock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0)
        DieWithSystemMessage("socket() failed");

    // Initialise the server address structure
    struct sockaddr_in servAddr;
    memset(&servAddr, 0, sizeof(servAddr));       // Zero out the structure
    servAddr.sin_family = AF_INET;                // Use IPv4 address family
    servAddr.sin_addr.s_addr = htonl(INADDR_ANY); // Accept connections on any available interface
    servAddr.sin_port = htons(servPort);          // Store port number in network byte order

    // Bind the socket to the specified address and port
    if (bind(servSock, (struct sockaddr*) &servAddr, sizeof(servAddr)) < 0)
        DieWithSystemMessage("bind() failed");

    // Set the socket to listen for incoming connections
    if (listen(servSock, MAXPENDING) < 0)
        DieWithSystemMessage("listen() failed");

    // Server loop to handle multiple client connections
    for (;;) {
        // Accept an incoming client connection
        int clntSock = accept(servSock, (struct sockaddr *) NULL, NULL);
        if (clntSock < 0)
            DieWithSystemMessage("accept() failed");

        // Get the current time and format it into a string
        ticks = time(NULL); // Get current time in seconds since the epoch
        snprintf(sendbuffer, sizeof(sendbuffer), "%.24s\r\n", ctime(&ticks)); // Format time into sendbuffer

        // Send the formatted time to the client
        ssize_t numBytesSent = send(clntSock, sendbuffer, strlen(sendbuffer), 0);  
        if (numBytesSent < 0)
            DieWithSystemMessage("send() failed");

        // Close the connection to the client
        close(clntSock);
    }

    // The program should never reach here due to the infinite loop
    return 0; 
}

```

### <mark style="background: #FF5582A6;">daytimeClient.c</mark>
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include "Practical.h"

int main(int argc, char *argv[]) {
	char recvbuffer[BUFSIZE]; 
	int numBytes = 0; 

	if (argc < 3) 
    DieWithUserMessage("Parameter(s)",
        "<Server Address> <Server Port>");

	char *servIP = argv[1];     
  
	in_port_t servPort = atoi(argv[2]);  

	
	int sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
	if (sock < 0)
		DieWithSystemMessage("socket() failed");

	
	struct sockaddr_in servAddr;
	memset(&servAddr, 0, sizeof(servAddr));
	servAddr.sin_family = AF_INET;
	
	int rtnVal = inet_pton(AF_INET, servIP, &servAddr.sin_addr.s_addr);
	if (rtnVal == 0)
		DieWithUserMessage("inet_pton() failed", "invalid address string");
	else if (rtnVal < 0)
		DieWithSystemMessage("inet_pton() failed");
	servAddr.sin_port = htons(servPort);    // Server port

  
	if (connect(sock, (struct sockaddr *) &servAddr, sizeof(servAddr)) < 0)
		DieWithSystemMessage("connect() failed");

	while ((numBytes = recv(sock, recvbuffer, BUFSIZE - 1, 0)) > 0) {
		recvbuffer[numBytes] = '\0';
		fputs(recvbuffer, stdout); 
			
		}
    if (numBytes < 0)
      DieWithSystemMessage("recv() failed");
		
  
	fputc('\n', stdout);

	close(sock);  
	exit(0);
}
```

#### <mark style="background: #FF5582A6;">daytimeClient.c COMMENTED:</mark>

```C
#include <stdio.h>          // For standard I/O functions (e.g., fputs, fputc)
#include <stdlib.h>         // For general-purpose functions like atoi and exit
#include <string.h>         // For string handling functions like memset
#include <unistd.h>         // For close() to terminate socket connections
#include <sys/types.h>      // For data types used in socket programming
#include <sys/socket.h>     // For socket API functions (e.g., socket, connect)
#include <netinet/in.h>     // For Internet address structures
#include <arpa/inet.h>      // For functions like inet_pton to parse IP addresses
#include "Practical.h"      // Custom utility functions for error handling

int main(int argc, char *argv[]) {
    char recvbuffer[BUFSIZE];    // Buffer to store data received from the server
    int numBytes = 0;            // Number of bytes received in a single `recv` call

    // Ensure the correct number of arguments are provided: server IP and port
    if (argc < 3) 
        DieWithUserMessage("Parameter(s)", "<Server Address> <Server Port>");

    // Extract the server IP address and port number from command-line arguments
    char *servIP = argv[1];        // Server IP address as a string
    in_port_t servPort = atoi(argv[2]);  // Convert the port string to an integer

    // Create a socket for the client
    int sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP); // TCP socket
    if (sock < 0)
        DieWithSystemMessage("socket() failed");

    // Set up the server address structure
    struct sockaddr_in servAddr;
    memset(&servAddr, 0, sizeof(servAddr));       // Zero out the structure
    servAddr.sin_family = AF_INET;                // Use IPv4 address family

    // Convert the IP address from string to network byte order
    int rtnVal = inet_pton(AF_INET, servIP, &servAddr.sin_addr.s_addr);
    if (rtnVal == 0)
        DieWithUserMessage("inet_pton() failed", "invalid address string");
    else if (rtnVal < 0)
        DieWithSystemMessage("inet_pton() failed");

    // Convert the server port to network byte order and store it
    servAddr.sin_port = htons(servPort);

    // Establish a connection to the server
    if (connect(sock, (struct sockaddr *) &servAddr, sizeof(servAddr)) < 0)
        DieWithSystemMessage("connect() failed");

    // Receive data from the server in a loop
    while ((numBytes = recv(sock, recvbuffer, BUFSIZE - 1, 0)) > 0) {
        recvbuffer[numBytes] = '\0'; // Null-terminate the received data
        fputs(recvbuffer, stdout);  // Print the received data to the console
    }

    // Check for errors during the receive operation
    if (numBytes < 0)
        DieWithSystemMessage("recv() failed");

    // Print a newline after all data has been received
    fputc('\n', stdout);

    // Close the socket after communication is complete
    close(sock);

    // Exit the program successfully
    exit(0);
}
```

### <mark style="background: #FF5582A6;">echoServer.c</mark>
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include "Practical.h"
#include <unistd.h>

static const int MAXPENDING = 5;

int main(int argc, char *argv[]) {

	char sendbuffer[BUFSIZE], recvbuffer[BUFSIZE];
	int numBytes = 0;

	if (argc != 2)
		DieWithUserMessage("Parameter(s)", "<Server Port>");

	in_port_t servPort = atoi(argv[1]);

	int servSock;
	if ((servSock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0)
		DieWithSystemMessage("socket() failed");


	struct sockaddr_in servAddr;
	memset(&servAddr, 0, sizeof(servAddr));
	servAddr.sin_family = AF_INET;
	servAddr.sin_addr.s_addr = htonl(INADDR_ANY);
	servAddr.sin_port = htons(servPort);


	if (bind(servSock, (struct sockaddr*) &servAddr, sizeof(servAddr)) < 0)
		DieWithSystemMessage("bind() failed");


	if (listen(servSock, MAXPENDING) < 0)
		DieWithSystemMessage("listen() failed");

	for (;;) {

    	int clntSock = accept(servSock, (struct sockaddr *) NULL, NULL);
    	if (clntSock < 0)
      		DieWithSystemMessage("accept() failed");

	while ((numBytes = recv(clntSock, recvbuffer, BUFSIZE - 1, 0)) > 0) {
		recvbuffer[numBytes] = '\0';
		fputs(recvbuffer, stdout);

		if (strstr(recvbuffer, "\r\n") > 0)
			break;
		}
    	if (numBytes < 0)
      		DieWithSystemMessage("recv() failed");

	snprintf(sendbuffer, sizeof(sendbuffer), "%s", recvbuffer);
    	
	ssize_t numBytesSent = send(clntSock, sendbuffer, strlen(sendbuffer), 0);
	
	if (numBytesSent < 0)
		DieWithSystemMessage("send() failed");

	close(clntSock);

  }
}
```

### <mark style="background: #FF5582A6;">echoServer.c COMMENTED:</mark>
```C
#include <stdio.h>          // For standard I/O functions
#include <stdlib.h>         // For general-purpose functions like atoi
#include <string.h>         // For string handling functions like memset, strstr
#include <sys/types.h>      // For data types used in socket programming
#include <sys/socket.h>     // For socket API functions like socket, bind, accept
#include <netinet/in.h>     // For Internet address structures
#include <arpa/inet.h>      // For functions like htonl and htons
#include "Practical.h"      // Custom utility functions for error handling
#include <unistd.h>         // For close() to close sockets

// Maximum number of pending client connections allowed in the queue
static const int MAXPENDING = 5;

int main(int argc, char *argv[]) {
    char sendbuffer[BUFSIZE], recvbuffer[BUFSIZE]; // Buffers for sending and receiving data
    int numBytes = 0;                              // Tracks the number of bytes received

    // Check if the user provided the required server port as an argument
    if (argc != 2)
        DieWithUserMessage("Parameter(s)", "<Server Port>");

    // Convert the provided port number from a string to an integer
    in_port_t servPort = atoi(argv[1]);

    // Create a socket for the server
    int servSock;
    if ((servSock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0)
        DieWithSystemMessage("socket() failed");

    // Initialize the server address structure
    struct sockaddr_in servAddr;
    memset(&servAddr, 0, sizeof(servAddr));       // Zero out the structure
    servAddr.sin_family = AF_INET;                // Use IPv4 address family
    servAddr.sin_addr.s_addr = htonl(INADDR_ANY); // Accept connections on any network interface
    servAddr.sin_port = htons(servPort);          // Convert port number to network byte order

    // Bind the server socket to the specified address and port
    if (bind(servSock, (struct sockaddr*) &servAddr, sizeof(servAddr)) < 0)
        DieWithSystemMessage("bind() failed");

    // Set the socket to listen for incoming client connections
    if (listen(servSock, MAXPENDING) < 0)
        DieWithSystemMessage("listen() failed");

    // Server loop to handle multiple clients
    for (;;) {
        // Accept an incoming client connection
        int clntSock = accept(servSock, (struct sockaddr *) NULL, NULL);
        if (clntSock < 0)
            DieWithSystemMessage("accept() failed");

        // Loop to receive data from the client
        while ((numBytes = recv(clntSock, recvbuffer, BUFSIZE - 1, 0)) > 0) {
            recvbuffer[numBytes] = '\0';  // Null-terminate the received string
            fputs(recvbuffer, stdout);   // Print the received data to the console

            // Check for the end-of-message indicator (CRLF: "\r\n")
            if (strstr(recvbuffer, "\r\n") > 0)
                break;  // Exit the loop if end-of-message is detected
        }

        // If the `recv` function fails, handle the error
        if (numBytes < 0)
            DieWithSystemMessage("recv() failed");

        // Prepare the response by copying the received message into the send buffer
        snprintf(sendbuffer, sizeof(sendbuffer), "%s", recvbuffer);

        // Send the response back to the client
        ssize_t numBytesSent = send(clntSock, sendbuffer, strlen(sendbuffer), 0);
        if (numBytesSent < 0)
            DieWithSystemMessage("send() failed");

        // Close the client connection after sending the response
        close(clntSock);
    }
}
```

### <mark style="background: #FF5582A6;">echoClient.c</mark>
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include "Practical.h"

int main(int argc, char *argv[]) {
	char recvbuffer[BUFSIZE];
	char sendbuffer[BUFSIZE];
	int numBytes = 0;

	if (argc < 3 || argc > 4 )
    		DieWithUserMessage("Parameter(s)", "<Server Address> <Server Port> <String Message>");

	char *servIP = argv[1];
	char *echoString = argv[3];
	in_port_t servPort = atoi(argv[2]);

	int sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
	if (sock < 0)
		DieWithSystemMessage("socket() failed");


	struct sockaddr_in servAddr;
	memset(&servAddr, 0, sizeof(servAddr));
	servAddr.sin_family = AF_INET;

	int rtnVal = inet_pton(AF_INET, servIP, &servAddr.sin_addr.s_addr);
	if (rtnVal == 0)
		DieWithUserMessage("inet_pton() failed", "invalid address string");
	else if (rtnVal < 0)
		DieWithSystemMessage("inet_pton() failed");
	servAddr.sin_port = htons(servPort);


	if (connect(sock, (struct sockaddr *) &servAddr, sizeof(servAddr)) < 0)
		DieWithSystemMessage("connect() failed");

	size_t echoStringLen  = strlen(echoString);


    	snprintf(sendbuffer, sizeof(sendbuffer), "%s\r\n", echoString);
    	ssize_t numBytesSent = send(sock, sendbuffer, strlen(sendbuffer), 0);
    	if (numBytesSent < 0)
      		DieWithSystemMessage("send() failed");

	while ((numBytes = recv(sock, recvbuffer, BUFSIZE - 1, 0)) > 0) {
		recvbuffer[numBytes] = '\0';
		fputs(recvbuffer, stdout);
		}
    	if (numBytes < 0)
      		DieWithSystemMessage("recv() failed");

	fputc('\n', stdout);

	close(sock);
	exit(0);
}
```

### <mark style="background: #FF5582A6;">echoClient.c COMMENTED:</mark>

```C
#include <stdio.h>          // For standard I/O functions like printf, fputs
#include <stdlib.h>         // For general-purpose functions like atoi and exit
#include <string.h>         // For string handling functions like memset and strlen
#include <unistd.h>         // For close() to close sockets
#include <sys/types.h>      // For data types used in socket programming
#include <sys/socket.h>     // For socket API functions like socket, connect, send, recv
#include <netinet/in.h>     // For Internet address structures
#include <arpa/inet.h>      // For functions like inet_pton to handle IP addresses
#include "Practical.h"      // Custom utility functions for error handling

int main(int argc, char *argv[]) {
    char recvbuffer[BUFSIZE];     // Buffer for receiving data from the server
    char sendbuffer[BUFSIZE];     // Buffer for sending data to the server
    int numBytes = 0;             // Tracks the number of bytes received

    // Validate the number of arguments provided by the user
    if (argc < 3 || argc > 4)     // Requires exactly 3 arguments: server IP, port, and message
        DieWithUserMessage("Parameter(s)", "<Server Address> <Server Port> <String Message>");

    char *servIP = argv[1];       // First argument: server IP address
    char *echoString = argv[3];   // Third argument: message to be sent to the server
    in_port_t servPort = atoi(argv[2]); // Second argument: server port, converted to an integer

    // Create a socket for connecting to the server
    int sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
    if (sock < 0)
        DieWithSystemMessage("socket() failed");

    // Initialize the server address structure
    struct sockaddr_in servAddr;
    memset(&servAddr, 0, sizeof(servAddr));  // Zero out the structure
    servAddr.sin_family = AF_INET;           // Use IPv4 address family

    // Convert the server IP address from text to binary format
    int rtnVal = inet_pton(AF_INET, servIP, &servAddr.sin_addr.s_addr);
    if (rtnVal == 0)
        DieWithUserMessage("inet_pton() failed", "invalid address string"); // Invalid IP format
    else if (rtnVal < 0)
        DieWithSystemMessage("inet_pton() failed"); // System error
    servAddr.sin_port = htons(servPort);      // Convert port number to network byte order

    // Connect to the server
    if (connect(sock, (struct sockaddr *)&servAddr, sizeof(servAddr)) < 0)
        DieWithSystemMessage("connect() failed");

    // Calculate the length of the message to be sent
    size_t echoStringLen = strlen(echoString);

    // Prepare the message with a newline character for proper transmission
    snprintf(sendbuffer, sizeof(sendbuffer), "%s\r\n", echoString);

    // Send the message to the server
    ssize_t numBytesSent = send(sock, sendbuffer, strlen(sendbuffer), 0);
    if (numBytesSent < 0)
        DieWithSystemMessage("send() failed");

    // Receive the echoed response from the server
    while ((numBytes = recv(sock, recvbuffer, BUFSIZE - 1, 0)) > 0) {
        recvbuffer[numBytes] = '\0'; // Null-terminate the received string
        fputs(recvbuffer, stdout);  // Print the received data to the console
    }

    // If `recv` fails, handle the error
    if (numBytes < 0)
        DieWithSystemMessage("recv() failed");

    // Print a newline for formatting purposes
    fputc('\n', stdout);

    // Close the socket and clean up
    close(sock);
    exit(0);  // Exit the program successfully
}
```

### <mark style="background: #FF5582A6;">httpServer.c</mark>
```C
//This application is a very simplistic server that simply returns requested file or error file contents using HTTP with simplistic HTTP Headers 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include "Practical.h"
#include <unistd.h>
#include <sys/stat.h>

static const int MAXPENDING = 5; 

int main(int argc, char *argv[]) {
	int numBytes = 0, char_in, count = 0, size = 0, recvLoop = 0, totalBytes =0;
	char recvbuffer[BUFSIZE], sendbuffer[BUFSIZE], path[200] ={'.'}, discard1[50], discard2[50]; 

	struct stat st;
	FILE * hFile; //declare file pointer
	
	 if (argc != 2) 
	    DieWithUserMessage("Parameter(s)", "<Server Port>");

	  in_port_t servPort = atoi(argv[1]); 

 
	  int servSock; 

	  if ((servSock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0)
		DieWithSystemMessage("socket() failed");

  
	struct sockaddr_in servAddr;                  
	memset(&servAddr, 0, sizeof(servAddr));      
	  servAddr.sin_family = AF_INET;               
	  servAddr.sin_addr.s_addr = htonl(INADDR_ANY); 
	  servAddr.sin_port = htons(servPort);          
  
  if (bind(servSock, (struct sockaddr*) &servAddr, sizeof(servAddr)) < 0)
    	DieWithSystemMessage("bind() failed");

  if (listen(servSock, MAXPENDING) < 0)
	DieWithSystemMessage("listen() failed");

  for (;;) {
  
    int clntSock = accept(servSock, (struct sockaddr *) NULL, NULL);

    if (clntSock < 0)
	DieWithSystemMessage("accept() failed");

		recvLoop = 1;
		totalBytes = 0;
		memset (sendbuffer, '\0', sizeof(sendbuffer));
		memset (recvbuffer, '\0', sizeof(recvbuffer));
		
		while (recvLoop  > 0) 
		{  

			numBytes = recv(clntSock, (recvbuffer+totalBytes), 1, 0); //note the one byte limitation -  argument three	
			totalBytes += numBytes; //updating the off-set

			if((totalBytes >= (BUFSIZE-2)) || (strstr(recvbuffer,"\r\n\r\n")>0))
				recvLoop = 0;  //Testing to ensure recv() does not over-write the recvbuffer OR looking for \r\n\r\n
					
		}


    if (numBytes < 0)
	DieWithSystemMessage("recv() failed");

	sscanf(recvbuffer, "%s %s %s", discard1, (path+1), discard2);
	printf("\npath contains: %s\n", path);


	if(strcmp(path, "./favicon.ico") == 0)
	{
		printf("\n\nFound and ignored favicon.ico\n\n");		
	}
	else
	{
		if(strcmp(path, "./") == 0)
		{
			strcpy(path, "./index.html");		//reset the path1 buffer back to "."
		}

		hFile = fopen(path, "r");  	//open the requested file			

		if (hFile == NULL) 	 		//if requested file does not exist
		{
			strcpy(path, "./error.html");		//reset the path1 buffer back to "."

			hFile = fopen(path, "r");  	//open the error file

			stat(path, &st);
			size = st.st_size;

			printf("\nERROR.HTML File size is: %d\n", size);
			snprintf(sendbuffer, sizeof(sendbuffer), "HTTP/1.1 404 File Not Found\r\nContent-Length: %d\r\nCache-Control: no-cache\r\nConnection: close\r\n\r\n", size); 
		}
		else
		{

			stat(path, &st);
			size = st.st_size;

			printf("\nRequested file size is: %d\n", size);
			snprintf(sendbuffer, sizeof(sendbuffer), "HTTP/1.1 200 Okay\r\nContent-Length: %d\r\nCache-Control: no-cache\r\nConnection: close\r\n\r\n", size); 
		}
	 
		ssize_t numBytesSent = send(clntSock, sendbuffer, strlen(sendbuffer), 0);
		if (numBytesSent < 0)
			DieWithSystemMessage("send() failed");

		strcpy(sendbuffer,"");  				//empty the outgoing buffer

		while((char_in = fgetc(hFile))!= EOF)   //reading one char at-a-time from the open file
		{
			sendbuffer[count] = char_in;	//storing the char in the outgoing buffer
			count++;				//increment the buffer index ready for next character
		}

		numBytesSent = send(clntSock, sendbuffer, count, 0);
		if (numBytesSent < 0)
			DieWithSystemMessage("send() failed");

		size = 0;
		count = 0;	
		fclose(hFile);			//close the file
		strcpy(path, ".");
	}//reset the path1 buffer back to "."
	close(clntSock); // Close client socket
  } //END FOR LOOP
  // NOT REACHED
}
```

### <mark style="background: #FF5582A6;">httpServer.c COMMENTED:</mark>

```C
#include <stdio.h>            // Standard I/O functions
#include <stdlib.h>           // General-purpose functions like atoi, exit
#include <string.h>           // String manipulation functions
#include <sys/types.h>        // Data types for sockets
#include <sys/socket.h>       // Socket API
#include <netinet/in.h>       // Internet address structures
#include <arpa/inet.h>        // Helper functions for IP addresses
#include <unistd.h>           // POSIX API (close, etc.)
#include <sys/stat.h>         // File statistics
#include "Practical.h"        // Custom error-handling utilities

// Define HTTP response templates for home and error pages
#define HOME_PAGE "HTTP/1.0 200 File Found\r\nContent-Length: 131\r\nConnection: close\r\nServer: httpserver\r\n\r\n<HTML><HEAD><TITLE>File  Found</TITLE></HEAD><BODY><h2>FILE Found</h2><hr><p>Your requested INDEX FILE was found.</p></BODY></HTML>"
#define ERROR_PAGE "HTTP/1.0 404 File Not Found\r\nContent-Length: 142\r\nConnection: close\r\n\r\n<HTML><HEAD><TITLE>File NOT Found</TITLE></HEAD><BODY><h2>FILE NOT Found</h2><hr><p>Your requested INDEX FILE was NOT found.</p></BODY></HTML>"

// Maximum number of pending connections
static const int MAXPENDING = 2;

int main(int argc, char *argv[]) {
    int recvLoop = 0, numBytes = 0, totalBytes = 0;
    char recvbuffer[BUFSIZE], sendbuffer[BUFSIZE], uri[200] = {""}, discard1[50], discard2[50];

    // Ensure exactly one argument is passed: the server port
    if (argc != 2) 
        DieWithUserMessage("Parameter(s)", "<Server Port>");

    in_port_t servPort = atoi(argv[1]); // Convert port to integer

    // Create the server socket
    int servSock; 
    if ((servSock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0)
        DieWithSystemMessage("socket() failed");

    // Configure server address structure
    struct sockaddr_in servAddr;
    memset(&servAddr, 0, sizeof(servAddr));       
    servAddr.sin_family = AF_INET;                
    servAddr.sin_addr.s_addr = htonl(INADDR_ANY); // Accept connections from any address
    servAddr.sin_port = htons(servPort);          // Convert port to network byte order

    // Bind the socket to the specified port
    if (bind(servSock, (struct sockaddr*) &servAddr, sizeof(servAddr)) < 0)
        DieWithSystemMessage("bind() failed");

    // Listen for incoming connections
    if (listen(servSock, MAXPENDING) < 0)
        DieWithSystemMessage("listen() failed");

    // Server runs indefinitely
    for (;;) {
        // Accept a client connection
        int clntSock = accept(servSock, (struct sockaddr *) NULL, NULL);
        if (clntSock < 0)
            DieWithSystemMessage("accept() failed");

        // Initialize variables for each client
        recvLoop = 1;
        totalBytes = 0;
        memset(uri, '\0', sizeof(uri));
        memset(sendbuffer, '\0', sizeof(sendbuffer));
        memset(recvbuffer, '\0', sizeof(recvbuffer));

        // Receive the HTTP request
        while (recvLoop > 0) {
            numBytes = recv(clntSock, (recvbuffer + totalBytes), 1, 0); // Read 1 byte at a time
            totalBytes += numBytes; 

            // Stop receiving if buffer is full or HTTP header is complete
            if ((totalBytes >= (BUFSIZE - 2)) || (strstr(recvbuffer, "\r\n\r\n") > 0))
                recvLoop = 0;
        }
        if (numBytes < 0)
            DieWithSystemMessage("recv() failed");

        // Parse the HTTP request
        sscanf(recvbuffer, "%s %s %s\r\n", discard1, uri, discard2);  

        // Ignore requests for favicon.ico
        if (strcmp(uri, "/favicon.ico") == 0) {
            printf("\n\nFound and ignored favicon.ico\n\n");
            close(clntSock);
            continue;
        }

        // Log the received request
        recvbuffer[totalBytes] = '\0'; 
        fputs(recvbuffer, stdout);

        // Generate the appropriate HTTP response
        if (strcmp(uri, "/index.html") == 0) {
            snprintf(sendbuffer, sizeof(sendbuffer), HOME_PAGE);
        } else {
            snprintf(sendbuffer, sizeof(sendbuffer), ERROR_PAGE);
        }

        // Send the HTTP response
        ssize_t numBytesSent = send(clntSock, sendbuffer, strlen(sendbuffer), 0);
        if (numBytesSent < 0)
            DieWithSystemMessage("send() failed");

        // Close the client socket
        close(clntSock);
    }
}
```
### <mark style="background: #FF5582A6;">httpClient.c</mark>
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include "Practical.h"

int main(int argc, char *argv[]) {

	char sendbuffer[BUFSIZE], recvbuffer[BUFSIZE], discard[20];
	int numBytes = 0; 

	if (argc < 3 || argc > 4) 
		DieWithUserMessage("Parameter(s)", "<Server Address> <Server Port> <HTTP Request>");

	char *servIP = argv[1];     
	char *httpRequest = argv[3]; 

	in_port_t servPort = atoi(argv[2]);

	int sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
	if (sock < 0)
		DieWithSystemMessage("socket() failed");

	struct sockaddr_in servAddr;         

	memset(&servAddr, 0, sizeof(servAddr)); 

	servAddr.sin_family = AF_INET;

	int rtnVal = inet_pton(AF_INET, servIP, &servAddr.sin_addr.s_addr);
	if (rtnVal == 0)
		DieWithUserMessage("inet_pton() failed", "invalid address string");
	else if (rtnVal < 0)
		DieWithSystemMessage("inet_pton() failed");

	servAddr.sin_port = htons(servPort);    // Server port


	if (connect(sock, (struct sockaddr *) &servAddr, sizeof(servAddr)) < 0)
		DieWithSystemMessage("connect() failed");

	snprintf(sendbuffer, sizeof(sendbuffer), "%s", httpRequest); 
	  
	ssize_t numBytesSent = send(sock, sendbuffer, strlen(sendbuffer), 0);

	if (numBytesSent < 0)
		  DieWithSystemMessage("send() failed");


	while ((numBytes = recv(sock, recvbuffer, BUFSIZE, 0)) > 0) {
		recvbuffer[numBytes] = '\0';    
		fputs(recvbuffer, stdout);      

		if (strstr(recvbuffer,"</html>")>0) 
			break;
		}
	if (numBytes < 0)
		DieWithSystemMessage("recv() failed");
			
	fputc('\n', stdout); 

	close(sock);
	exit(0);
}
```

### <mark style="background: #FF5582A6;">httpClient.c COMMENTED:</mark>

```C
#include <stdio.h>           // Standard input/output functions like printf
#include <stdlib.h>          // General-purpose functions like atoi, exit
#include <string.h>          // String manipulation functions like memset, strcmp
#include <unistd.h>          // For system calls like close()
#include <sys/types.h>       // Data types used in socket programming
#include <sys/socket.h>      // Socket API functions like socket(), connect()
#include <netinet/in.h>      // Structures and constants for Internet domain addresses
#include <arpa/inet.h>       // Functions for manipulating IP addresses
#include "Practical.h"       // Custom error-handling utilities

int main(int argc, char *argv[]) {
    char sendbuffer[BUFSIZE], recvbuffer[BUFSIZE], discard[20]; // Buffers for sending and receiving data
    int numBytes = 0;  // Variable to store the number of bytes received

    // Validate command-line arguments
    if (argc < 3 || argc > 4) 
        DieWithUserMessage("Parameter(s)", "<Server Address> <Server Port> <HTTP Request>");

    char *servIP = argv[1];      // Server IP address
    char *httpRequest = argv[3]; // HTTP request string

    in_port_t servPort = atoi(argv[2]); // Server port number

    // Create a socket
    int sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
    if (sock < 0)
        DieWithSystemMessage("socket() failed");

    // Set up the server address structure
    struct sockaddr_in servAddr;          
    memset(&servAddr, 0, sizeof(servAddr)); // Clear the structure
    servAddr.sin_family = AF_INET;         // IPv4 protocol

    // Convert IP address from text to binary form
    int rtnVal = inet_pton(AF_INET, servIP, &servAddr.sin_addr.s_addr);
    if (rtnVal == 0)
        DieWithUserMessage("inet_pton() failed", "invalid address string");
    else if (rtnVal < 0)
        DieWithSystemMessage("inet_pton() failed");

    servAddr.sin_port = htons(servPort); // Convert port number to network byte order

    // Establish a connection to the server
    if (connect(sock, (struct sockaddr *) &servAddr, sizeof(servAddr)) < 0)
        DieWithSystemMessage("connect() failed");

    // Prepare the HTTP request
    snprintf(sendbuffer, sizeof(sendbuffer), "%s", httpRequest); 
      
    // Send the HTTP request to the server
    ssize_t numBytesSent = send(sock, sendbuffer, strlen(sendbuffer), 0);
    if (numBytesSent < 0)
        DieWithSystemMessage("send() failed");

    // Receive the HTTP response from the server
    while ((numBytes = recv(sock, recvbuffer, BUFSIZE, 0)) > 0) {
        recvbuffer[numBytes] = '\0';   // Null-terminate the received data
        fputs(recvbuffer, stdout);    // Print the received data to standard output

        // Stop receiving if the closing HTML tag is detected
        if (strstr(recvbuffer, "</html>") > 0) 
            break;
    }

    // Check for errors during reception
    if (numBytes < 0)
        DieWithSystemMessage("recv() failed");

    fputc('\n', stdout); // Add a newline for clean output

    // Close the socket and exit
    close(sock);
    exit(0);
}
```