### <mark style="background: #BABD00;">TFA - Why should we care?</mark>

<mark style="background: #BABD00;">The Twelve-Factor App provides a methodology of established best practices that:</mark>  
- provides invaluable guidance that should inform and influence every decision when designing the architecture of a modern IT Environment and Infrastructure.  
- facilitates a highly scalable, highly available, performant, secure, resilient, robust, reliable, recoverable, responsive, flexible, transparent, interoperable, modular and composable IT Environment.

### <mark style="background: #BABD00;">TFA - What is it?</mark>

In the Cloud Era, software is delivered as a service software-as-a-service (SaaS).  

<mark style="background: #BABD00;">The Twelve-Factor App is a methodology (developed at Heroku) for building SaaS such that:</mark>  
- Use <mark style="background: #BABD00;">declarative</mark> formats for setup automation.  
- Have a <mark style="background: #BABD00;">clean contract</mark> with the underlying operating system (Portability).  
- Are suitable for <mark style="background: #BABD00;">deployment</mark> on modern <mark style="background: #BABD00;">cloud platforms</mark>.  
- <mark style="background: #BABD00;">Minimise divergence</mark> between development and production.  
- Designed for Scalability.

Imperative Language: evaluated left to right and top to bottom, specifies the how. e.g. C.

Object Oriented: encapsulation e.g. Java

Functional: Global values do not exist. There are no side effects, useful for concurrent programs. e.g. Go, Haskell.

Declarative: You tell the language what you want, not how to do it. e.g. SQL, Prolog
### <mark style="background: #BABD00;">Background:</mark>

TFA is a distillation of best practices and experiences of many contributors involved in the development, deployment and scaling of 100’s of apps.  

<mark style="background: #BABD00;">TFA seeks to integrate:</mark>  
- Ideal practices for App development.  
- The dynamic of collaboration between developers.  
- Avoid the cost of software deterioration/erosion.

TFA can be applied to any app written in any language.  

<mark style="background: #BABD00;">TFA can use any combination of services:</mark>
- Database.  
- Queue.  
- Memory Cache.

### <mark style="background: #BABD00;">Twelve Factors:</mark>

1. <mark style="background: #BABD00;">Codebase:</mark> One codebase tracked in revision control, many deploys.  
2. <mark style="background: #BABD00;">Dependencies:</mark> Explicitly declare and isolate dependencies.  
3. <mark style="background: #BABD00;">Config:</mark> Store config in the environment.  
4. <mark style="background: #BABD00;">Backing Services:</mark> Treat backing services as attached resources.  
5. <mark style="background: #BABD00;">Build, release, run:</mark> Strictly separate build and run stages.  
6. <mark style="background: #BABD00;">Processes:</mark> Execute the app as one or more stateless processes
7. <mark style="background: #BABD00;">Port Binding:</mark> Export services via port binding.  
8. <mark style="background: #BABD00;">Concurrency:</mark> Scale out via the process model.  
9. <mark style="background: #BABD00;">Disposability:</mark> Maximize robustness with fast start-up and graceful shutdown.  
10. <mark style="background: #BABD00;">Dev/prod parity:</mark> Keep development, staging, and production as similar as possible.  
11. <mark style="background: #BABD00;">Logs:</mark> Treat logs as event streams.  
12. <mark style="background: #BABD00;">Admin processes:</mark> Run admin/management tasks as one-off processes.

### <mark style="background: #BABD00;">Codebase:</mark>

<mark style="background: #BABD00;">One codebase tracked in revision control, many deploys</mark>  
- Put all your code in a source control system, such as Git, Mercurial or Subversion.  
- There is always a one-to-one correlation between the codebase and the app.  
- If there are multiple codebases, it’s not an app – it’s a distributed system.  
- Each component in a distributed system is an app, and each can individually comply with twelve-factor.

All shared code should be imported in as libraries.

