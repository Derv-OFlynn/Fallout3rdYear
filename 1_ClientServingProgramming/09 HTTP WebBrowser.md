### <mark style="background: #FF5582A6;">WWW - Hypertext and Hypermedia:</mark>

The Web is a <mark style="background: #FF5582A6;">distributed hypermedia</mark> system that supports interactive access to Hypermedia documents (aka <mark style="background: #FF5582A6;">Resources</mark>).

<mark style="background: #FF5582A6;">Hypermedia</mark> (as opposed to <mark style="background: #FF5582A6;">Hypertext</mark>) Resources
potentially contain:
- Different types of information including: text, pictures, graphics, audio etc. Examples include: HTML files, image files, query results etc.
- <mark style="background: #FF5582A6;">Hyperlinks</mark> to other Resources,

From a Network Programming perspective these Resources are treated as <mark style="background: #FF5582A6;">Data</mark>.

### <mark style="background: #FF5582A6;">WWW and the Client-server paradigm:</mark>

The distributed nature of the Web means that the Resources/Data are potentially spread across a number of computers across the Internet.

This lends itself well to the Client-server paradigm as follows:
- <mark style="background: #FF5582A6;">On the Client-side:</mark> Here sits the consumer of the Resources/Data i.e. the end-users. They typically interact with a client application known as a Browser.
- <mark style="background: #FF5582A6;">On the Server-side:</mark> Here is where the resource repositories are located i.e. on a remote server-class machine. Access to these Resources is typically controlled by a Web server.

### <mark style="background: #FF5582A6;">Problems to be addressed:</mark>

However, this distribution of Resources also introduces a number of potential problems:
- The Resources may be updated, moved or removed without notification to the client applications,
- Accessing Resources on remote host machines has implications for network bandwidth usage.
- These problems can affect the end-user experience and, the network.

### <mark style="background: #FF5582A6;">Client-server interaction - HTTP:</mark>

Browsers and servers interact with each other using the <mark style="background: #FF5582A6;">HyperText Transfer Protocol</mark> (<mark style="background: #FF5582A6;">HTTP</mark>).

This is a <mark style="background: #FF5582A6;">network protocol</mark> used to deliver virtually all Resources on the Web:
- The Browser client sends <mark style="background: #FF5582A6;">HTTP Request</mark> messages to a Web Server. These messages typically (but not always) contain requests for a Resource,
- The Web server returns <mark style="background: #FF5582A6;">HTTP Response</mark> messages to the clients. These messages typically contain Resources/Data (but not always).

### <mark style="background: #FF5582A6;">Operation of Web Browsers and Servers:</mark>

In order to appreciate the potential problems to be addressed when developing Browsers and Web servers it is important to understand their operation.

Web Servers perform a straightforward task over and over again:
- Accept connection requests from clients,
- Accept and parse incoming HTTP Requests,
- Retrieve and return HTTP Responses indicating success or failure.
- Close the connection.

### <mark style="background: #FF5582A6;">Browser Architecture:</mark>

Web browsers are much more complex in their operation. This can best seen from their architecture (see next slide).

The functions of a Browser include:
- Rendering and displaying disparate (different types) resources to the user,
- User interaction the user,
- Initiating interaction with Web servers to retrieve resources or in some instances to upload resources.

The Browser provides these services seamlessly using a number of software components.

![](https://i.imgur.com/Pr4NDCf.png)

Specifically, a browser consists of the following components:
- A set of clients for uploading/retrieving Resources,
- A set of interpreters for displaying/rendering Resources,
- A Controller to manage them all. The Controller is responsible for: Interpreting user input via the keyboard and mouse clicks and invoking interpreter and client components at the appropriate time.
All browsers minimally contain a basic HTTP client, a basic HTML interpreter and, a Controller.

Modern Browsers contain much more.

# <mark style="background: #BABD00;">SLIDE 9</mark>
