### <mark style="background: #FF5582A6;">Network Programming and Applications:</mark>

<mark style="background: #FF5582A6;">Previously</mark> we looked at some of the services that a network provides

A data network is a <mark style="background: #FF5582A6;">passive</mark> entity, it neither <mark style="background: #FF5582A6;">generates</mark> nor <mark style="background: #FF5582A6;">understands</mark> the data being sent.

<mark style="background: #FF5582A6;">Now</mark>, we look at computer networks from an application perspective:
- Applications that use computer networks operate in pairs; the <mark style="background: #FF5582A6;">client</mark> and the <mark style="background: #FF5582A6;">server</mark>.
- Typically these applications run on hosts that are remote from each other.
- Between the host machines there is a network across which the data must travel.

Server applications run on <mark style="background: #FF5582A6;">server-class machines</mark>:
- Sometimes these are mistakenly referred to as <mark style="background: #FF5582A6;">servers</mark>,
- <mark style="background: #FF5582A6;">Servers</mark> are applications and the machines on which they run are server-class machines.

Client applications can run on any machine.

Server applications play a vital role in modern networked applications:
- They are continuously running waiting for contact from Client applications. 

Some texts use the analogy of two people communicating over the telephone network to represent client-server communications:
- However, the analogy falls short as there are some unique challenges when writing client and server  applications which we will explore in the lab.

### <mark style="background: #FF5582A6;">Making Contact - Client Server Interaction:</mark>

How does an application know when a 
message has arrived? 

It’s not so straight forward with applications:
- Before any inter-application communication can take place an application must interact with its local protocol software to notify it to expect <mark style="background: #FF5582A6;">messages</mark> of a specific <mark style="background: #FF5582A6;">type</mark>,
- The application then waits <mark style="background: #FF5582A6;">passively</mark> for contact from remote applications.

### <mark style="background: #FF5582A6;">Client-Server Interaction:</mark>

The protocol software examines incoming messages and passes <mark style="background: #FF5582A6;">matching</mark> messages to the application.

The application that is continuously running, passively  waiting for contact from other applications is called a <mark style="background: #FF5582A6;">server</mark>.

The application that actively initiates contact with a server is called a <mark style="background: #FF5582A6;">client</mark>.

This is known as the <mark style="background: #FF5582A6;">client-server</mark> paradigm.

### <mark style="background: #FF5582A6;">Characteristics of Clients:</mark>

<mark style="background: #FF5582A6;">In general</mark>, client software has the following characteristics:
- It provides general purpose computational functionality to a user but on occasion it becomes a <mark style="background: #FF5582A6;">client application</mark>
- It is invoked directly by a user and executes for one session
- It runs locally on a user's personal computer
- It actively <mark style="background: #FF5582A6;">initiates</mark> contact with a server
- It can access multiple services but can only contact one <mark style="background: #FF5582A6;">server</mark> at a time
- It does not require specialised hardware or a sophisticated operating system

### <mark style="background: #FF5582A6;">Characteristics of Servers:</mark>

<mark style="background: #FF5582A6;">In general</mark>, server software has the following 
characteristics:
- It is a special-purpose, <mark style="background: #FF5582A6;">privileged</mark> program dedicated to providing one <mark style="background: #FF5582A6;">service</mark>
- It can handle multiple remote clients simultaneously 
- It invoked automatically upon boot-up, and executes through many sessions
- It runs on a shared computer 
- It passively waits for and accepts contact from <mark style="background: #FF5582A6;">arbitrary</mark> remote clients
- It requires powerful hardware and a sophisticated operating system

### <mark style="background: #FF5582A6;">Multiple Services on one computer:</mark>

Some server-class machines run <mark style="background: #FF5582A6;">multiple</mark> clients and servers simultaneously 
- These computers have an operating system that allows multiple application programs to execute <mark style="background: #FF5582A6;">concurrently</mark> (e.g., UNIX or Windows). 
- For each service offered there must be an associated server program executing e.g. a single computer might run a <mark style="background: #FF5582A6;">file server</mark> and a <mark style="background: #FF5582A6;">World Wide Web server</mark>
- The following diagram illustrates this

![](https://i.imgur.com/DHHduvU.png)

With <mark style="background: #FF5582A6;">multiple</mark> servers running, how can a client identify a <mark style="background: #FF5582A6;">particular</mark> server <mark style="background: #FF5582A6;">unambiguously</mark>?

Some form of addressing is required:
- Each server is assigned a unique identifier
- <mark style="background: #FF5582A6;">Clients</mark> and <mark style="background: #FF5582A6;">servers</mark> use this identifier in <mark style="background: #FF5582A6;">all</mark> interactions 

The <mark style="background: #FF5582A6;">communications paradigm</mark> is as follows:
- The server application starts execution first:
- It registers its identifier with the local protocol software
- It then waits for contact from clients

<mark style="background: #FF5582A6;">Clients</mark> contact <mark style="background: #FF5582A6;">servers</mark> by specifying the server’s <mark style="background: #FF5582A6;">location</mark> and <mark style="background: #FF5582A6;">unique identifier</mark> 

The client and server exchange messages and terminate communication