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

### <mark style="background: #FF5582A6;">Interpreter and Client components:</mark>

An example interpreter is the <mark style="background: #FF5582A6;">HTML interpreter</mark>:
- It parses documents that contain standard HTML code and renders the content to the local screen,
- Other interpreters are needed for displaying pictures, video, audio etc.

An example client is the <mark style="background: #FF5582A6;">HTTP client</mark>:
- It is used to interact with HTTP servers for the purpose of retrieving/uploading Resources,
- Other clients are needed for sending/receiving e-mail messages, file transfer using FTP etc.
- The 1st field in the destination URL identifies the client component to invoke.

### <mark style="background: #FF5582A6;">Document Transfer and HTTP:</mark>

From a Network Programming perspective we are interested in the HTTP client and its interaction with HTTP servers.

This interaction consists of an exchange of HTTP Requests and Responses:
- These are typically sent as plain-text encoded in ASCII i.e. in English, 
- This means that when viewed with a protocol analyser such as Wireshark, the Application Data field can be easily read and understood.

### <mark style="background: #FF5582A6;">HTTP Requests:</mark>

HTTP Requests originate from the HTTP client.

They support a number of operations through a set of methods:
- GET, HEAD, POST, OPTIONS, PUT, DELETE, TRACE and CONNECT.
- For the purposes of this module we shall restrict ourselves to the GET and HEAD methods,
- These two methods should adequately demonstrate the problems to be addressed.

### <mark style="background: #FF5582A6;">HTTP Responses:</mark>

HTTP Responses originate from the HTTP server.

Recall the problems previously outlined in relation to broken links, re-located Resources and Bandwidth limitations:
- HTTP includes a lot of functionality to address these problems,
- The server typically sends additional information with each transfer of data,
- This additional information allows the HTTP client to call an appropriate interpreter to display/render the Resource data, to infer an error condition etc.

### <mark style="background: #FF5582A6;">Structure of HTTP Messages:</mark>

Recall that each layer of the Protocol Hierarchy specifies a “framing-type” structure known as a <mark style="background: #FF5582A6;">Protocol Data Unit (PDU)</mark>:

Examples include: a Data Link Frame, an IP Datagram/Packet, a TCP segment etc.

HTTP is also a protocol:
- It exists in the Application layer,
- There are many other protocols that exist in the Application layer.

When talking about Application layer protocols the term PDU has no real meaning.

This is because Application layer protocols typically follow a request-response or command-response model of interaction:
- Clients typically request something from the server or, issue a command to the server,
- Servers typically respond to the Client with an indication of success or failure,
- However, sometimes servers issue requests and commands, but more on that later.

Application layer protocols are more usefully described in terms of <mark style="background: #FF5582A6;">Syntax</mark> and <mark style="background: #FF5582A6;">Semantics</mark>.

### <mark style="background: #FF5582A6;">Syntax and Semantics:</mark>

<mark style="background: #FF5582A6;">Syntax</mark> describes the structure of the request-response messages.

<mark style="background: #FF5582A6;">Semantics</mark> describes the interaction between the client and the server:
- Essentially this relates to the <mark style="background: #FF5582A6;">sequence</mark> of request/response messages,
- More usefully this can be described as “who talks first” i.e. which side issues the first message.

### <mark style="background: #FF5582A6;">Syntax of HTTP Messages:</mark>

HTTP Messages have a particular structure or format.

The format of the Requests and Responses messages are similar. Both consist of:
- An initial line,
- Zero or more Header Lines,
- A blank line, and
- An optional Message Body typically containing Resource data from a file, or a query output etc.

Specifically, the format of an HTTP message is:
```HTTP
<initial line, different for request and response>
Header1: value1
Header2: value2
Header3: value3
<Blank line>
<optional message body goes here, like file contents or query
data>
```

Initial lines and headers should end in CRLF - Specifically CR and LF here mean ASCII values 13 and 10 respectively.

This structure can more usefully described in terms of a Protocol Box Diagram:

![](https://i.imgur.com/vhY7K8g.png)

### <mark style="background: #FF5582A6;">Initial Request Line:</mark>

The initial line for a Request line has three parts, separated by spaces:
- a method name
- the local path of the requested resource
- the version of HTTP being used.

A typical request line is:
```
GET /path/to/file/index.html HTTP/1.0
```

<mark style="background: #FF5582A6;">Notes:</mark>
- GET is the most common HTTP method -it says “fetch me this resource"
- Method names are always uppercase.
- The path is the part of the URL after the host name.
- The HTTP version always takes the form "HTTP/x.x", uppercase.

### <mark style="background: #FF5582A6;">Initial Response Line:</mark>

The initial response line also has three parts separated by spaces:
- The HTTP version,
- A response status code that gives the result of the request,
- An English reason phrase describing the status code.

Typical status lines are:
- HTTP/1.0 200 OK
- HTTP/1.0 404 Not Found

<mark style="background: #FF5582A6;">Notes:</mark>
- The HTTP version is of format "HTTP/x.x".
- The status code is meant to be <mark style="background: #FF5582A6;">computer-readable</mark>. It comprises a three-digit integer, and the first digit identifies the general category of response
- The reason phrase is meant to be <mark style="background: #FF5582A6;">human-readable</mark>, and may vary.

### <mark style="background: #FF5582A6;">Header Lines:</mark>

Header lines provide information about the <mark style="background: #FF5582A6;">request</mark> or <mark style="background: #FF5582A6;">response</mark>, or about the Resource sent in the message body.

The header lines are in a particular format
- One line per header, of the form "Header-Name: value", ending with CRLF.
- This is a similar format used for email and is defined in RFC 822.
- The header name is <mark style="background: #FF5582A6;">not</mark> case-sensitive (although the value may be).

<mark style="background: #FF5582A6;">There are different versions of HTTP:</mark>
-  HTTP 1.0 is older and defines 16 headers, although none are required.
- HTTP 1.1 is newer and defines 46 headers, and one (Host:) is required in requests.
- HTTP/2.0 is the latest version and addresses some of the inefficiencies of HTTP/1.1.
- For application development purposes, this module will focus on HTTP/1.0 and HTTP/1.1

### <mark style="background: #FF5582A6;">Example Request Header Lines:</mark>

![](https://i.imgur.com/FkXQhdQ.png)

![](https://i.imgur.com/tyLMme8.png)

### <mark style="background: #FF5582A6;">Header Lines - Net-politeness:</mark>

Consider including the following headers in <mark style="background: #FF5582A6;">client</mark> requests:
- A <mark style="background: #FF5582A6;">From</mark>: header gives the email address of the person making the request or running the program. (This must be user-configurable, for privacy concerns.)
- A <mark style="background: #FF5582A6;">User-Agent</mark>: header identifies the program that's making the request, in the form <mark style="background: #FF5582A6;">"Program-name/x.xx"</mark>, where x.xx is the (mostly) alphanumeric version of the program.
- e.g. Netscape 3.0 sends the header "User-agent: Mozilla/3.0Gold".

Consider including the following headers in server responses:
- A <mark style="background: #FF5582A6;">Server</mark>: header. Similar to the <mark style="background: #FF5582A6;">User-Agent</mark>: header: it identifies the server software in the form "<mark style="background: #FF5582A6;">Program-name/x.xx</mark>".
- e.g. An Apache server might return "Server: Apache/1.2b3-dev".
- The <mark style="background: #FF5582A6;">Last-Modified</mark>: header gives the modification date (in GMT) of the resource that's being returned. It is used in caching.
- e.g. <mark style="background: #FF5582A6;">Last-Modified: Fri, 31 Dec 1999 23:59:59 GMT</mark>

### <mark style="background: #FF5582A6;">The Message Body:</mark>

A HTTP <mark style="background: #FF5582A6;">message</mark> may have a <mark style="background: #FF5582A6;">body</mark> of data sent after the header lines.

<mark style="background: #FF5582A6;">In a response:</mark>
- This is where the requested resource is returned to the client (the most common use of the message body),
- Or some explanatory text for an error condition.

<mark style="background: #FF5582A6;">In a request:</mark>
- This is where form data or uploaded files are sent to the server.

If a HTTP message includes a body, there are usually header lines in the message that describe the body. In particular,
- The <mark style="background: #FF5582A6;">Content-Type</mark>: header gives the MIME-type of the data in the body, such as text/html or image/gif.
- The <mark style="background: #FF5582A6;">Content-Length</mark>: header gives the number of bytes in the body.

### <mark style="background: #FF5582A6;">Other HTTP Methods - HEAD and POST:</mark>

Two other commonly used methods are HEAD and POST.

The HEAD Method
- Similar to a GET request, except it asks the server to return the response headers only, not the actual resource (i.e. no message body).
- Useful for checking characteristics of a resource without actually downloading it.
- The response to a HEAD request must never contain a <mark style="background: #FF5582A6;">message</mark> body.

### <mark style="background: #FF5582A6;">Other HTTP Methods - HEAD and POST:</mark>

<mark style="background: #FF5582A6;">The POST Method</mark>

A POST request is used to send data to the server to be processed in some way, like by a CGI script.

It differs from a GET request in the following ways:
- There's a block of data sent with the request, in the message body. There are usually extra headers to describe this message body, like <mark style="background: #FF5582A6;">Content-Type:</mark> and <mark style="background: #FF5582A6;">Content-Length</mark>:
- The request URI is not a resource to retrieve; it's usually a program to handle the data you're sending.

### <mark style="background: #FF5582A6;">Sample Document Transfer with HTTP:</mark>

```HTTP
GET http://www.comp.dit.ie/dbourke/ HTTP/1.1
Accept-Language: en-us,en;q=0.5
Accept:text/xml,application/xml,application/xhtml+x
ml,text/html;q=0.9,text/plain;q=0.8,image/png.
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Host: www.comp.dit.ie
Accept-Encoding: gzip,deflate
User-Agent: Mozilla/5.0 (Windows; U; Windows NT
5.1; en-US; rv:1.8.0.1) Gecko/20060111
Firefox/1.5.0.1
Cookie: PHPSESSID=13ceaac67329048c4
Keep-Alive: 300
Proxy-Connection: keep-alive
HTTP/1.1 200 OK
Pragma: no-cache
Cache-Control: no-cache
MicrosoftOfficeWebServer: 5.0_Pub
ETag: "e21ceefa6e28df"
Accept-Ranges: bytes
Content-Type: text/html
Connection: close
Date: Wed, 22 Oct 2008 14:20:12 GMT
Server: Microsoft-IIS/6.0
Content-Location:
http://www.comp.dit.ie/dbourke/index.htm
Last-Modified: Thu, 02 Oct 2008 09:12:23 GMT
Content-Length: 1837
X-Powered-By: ASP.NET
```

### <mark style="background: #FF5582A6;">HTTP Versions 1.0 and 1.1:</mark>

As mentioned there are two versions of HTTP: HTTP/1.0 and HTTP/1.1

There are some key differences between the two in the following areas (not all are listed):
- Persistent connections,
- Multi-hosting
- More efficient cache control.

### <mark style="background: #FF5582A6;">HTTP/1.0 Connections:</mark>

With HTTP 1.0 the connection between the server and the client is closed by the server immediately after the HTTP Response is transmitted.

Consider a simple HTML page containing five image tags:
- Downloading and rendering this page requires six connection establishments and cessations,
- One for the HTML page and one for each of the images. The images are downloaded separately on a separate connection.

<mark style="background: #FF5582A6;">This behaviour has implications for:</mark>
- <mark style="background: #FF5582A6;">Network bandwidth</mark> due to the amount of extra segments required to establish and terminate connections,
- <mark style="background: #FF5582A6;">Internal TCP resources</mark>. Each connection consumes resources within the TCP memory space.

### <mark style="background: #FF5582A6;">HTTP/1.1 Persistent Connections:</mark>

With HTTP 1.1, the connection between the server and the client remains open by default:
- This allows for multiple HTTP Requests to be submitted across a single connection,
- This default behaviour is not always required and it can be overridden using the Connection: header as follows: ``Connection: close\r\n``
- This is an instruction to the server to close the connection after the Resource has been returned.

### <mark style="background: #FF5582A6;">Multi-hosting:</mark>

<mark style="background: #FF5582A6;">HTTP/1.1 facilitates Multi-hosting:</mark>
- Multiple webservers sharing a single IP address,
- The problem is that each server is listening on Port 80,
- This causes problems for TCP determining which server should receive an incoming HTTP Request,
- The problem is solved using the <mark style="background: #FF5582A6;">Host</mark>: header as follows: ``Host: www.tudublin.ie``
- Its inclusion is mandatory in all HTTP/1.1 Requests.