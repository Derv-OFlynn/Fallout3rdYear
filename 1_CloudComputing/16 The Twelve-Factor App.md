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

### <mark style="background: #BABD00;">Software Erosion:</mark>

![](https://i.imgur.com/e3fmAkq.png)

The “bathtub curve” for <mark style="background: #BABD00;">hardware</mark> failure.

![](https://i.imgur.com/TQ1BA7U.png)

Software doesn’t wear out.

### <mark style="background: #BABD00;">The Software Product:</mark>

<mark style="background: #BABD00;">What are some of the attributes of good software?</mark>
- <mark style="background: #BABD00;">Reliability:</mark> Software must be trustworthy.
- <mark style="background: #BABD00;">Usability:</mark> Software must be usable by the users for which it was designed.  
- <mark style="background: #BABD00;">Efficiency:</mark> Software should not make wasteful use of system resources.  
- <mark style="background: #BABD00;">Maintainability:</mark> Software must evolve to meet changing needs.  
- <mark style="background: #BABD00;">Portability:</mark> We should be able to move software from machine to machine as we require.
- <mark style="background: #BABD00;">Others:</mark> Functional suitability, Compatibility, Security (ISO/IEC 25010:2011

<mark style="background: #BABD00;">The cost of change:</mark>
![](https://i.imgur.com/JCoSRyn.png)

### <mark style="background: #BABD00;">Three Ways Software wears out:</mark>

<mark style="background: #BABD00;">1. Bugs</mark>

"Computer" was originally a job, mostly done by women. Seen as a secondary, secretarial role. 

First computer was made in 1942 by the British. "The Colossus".

The origin of the word "Bug" is from when a moth flew into a vacuum tube and had to be removed - "debugging".

Bugfixes are the second most common source of bugs.

<mark style="background: #BABD00;">2. New Feature requests</mark>

Users request more features as time goes on. 

<mark style="background: #BABD00;">3. Environment in which the software runs changes</mark>

SQLite is the most used DB in the world. Switching their build process to TCL

Dr. Richard Hipp created SQLite.

### <mark style="background: #BABD00;">The Twelve Factors:</mark>

1. <mark style="background: #BABD00;">Codebase:</mark> One codebase tracked in revision control, many deploys.  
2. <mark style="background: #BABD00;">Dependencies:</mark> Explicitly declare and isolate dependencies.  
3. <mark style="background: #BABD00;">Config:</mark> Store config in the environment.  
4. <mark style="background: #BABD00;">Backing Services:</mark> Treat backing services as attached resources.  
5. <mark style="background: #BABD00;">Build, release, run:</mark> Strictly separate build and run stages.  
6. <mark style="background: #BABD00;">Processes:</mark> Execute the app as one or more stateless processes.
7. <mark style="background: #BABD00;">Port Binding:</mark> Export services via port binding.  
8. <mark style="background: #BABD00;">Concurrency:</mark> Scale out via the process model.  
9. <mark style="background: #BABD00;">Disposability:</mark> Maximise robustness with fast start-up and graceful shutdown.  
10. <mark style="background: #BABD00;">Dev/prod parity:</mark> Keep development, staging, and production as similar as possible.  
11. <mark style="background: #BABD00;">Logs:</mark> Treat logs as event streams.  
12. <mark style="background: #BABD00;">Admin processes:</mark> Run admin/management tasks as one-off processes.

The role of any project manager is to manage time, resources, money and people in order to deliver a project on time, within budget and meeting the requirements

### <mark style="background: #BABD00;">Load Balancing:</mark>

All inbound traffic to a web role passes through a stateless load balancer, which distributes client requests among the role instances.  

Individual role instances do not have public IP addresses, and are not directly addressable from the Internet. (This is why you can’t ‘Ping’ the IP addresses).  

Web roles are stateless, so that any client request can be routed to any role instance.  

A Status-check event is raised every 15 seconds. This can be used to indicate if the role is ready to receive traffic, or is busy and should be taken out of the load balancer rotation.

![](https://i.imgur.com/1k4ZMNx.png)

### <mark style="background: #BABD00;">Elasticity:</mark>

<mark style="background: #BABD00;">Elasticity – What is it?</mark>  

The degree to which a system is able to adapt to workload changes by provisioning and deprovisioning resources in an automated manner, such that at each point in time the available resources match the current demand as closely as possible.  

<mark style="background: #BABD00;">Elasticity is automated scalability.</mark>  
Scalability provides the ability to increase (or decrease) the amount of resources in scaling up (more powerful instances) or out (additional instances), which is usually done through manual intervention.  

Elasticity does the same but in an automated manner, independent from human interaction.

### <mark style="background: #BABD00;">7. Port Binding:</mark>

<mark style="background: #BABD00;">Export services via port binding.</mark>  

In essence, your application must interface to the outside world using a simple URL.  

Web apps are sometimes executed inside a webserver container.  

For example, PHP apps might run as a module inside Apache HTTPD, or Java apps might run inside Tomcat.  

The twelve-factor app is completely self-contained and does not rely on runtime injection of a webserver into the execution environment to create a web-facing service.

The web app exports HTTP (and any other server software) as a service by binding to a port, and listening to requests coming in on that port.  

This means that one app can become the backing service for another app, by providing the URL to the backing app as a resource handle in the config for the consuming app.  
<mark style="background: #BABD00;">Software Composable Intrastructure ???</mark>

![](https://i.imgur.com/5MmGUgs.png)

### <mark style="background: #BABD00;">8. Concurrency</mark>

<mark style="background: #BABD00;">Scale out via the process model.</mark>  

In the twelve-factor app, processes are a first class citizen.  
Processes in the twelve-factor app take strong cues from the unix process model for running service daemons.  

The unix philosophy states that an app should do one thing, only one thing and do it well.

A daemon is a program that runs in the background.

The developer can architect their app to handle diverse workloads by assigning each type of work to a process type.  

For example, HTTP requests may be handled by a web process, and long-running background tasks handled by a worker process.

![](https://i.imgur.com/6EImxu6.png)

![](https://i.imgur.com/viAPH3q.png)

The idea is that lots of little processes are handling specific needs.  

So you might have dozens of handlers at the ready to process web requests, and another dozen to handle API calls for your enterprise users. And still another half-dozen processing background welcome-emails going to new users.  

By keeping all these small parts working independently, and running them as separate processes, your application will scale better. In particular, you’ll be able to do more stuff concurrently.  

By scaling horizontally (or vertically).

### <mark style="background: #BABD00;">9. Disposability</mark>

<mark style="background: #BABD00;">Maximize robustness with fast start-up and graceful shutdown.</mark>  

The twelve-factor app’s processes are disposable, meaning they can be started or stopped at a moment’s notice.  

This facilitates fast elastic scaling, rapid deployment of code or config changes, and robustness of production deploys.  

Consequently, processes should strive to minimize startup time.  

Processes shut down gracefully.  

For a web process, a graceful shutdown is achieved by ceasing to listen on the service port (thereby refusing any new requests), allowing any current requests to finish, and then exiting.

Further, your application should be robust against sudden death (crashing) in the case of a failure in the underlying hardware.  

Meaning, if it does crash, it should always be able to start back up cleanly.  

You should never do any mandatory “cleanup” tasks when the app shuts down, because that might cause problems if they failed to run in a crash scenario.  

A recommended approach is use of a robust queueing backend, such as Beanstalkd, that returns jobs to the queue when clients disconnect or time out.

You should never require any manual intervention or manual clean-up tasks unless you have a good and compelling reason to do so.

### <mark style="background: #BABD00;">10. Dev/Prod Parity</mark>

<mark style="background: #BABD00;">Keep development, staging, and production as similar as possible.</mark>
![](https://i.imgur.com/fSfO4mc.png)

<mark style="background: #BABD00;">Historically, there have been substantial gaps between development and production:</mark>  
- <mark style="background: #BABD00;">The time gap:</mark> A developer may work on code that takes days, weeks, or even months to go into production.  
- <mark style="background: #BABD00;">The personnel gap:</mark> developers write code, ops engineers deploy it.  
- <mark style="background: #BABD00;">The tools gap:</mark> Developers may be using a stack like Nginx, SQLite, and OS X, while the production deploy uses Apache, MySQL, and Linux.

The twelve-factor app is designed for continuous deployment by keeping the gap between development and production small.  
- <mark style="background: #BABD00;">Make the time gap small:</mark> a developer may write code and have it deployed hours or even just minutes later.  
- <mark style="background: #BABD00;">Make the personnel gap small:</mark> developers who wrote code are closely involved in deploying it and watching its behaviour in production.  
- <mark style="background: #BABD00;">Make the tools gap small:</mark> keep development and production as similar as possible.

![](https://i.imgur.com/9YM79wZ.png)

### <mark style="background: #BABD00;">Continuous Delivery Vs Continuous Deployment:</mark>

Subtle but important different between Continuous Delivery and Continuous Deployment.  

Continuous deployment is the next step of continuous delivery

![](https://i.imgur.com/Jtd1zB8.png)

### <mark style="background: #BABD00;">Logs:</mark>

<mark style="background: #BABD00;">Treat logs as event streams.</mark>  

Logs provide visibility into the behaviour of a running app.  

Logs are the stream of aggregated, time-ordered events collected from the output streams of all running processes and backing services.  

Logs have no fixed beginning or end, but flow continuously as long as the app is operating.  

Logs in their raw form are typically a text format with one event per line (though backtraces from exceptions may span multiple lines).

<mark style="background: #BABD00;">A twelve-factor app never concerns itself with routing or storage of its output stream.</mark>  
- It should not attempt to write to or manage logfiles. Instead, each running process writes its event stream, unbuffered, to stdout.  
- During local development, the developer will view this stream in the foreground of their terminal to observe the app’s behaviour.

<mark style="background: #BABD00;">In staging or production deploys, each process’ stream will be captured by the execution environment:</mark>  
- collated together with all other streams from the app.  
- routed to one or more final destinations for viewing and long-term archival.  

These archival destinations are not visible to or configurable by the app, and instead are completely managed by the execution environment.

### <mark style="background: #BABD00;">12. Admin Processes</mark>

<mark style="background: #BABD00;">Run admin/management tasks as one-off processes.</mark>  

<mark style="background: #BABD00;">Developers will often wish to do one-off administrative or maintenance tasks for the app, such as:</mark>  
- Running database migrations.  
- Running a console (also known as a REPL shell) to run arbitrary code or inspect the app’s models against the live database (e.g.: python, perl, irb for ruby, etc).  
- Running one-time scripts committed into the app’s repo (e.g. php scripts/fix_bad_records.php).

One-off admin processes should be run in an identical environment as the regular long-running processes of the app.  

Admin code must ship with application code to avoid synchronization issues.  

Twelve-factor strongly favours languages which provide a REPL shell out of the box, and which make it easy to run one-off scripts.  

In a local deploy, developers invoke one-off admin processes by a direct shell command.  

In a production deploy, developers can use ssh or other remote command execution mechanism to run a one-off process.

[Source](https://12factor.net)