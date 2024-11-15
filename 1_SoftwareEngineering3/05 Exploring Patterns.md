### <mark style="background: #FFB8EBA6;">Client - Server(Static):</mark>

![](https://i.imgur.com/7HArCaY.png)

<mark style="background: #FFB8EBA6;">HTTP</mark> – Hypertext Transfer Protocol, rules used to transfer data across the internet  

<mark style="background: #FFB8EBA6;">Client</mark> – Any software – PC, Laptop, Smartphone, Tablet  

<mark style="background: #FFB8EBA6;">Web Server</mark> – Computer system that provides the service of responding to HTTP requests, can “serve” web site pages, images etc. using an HTTP response

### <mark style="background: #FFB8EBA6;">Client – Server (Dynamic):</mark>

![](https://i.imgur.com/ltmvYBb.png)

Web Server – as well as static content serving, the server provides an execution environment for application code to return dynamic content.

<mark style="background: #FFB8EBA6;">Servlet Container:</mark>  
- A servlet is a java class that can be directly invoked by a http client – e.g. a web browser.  
- The java code executing in the servlet, for example, may access a relational database and retrieve information that can either directly returned to the http client or processed further into html and then returned to the client.

### <mark style="background: #FFB8EBA6;">Example Servlet:</mark>

```Java
public class UserController extends HttpServlet {  
	public UserController() {  
		super();  
	} 
	//HTTP GET from client handled here
	protected void doGet( HttpServletRequest request, HttpServletResponse response)  
	throws ServletException, IOException  
	{  
		// code...  
	}  
	//HTTP POST from client handled here
	protected void doPost( HttpServletRequest request, HttpServletResponse response)  
	throws ServletException, IOException  
	{  
		//code...  
	}  
}
```

### <mark style="background: #FFB8EBA6;">We can use the DAO's and other classes from a Servlet:</mark>

![](https://i.imgur.com/R737R6t.png)

What do we do with the data retrieved / result of request?

### <mark style="background: #FFB8EBA6;">The Model View Controller (MVC) Pattern</mark>

![](https://i.imgur.com/df8I2Im.png)

A pattern for designing an architecture that separates the application logic from the user interface logic

This allows development, testing and maintenance to be achieved independently

### <mark style="background: #FFB8EBA6;">MVC Applied to Web Applications:</mark>

![](https://i.imgur.com/oLcmvVP.png)
![](https://i.imgur.com/Wl5X6R2.png)

### <mark style="background: #FFB8EBA6;">Using JSP for the View:</mark>

<mark style="background: #FFB8EBA6;">JSP:</mark> Java Server Pages

Writing a JSP source file

<mark style="background: #FFB8EBA6;">static_example.html:</mark>
```html
<html>  
	<body bgcolor="yellow">  
		<center>  
			<h2>Hello World</h2>  
		</center>  
	</body>  
</html>
```

<mark style="background: #FFB8EBA6;">static_example.jsp</mark>
```JSP
<html>  
	<body bgcolor="yellow">  
		<center>  
			<h2>Hello world</h2>  
		</center>  
	</body>  
</html>
```

<mark style="background: #FFB8EBA6;">dynamic_example.jsp</mark>
```JSP
<html>  
	<body bgcolor="yellow">  
		<center>  
			<h2>Hello World</h2>  
			//View accesses an object to display some information
			<p> <%= new java.util.Date() %> </p>  
		</center>  
	</body>  
</html>
```

### <mark style="background: #FFB8EBA6;">Requesting a JSP file:</mark>

Browser requests a ``.jsp`` file instead of a ``.html`` file from the server  

If you just renamed a .html to a ``.jsp`` file, the first time you loaded/requested the file it would take longer to load than the HMTL version...  

What’s happening?  
The first time the .jsp page is requested by the browser, the server reads the file and converts it to a java class and compiles it. Once compiled, it is executed completely as a java program.  

This generated java class is a <mark style="background: #FFB8EBA6;">servlet</mark>

![](https://i.imgur.com/HqL0bno.png)

### <mark style="background: #FFB8EBA6;">Service Layer:</mark>

A set of classes, each of which provide a set of application operations.  

E.g. ``UserService`` class provides a login operation. A typical implementation is a Service class that has a corresponding DAO attribute.  

E.g. ``UserService`` has an attribute ``userDao`` which is of type ``UserDao``.

![](https://i.imgur.com/o3RHbLt.png)

![](https://i.imgur.com/CXZzvRZ.png)

### <mark style="background: #FFB8EBA6;">Singleton Pattern:</mark>

<mark style="background: #FFB8EBA6;">Intent:</mark> Ensure that a class has only one instance, and provide a global point of access to it  

Only one object will ever exist in memory. It is not possible to create a second object of the same class in memory

```Java
public class MyServer {  
	//Must be static, as static methods can only access static attributes. Only one myServer object created, even if some other member method created another object of MyServer.
	private static MyServer myServer = null; 
	
	//private constructor ensures only methods of the class can call the constructor.
	private MyServer() {}  
	
	public static synchronized MyServer getInstance() {  
		if (myServer == null){ 
			//Creates object first time. Returns the same myServer object each time the method is called. 
			myServer = new MyServer();  
		}  
		return myServer;  
	}  
	// other attributes, methods etc.  
}
```

```Java
public class MyServerTest { 
	//Line below is not permitted as constructor is private.
	// MyServer myServer = new MyServer() ;  
	MyServer server1 = MyServer.getInstance() ;  
	MyServer server2 = MyServer.getInstance() ;  
	//As clients cannot create objects, getInstance() must be a static method. This static method provides a global point of access. It always returns reference to the same object.
	if (server1 == server2)  
		System.out.println("Same server") ;  
	else  
		System.out.println("Different servers") ;  
	}  
}
```

### <mark style="background: #FFB8EBA6;">Command Pattern:</mark>

<mark style="background: #FFB8EBA6;">Intent:</mark> Encapsulate a request as an object, thereby letting you  parameterise clients with different requests, queue or log requests.  

E.g. Request from client browser to the server to list all users – we can encapsulate the code to handle this request on the server into a  single object.

<mark style="background: #FFB8EBA6;">Recall - Example Servlet</mark>
```Java
public class UserController extends HttpServlet {  
	
	public UserController() {  
		super();  
	}  
	
	protected void doGet( HttpServletRequest request, HttpServletResponse response)  
	throws ServletException, IOException  
	{  
	// code...  
	}  
	
	protected void doPost( HttpServletRequest request, HttpServletResponse response)  
	throws ServletException, IOException  
	{  
	//code...  
	}  
}
```

### <mark style="background: #FFB8EBA6;">Using the Command Pattern with JSP/Servlets Example snippet from a simple Servlet</mark>

<mark style="background: #FFB8EBA6;">Code inside doGet() method:</mark>
```Java
//Action requested from web page.
else if ( request.getParameter("action").equalsIgnoreCase("listUsers") ) {  

	//The user wants a list if all users...  
	//Use the UserService class to get all Users...  
	List<User> users = new ArrayList<User>();  
	users = userService.getAllUsers();  
	//Put the list of users into the session so that JSP(the View) can display them...  
	session.setAttribute("users", users);  
	forwardToJsp = "/listUsers.jsp";  
}
```

### <mark style="background: #FFB8EBA6;">New Servlet Code:</mark>

```Java
if ( request.getParameter("action").equalsIgnoreCase("listUsers") ) 
{  
	//The user wants a list of all users...  
	//Code to handle this is moved to the ListUsersCommand object. Note the use of a Command Interface
	Command command = new ListUsersCommand();  
	forwardToJsp = command.execute(request, response);  
}
```

```Java
public interface Command {  
	
	public String execute(HttpServletRequest request, HttpServletResponse response);  
}  

public class ListUsersCommand implements Command {  

	public String execute(HttpServletRequest request, HttpServletResponse response) {  
		UserService userService = new UserService();  
		String forwardToJsp = "";  
		HttpSession session = request.getSession();  
		//Make the call to the 'Model' by using the UserService class to get all Users...  
		List<User> users = new ArrayList<User>();  
		users = userService.getAllUsers();  
		//Put the list of users into the session so that JSP(the View) can pick them up and display them...  
		session.setAttribute("users", users);  
		forwardToJsp = "/listUsers.jsp";  
		return forwardToJsp;  
	}  
}
```

### <mark style="background: #FFB8EBA6;">The Simple Factory Pattern:</mark>

<mark style="background: #FFB8EBA6;">Intent:</mark> Provide a class for creating an instance of one of several possible classes depending on the data provided to it. Usually all classes that it returns have a common parent interface or class, but each performs a task differently.  

E.g. a <mark style="background: #FFB8EBA6;">CommandFactory</mark> object that can instantiate and return <mark style="background: #FFB8EBA6;">Command</mark> objects to the calling code.  

The objects that it returns are specific Command objects like <mark style="background: #FFB8EBA6;">ListUsersCommand</mark> – however, they are treated as <mark style="background: #FFB8EBA6;">Command</mark> objects because all specific <mark style="background: #FFB8EBA6;">Command</mark> objects (e.g. ``ListUsersCommand``) implement the ``Command Interface``.

```Java
public class CommandFactory {  
	... 
	//Implemented as a singleton – private constructor 
	private CommandFactory() 
	{}  
	...  
	//Note, this method returns the object as a Command, however, the specific Command implementation is what is returned (e.g. ListUsersCommand)
	public synchronized Command createCommand(String commandStr) {  
	Command command = null;  
	//Instantiate the required Command object...  
	if (commandStr.equals("LoginUser")) {  
	command = new LoginUserCommand();  
	}  
	//Depending on what information is passed to the createCommand method, the factory will create the specific command
	if (commandStr.equals("ListUsers")) {  
	command = new ListUsersCommand();  
	}  
	if (commandStr.equals("ViewUserProfile")) {  
	command = new ViewUserProfileCommand();  
	}  
	//Return the instantiated Command object to the calling code...  
	return command;// may be null  
}
```

### <mark style="background: #FFB8EBA6;">Using the CommandFactory from our Servlet:</mark>

```Java
if ( request.getParameter("action").equalsIgnoreCase("listUsers") ) {  
	//The user wants a list if all users...  
	CommandFactory factory = CommandFactory.getInstance();  
	Command command = factory.createCommand("ListUsers");  
	forwardToJsp = command.execute(request, response);  
}
```

### <mark style="background: #FFB8EBA6;">Front Controller Pattern:</mark>

<mark style="background: #FFB8EBA6;">Intent:</mark> Provide a centralised point of access for handling client requests in a web application.  

Our <mark style="background: #FFB8EBA6;">servlet</mark> acts as <mark style="background: #FFB8EBA6;">Front Controller</mark> – it accepts all <mark style="background: #FFB8EBA6;">User</mark> related requests from the client (browser), calls the relevant ``command.execute()`` method and forwards the server to the next page.

### <mark style="background: #FFB8EBA6;">UserController Servlet:</mark>

```Java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {  
	processRequest (request, response);  
}  

protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {  
	processRequest(request, response);  
}  
/**  
* Common method to process all client requests (GET and POST)  
*/  
private void processRequest(HttpServletRequest request, HttpServletResponse response) {  
	//Execute the appropriate command...  
}
```

### <mark style="background: #FFB8EBA6;">Sending a request through doGet() / doPost()</mark>

<mark style="background: #FFB8EBA6;">This sends the data using Http POST:</mark>
```JSP
<form action="UserController" method="post">  
	<input type="hidden" name="action" value="listUsers" />  
	<input type="submit" value="List Users" />  
</form>
```

<mark style="background: #FFB8EBA6;">This sends the data using Http GET:</mark>
```JSP
<a href="UserController?action=listUsers">List All Users</a>
```

### <mark style="background: #FFB8EBA6;">Application Example using multiple patterns:</mark>

Web Application example  

Start with a Login User use case  
1. User enters username and password  
2. User clicks Login button  
3. System validates username / password  
4. 4a Normal flow - user presented with options page
4. 4b Alternative flow - if invalid, authentication message displayed with option to return to login page

![](https://i.imgur.com/O1i4zYO.png)

### <mark style="background: #FFB8EBA6;">Login Page - Static html</mark>

![](https://i.imgur.com/u05kcwO.png)

This action (command) drives the request through the back end

### <mark style="background: #FFB8EBA6;">Front Controller:</mark>

![](https://i.imgur.com/7gUvsPk.png)

This method processes any http POST requests.

For completeness, here is the ``forwardToPage`` method implementation.

![](https://i.imgur.com/NhS8rTU.png)

### <mark style="background: #FFB8EBA6;">Command Factory:</mark>

![](https://i.imgur.com/Etp0cWu.png)

Implements the singleton pattern

![](https://i.imgur.com/L4Vl3N8.png)

The ``CommandFactory`` object itself still has no explicit knowledge of the command implementation it is instantiating.  

It uses the reflective method ``theClass.newInstance()`` which invokes the zero argument constructor.

### <mark style="background: #FFB8EBA6;">LoginUserCommand:</mark>

![](https://i.imgur.com/hgLTBIW.png)

Accepts the client request and invokes the business service

### <mark style="background: #FFB8EBA6;">User Service:</mark>

![](https://i.imgur.com/Gny3y6K.png)

In this instance, the service just calls through to the DAO object.

### <mark style="background: #FFB8EBA6;">UserDao:</mark>

![](https://i.imgur.com/gRenAmN.png)

In this example, we are simply using JDBC, however, we could implement code here that utilises an Object Relational Mapping framework.

### <mark style="background: #FFB8EBA6;">Login Successful View – loginSuccess.jsp</mark>

![](https://i.imgur.com/JfkF6AV.png)

The view accesses the data made available by the model

### <mark style="background: #FFB8EBA6;">This gives us a separation of the layers:</mark>

![](https://i.imgur.com/Vk3kBPO.png)

### <mark style="background: #FFB8EBA6;">Eclipse Dynamic Web Project:</mark>

![](https://i.imgur.com/qPLVJYz.png)

Our package structure reflects our layered design

Each package contains the set of classes appropriate to that layer

![](https://i.imgur.com/TvdBWHi.png)