![](https://i.imgur.com/1jeumRk.png)

<mark style="background: #BABD00;">Dependency Manager:</mark>
- Dependency management is a technique for declaring, resolving and using dependencies required by the project in an automated fashion.  
- Question: Is a dependency manager the same as a package manager?
- No. A package manager operates at the system level and most often deals with binaries. Its role is to install libraries, tools, and other applications. It affects the entire system and not just one project.
- A dependency manager operates at source code level. Its role is to setup the right dependencies for a particular application. It is used by developers, not users or system admins. Thus, a dependency manager is project specific.

Developers use dependency managers, SysAdmins use package managers.

### <mark style="background: #BABD00;">Dependencies:</mark>

<mark style="background: #BABD00;">Explicitly declare and isolate dependencies</mark>  

Many programming languages offer a packaging system for distributing support libraries.  
- Python has pip.  
- Perl has CPAN.  
- Ruby has Rubygems.  
- NodeJS has npm.  
- Rust has cargo, etc.  
- Libraries installed through a packaging system can be installed system-wide (known as “site packages”).  

Libraries also can be scoped into the directory containing the app (known as “vendoring” or “bundling”).

All the environments your code runs in need to have some  
dependencies, like a database, or an image processing library, or a command-line tool.  
- Never let your application assume those things will be in place on a given machine.  
- Ensure they are present by baking those dependencies into your software system.  
- This philosophy extends to your devs or DevSecOps team managing entire machine configurations using management tools like Chef and Puppet.

A twelve-factor app never relies on implicit existence of system-wide packages or libraries.  

It declares all dependencies, completely and exactly, via a dependency declaration manifest.  

Furthermore, it uses a dependency isolation tool during execution to ensure that no implicit dependencies “leak in” from the surrounding system.  

The full and explicit dependency specification is applied uniformly to both production and development.

### <mark style="background: #BABD00;">Config:</mark>

<mark style="background: #BABD00;">Store config in the environment.</mark>  

Configuration is anything that may vary between different environments and deploys. Code is all the stuff that doesn’t. 

<mark style="background: #BABD00;">Examples include:</mark>  
- Resource handles to the database, Memcached, and any other backing services.  
- Credentials to external services such as Amazon S3 or Twitter.  
- Per-deploy values such as the canonical hostname for the deploy.

<mark style="background: #BABD00;">Apps sometimes store config as constants in the code:</mark>
- This is a violation of twelve-factor, which requires strict  separation of config from code. Config varies substantially across deploys, code does not.  
- A litmus test for whether an app has all config correctly factored out of the code is whether the codebase could be made open source at any moment, without compromising any credentials.  
- Note that this definition of “config” does not include internal application config (does not vary between deploys).

The twelve-factor app stores config in environment variables.  

Environment variables are easy to change between deploys without changing any code.  

Unlike config files, there is little chance of them being checked into the code repo accidentally.  

All configuration data should be stored in a separate place from the code, and read in by the code at runtime.  

So, when you deploy code to an environment, you copy the correct configuration files into the codebase at that time.

### <mark style="background: #BABD00;">Backing Services:</mark>

<mark style="background: #BABD00;">Treat backing services as attached resources.</mark>  

A backing service is any service the app consumes over the network as part of its normal operation. Examples include:  
- datastores (such as MySQL or CouchDB).  
- messaging/queueing systems (such as RabbitMQ or Beanstalkd).  
- SMTP services for outbound email (such as Postfix).  caching systems (such as Memcached). 

The code for a twelve-factor app makes no distinction between local and third party services. your code shouldn’t know the difference.  

To the app, both are attached resources, accessed via a URL or other locator/credentials stored in the config.  

A deploy of the twelve-factor app should be able to swap out a local MySQL database with one managed by a third party (such as Amazon RDS) without any changes to the app’s code.  

Likewise, a local SMTP server could be swapped with a third-party SMTP service (such as Postmark) without code changes. In both cases, only the resource handle in the config needs to change.

![](https://i.imgur.com/cT33qN9.png)

### <mark style="background: #BABD00;">Build, Release, Run:</mark>

<mark style="background: #BABD00;">Strictly separate build and run stages.</mark> 

The process of turning the code into a bundle of scripts, assets and binaries that run the code is the <mark style="background: #BABD00;">build</mark>.  

The <mark style="background: #BABD00;">release</mark> sends that code to a server in a fresh package together with the nicely-separate config files for that environment.  

Then the code is <mark style="background: #BABD00;">run</mark> so the application is available on those servers.  

The twelve-factor app uses strict separation between the build, release, and run stages.

![](https://i.imgur.com/dyXe35y.png)

The idea here is that the build stage does a lot of heavy lifting, and developers manage it.  

The run stage should be simple and bullet-proof, kept to as few moving parts as possible, since problems that prevent an app from running can cause it to break in the middle of the night when no developers are on hand.  

The build stage can be more complex, since errors are always in the foreground for a developer who is driving the deploy.

### <mark style="background: #BABD00;">Processes:</mark>

<mark style="background: #BABD00;">Execute the app as one or more stateless processes.</mark>  

It’s likely you will have your application running on many servers, because that makes it more fault tolerant, and because you can support more traffic.  

As a rule, you want each of those instances of running code to be stateless.  

In other words, the state of your system is completely defined by your databases and shared storage, and not by each individual running application instance.  

Twelve-factor processes are stateless and share-nothing. Any data that needs to persist must be stored in a stateful backing service, typically a database.

Some web systems rely on “sticky sessions”.  That is, caching user session data in memory of the app’s process and expecting future requests from the same visitor to  
be routed to the same process.  

Sticky sessions are a violation of twelve-factor and should never be used or relied upon.  

Session state data is a good candidate for a datastore that offers time-expiration, such as Memcached or Redis.

Example: signup workflow, where a user has to enter 3 screens of information to create their profile.  

Wrong approach would be to store each intermediate state in the running code, and direct the user back to the same server until the signup process is complete.  

The right approach is to store intermediate data in a database or persistent key-value store.  

So, if the web server goes down in the middle of the user’s signup, another web server can handle the traffic, and the system is none-the-wiser.

<mark style="background: #BABD00;">Generic benefits of Stateless Apps:</mark>  
- More robust.  
- Easier to manage.  
- Less error prone.  
- Scalable (horizontally).