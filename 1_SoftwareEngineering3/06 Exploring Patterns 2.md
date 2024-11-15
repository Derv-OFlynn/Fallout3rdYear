### <mark style="background: #FFB8EBA6;">Context Object Pattern:</mark>

![](https://i.imgur.com/YbB0MRL.png)

<mark style="background: #FFB8EBA6;">Intent:</mark> Avoid using protocol-specific system information outside of its relevant context.  

The Command classes we used in our Web Application were <mark style="background: #FFB8EBA6;">protocol dependent</mark>.  

```JSP
public interface Command 
{  
	String execute(HttpServletRequest request, HttpServletResponse response);  
}
```

### <mark style="background: #FFB8EBA6;">Context Object Pattern:</mark>

This makes it <mark style="background: #FFB8EBA6;">difficult to test</mark> these classes outside of their context or to re-use them in another context.  

The <mark style="background: #FFB8EBA6;">Context Object</mark> pattern may be used to write these classes in a <mark style="background: #FFB8EBA6;">protocol-independent way</mark>.  

The simplest implementation of <mark style="background: #FFB8EBA6;">Context Object</mark> in this case involves using a Map (e.g. a HashMap) for storing the relevant data  

This can make it <mark style="background: #FFB8EBA6;">easy to test</mark> these new Command classes.

```Java
package command ;  
import java.util.Map;  

public interface Command {  
	String execute(Map<String, Object> map) ;  
}
```

``HttpServletRequest`` is replaced by Map  

Examine the Map interface in the Java documentation.

![](https://i.imgur.com/xxt6z7G.png)

``HttpServletRequest`` is replaced by ``Map``

``request.setAttribute( /* etc. */ )``  
is replaced by  
``myMap.put( /* etc. */ )``

As the ``ListUsersCommand`` class is <mark style="background: #FFB8EBA6;">no longer protocol-dependent</mark>, it is a simple matter to test the class without starting the web server (e.g. Tomcat).

### <mark style="background: #FFB8EBA6;">Context Object Pattern - makes testing easier:</mark>

![](https://i.imgur.com/WD52tI5.png)

![](https://i.imgur.com/qjacRZy.png)

### <mark style="background: #FFB8EBA6;">getParameterMap():</mark>

This method returns a ``java.util.Map`` of the parameters of this request. Request parameters are extra information sent with the request. For HTTP servlets, parameters are contained in the query string or posted form data.  

Note: for the map returned from the method `getParameterMap()` the <mark style="background: #FFB8EBA6;">key</mark> is of type String and the <mark style="background: #FFB8EBA6;">value</mark> is of type String[].

### <mark style="background: #FFB8EBA6;">Wrapper Patterns:</mark>

- Adapter  
- Decorator  
- Proxy  
- Bridge

### <mark style="background: #FFB8EBA6;">Adapter</mark> 

<mark style="background: #FFB8EBA6;">Intent:</mark> Convert the interface of a class into another interface that clients expect. Adapter lets classes work together that couldn't otherwise because of  
incompatible interfaces.  

Provide an Adapter class which wraps the class that will ultimately perform the requested logic. The Adapter class provides a different interface to that provided by the wrapped class.

![](https://i.imgur.com/y0IqfTB.png)

![](https://i.imgur.com/cuEQNRu.png)

### <mark style="background: #FFB8EBA6;">Adapter Example:</mark>

![](https://i.imgur.com/3bBTjhy.png)

This class implements the interface that the client is expecting and an instance of this class converts the invocation onto the wrapped object.

### <mark style="background: #FFB8EBA6;">Decorator:</mark> 

<mark style="background: #FFB8EBA6;">Intent:</mark> add additional responsibilities dynamically to an object  

Used when you want to add functionality to an object, but not by extending that object's type  

Note, with the <mark style="background: #FFB8EBA6;">Adapter</mark> pattern, the intent was not add additional responsibility (decorations) as it is here but just to provide a different interface

![](https://i.imgur.com/zQySi4b.png)

### <mark style="background: #FFB8EBA6;">Decorator Example:</mark>

![](https://i.imgur.com/SZfJN5k.png)

### <mark style="background: #FFB8EBA6;">Proxy:</mark>

<mark style="background: #FFB8EBA6;">Intent:</mark> Provide a Placeholder for an object to control  
references to it.  

<mark style="background: #FFB8EBA6;">Used to:</mark>
- lazy-instantiate an object  
- hide call to a remote service  
- control access to an object

![](https://i.imgur.com/9hDf9X2.png)
![](https://i.imgur.com/4Ff1Ped.png)

### <mark style="background: #FFB8EBA6;">Proxy Example:</mark>

![](https://i.imgur.com/VVccG2l.png)

### <mark style="background: #FFB8EBA6;">Bridge:</mark>

<mark style="background: #FFB8EBA6;">Intent:</mark> Decouple abstraction from implementation so that the two can vary independently  

Define both the abstract interface and the underlying implementation – can swap out different implementations

![](https://i.imgur.com/OioX033.png)

### <mark style="background: #FFB8EBA6;">Bridge Example:</mark>

![](https://i.imgur.com/syxr1Gv.png)
![](https://i.imgur.com/QTWm7Wg.png)

### <mark style="background: #FFB8EBA6;">Bridge Example – using Inheritance</mark>

![](https://i.imgur.com/oQa6DUI.png)

### <mark style="background: #FFB8EBA6;">Bridge Example – using Aggregation</mark>

![](https://i.imgur.com/jvMa5mw.png)

### <mark style="background: #FFB8EBA6;">REST:</mark>

<mark style="background: #FFB8EBA6;">Architectural Style or Design Pattern?</mark>

W3C - A software system designed to support interoperable machine-to-machine interaction over a network  

<mark style="background: #FFB8EBA6;">Two implementations:</mark>  
- <mark style="background: #FFB8EBA6;">SOAP:</mark> Defines the runtime message that contains the service request and response – the <mark style="background: #FFB8EBA6;">envelope</mark>. SOAP is independent of any particular transport and implementation technology. 
- <mark style="background: #FFB8EBA6;">REST:</mark> Representational State Transfer. REST is an architectural style which is based on web-standards and the HTTP protocol.  REST was first described by Roy Fielding in 2000. Seen as an alternative to SOAP.

### <mark style="background: #FFB8EBA6;">REST:</mark>

In a REST based architecture <mark style="background: #FFB8EBA6;">everything is a resource</mark>. A  
resource is accessed via a common interface based on the HTTP standard methods.  

In an REST architecture you typically have a REST server which provides access to the resources and a REST client which accesses and modify the REST resources. Every resource should support the HTTP common operations. <mark style="background: #FFB8EBA6;">Resources are identified by global ID's</mark>.  

REST allows that <mark style="background: #FFB8EBA6;">resources have different representations</mark>, e.g. text, xml, json etc. The rest client can ask for specific representation via the HTTP protocol (Content Negotiation).

### <mark style="background: #FFB8EBA6;">HTTP Methods:</mark>

The ``HTTP`` standards methods which are typically used in ``REST`` are ``PUT``, ``GET``, ``POST``, ``DELETE``.  
- <mark style="background: #FFB8EBA6;">GET</mark> defines a reading access of the resource without side-effects. The resource is never changed via a GET request, e.g. the request has no side effects.  
- <mark style="background: #FFB8EBA6;">PUT</mark> updates an existing resource or creates a new resource.  
- <mark style="background: #FFB8EBA6;">DELETE</mark> removes the resources.  
- <mark style="background: #FFB8EBA6;">POST</mark> creates a new resource.

### <mark style="background: #FFB8EBA6;">Resources:</mark>

Data and functionality are considered resources and are accessed using <mark style="background: #FFB8EBA6;">Uniform Resource Identifiers (URIs)</mark>  

The resources are acted upon by using a set of simple, well-defined operations (the HTTP methods)  

E.g. GET http://localhost:8080/RestExample/rest/hello  
E.g. POST http://localhost:8080/RestExample/rest/hello

### <mark style="background: #FFB8EBA6;">JAX-RS:</mark>

<mark style="background: #FFB8EBA6;">JAX-RS</mark> - The Java API for <mark style="background: #FFB8EBA6;">RESTful</mark> Web Services  

<mark style="background: #FFB8EBA6;">JAX-RS</mark> is a Java programming language API designed to make it easy to develop applications that use the REST architecture.  

<mark style="background: #FFB8EBA6;">Jersey</mark> (http://jersey.java.net/) is a reference implementation of the JAX-RS specification (JSR 311).

### <mark style="background: #FFB8EBA6;">Implementing a REST Web Service:</mark>

All incoming requests from clients are received by a servlet.  

The servlet analyses the request and <mark style="background: #FFB8EBA6;">selects the correct class and method to execute</mark> based on the request.  

How does it know what class/method to execute?

### <mark style="background: #FFB8EBA6;">Java Annotations:</mark>

Within our server side code, we use annotations to specify what code should be executed for specific client requests.

### <mark style="background: #FFB8EBA6;">JAX-RS Hello World Example - No Annotation:</mark> 

```Java
public class HelloWorld {  
	public String sayPlainTextHello() {  
		return "Hello World";  
	}  
	public String sayXMLHello() {  
		return "<?xml version=\"1.0\"?>" + "<hello> Hello World" + "</hello>";  
	}  
	
	public String sayHtmlHello() {  
		return "<html> " + "<title>" + "Hello World" + "</title>"  + "<body>" + "Hello World" + "</body>" + "</html> ";  
	}  
}
```

### <mark style="background: #FFB8EBA6;">JAX-RS Hello World Example - Annotated</mark>

```Java
@Path("/helloworld")  
public class HelloWorld {  
	// HTTP GET with TEXT_PLAIN request...  
	@GET  
	@Produces(MediaType.TEXT_PLAIN)  
	public String sayPlainTextHello() {  
		return "Hello World";  
	}  
	// HTTP GET with TEXT_XML request...  
	@GET  
	@Produces(MediaType.TEXT_XML)  
	public String sayXMLHello() {  
		return "<?xml version=\"1.0\"?>" + "<hello> Hello World" + "</hello>";  
	}  
	// HTTP GET with TEXT_HTML request...  
	@GET  
	@Produces(MediaType.TEXT_HTML)  
	public String sayHtmlHello() {  
		return "<html> " + "<title>" + "Hello World" + "</title>" + "<body>" + "Hello World" + "</body>" + "</html> ";  
	}  
}
```

### <mark style="background: #FFB8EBA6;">Configuration File - web.xml:</mark>

```XML
<display-name>RestExample</display-name>  

<servlet>  
	<servlet-name>Jersey REST Service</servlet-name>  
	<servlet-class>...REST handling servlet class...</servlet-class>  
	<init-param>  
		<param-name>...packages...</param-name>  
		<param-value>com.restexample</param-value>  
	</init-param>  
	<load-on-startup>1</load-on-startup>  
</servlet>  
<servlet-mapping>  
	<servlet-name>Jersey REST Service</servlet-name>  
	<url-pattern>/rest/</url-pattern>  
</servlet-mapping>
```

### <mark style="background: #FFB8EBA6;">REST Requests:</mark>

![](https://i.imgur.com/0bXVrr8.png)

### <mark style="background: #FFB8EBA6;">REST Request – Java Client:</mark> 
```Java
public void sendPostHelloWorldExample() throws ClientProtocolException, IOException {  
	CloseableHttpClient client = HttpClients.createDefault();  
	HttpPost httpPost = new HttpPost("http://localhost:8080/RestExample/rest/hello");  
	List<NameValuePair> params = new ArrayList<NameValuePair>();  
	params.add( new BasicNameValuePair("greeting", "Here is my message...") );  
	httpPost.setEntity(new UrlEncodedFormEntity(params));  
	CloseableHttpResponse response = client.execute(httpPost);  
	//Do something with response...  
	client.close();  
}
```

### <mark style="background: #FFB8EBA6;">REST Request – Java (server side):</mark>

```Java
@POST  
@Produces(MediaType.TEXT_HTML)  
@Consumes(MediaType.APPLICATION_FORM_URLENCODED)  
public void postHelloWorld(  
@FormParam(“greeting") String greeting,  
@Context HttpServletResponse servletResponse  
) throws IOException {  
...  
//Do something with greeting...  
...  
}
```

### <mark style="background: #FFB8EBA6;">More Annotations:</mark>

![](https://i.imgur.com/1zZK7ij.png)

### <mark style="background: #FFB8EBA6;">Passing Parameters – in true REST style:</mark>

<mark style="background: #FFB8EBA6;">True REST style:</mark>
```HTTP
http://localhost:8080/RestExample/rest/hello/tom
```

Although you can see this type of usage
```HTTP
http://localhost:8080/RestExample/rest/hello?name=tom
```

```Java
@Path("/hello")  
public class HelloWorld {  
	....  
	@Path("{name}")  
	@GET  
	@Produces(MediaType.TEXT_PLAIN)  
	public String sayPlainTextHello(@PathParam(“name") String name) {  
	return "Hello " + name;  
}
```

### <mark style="background: #FFB8EBA6;">Benefits of REST:</mark>
- Familiar Simple Architecture  
- Modularity  
- OO Design  
- Abstraction