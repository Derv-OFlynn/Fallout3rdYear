# <mark style="background: #BABD00;">Difference between Stateless and Stateful Protocol</mark>

[Link](https://www.geeksforgeeks.org/difference-between-stateless-and-stateful-protocol/)

In networking, how interactions between clients and servers are managed greatly affects system performance. There are two main types of protocols for this purpose: ****stateless**** and ****stateful**** protocols. Stateless protocols do not maintain state information, so a server does not need to retain information from prior requests. This simplifies server design and optimizes resource utilization. In contrast, stateful protocols maintain session information, allowing for more consistent interaction between clients and servers. Understanding the characteristics and differences of these protocols is crucial for properly designing network systems.

### <mark style="background: #BABD00;">What is the Stateless Protocol?</mark>

Stateless Protocols are the type of network protocols in which the Client sends a request to the server and the server responds back according to the current state. It does not require the server to retain session information or status about each communicating partner for multiple requests. 

HTTP (Hypertext Transfer Protocol), UDP (User Datagram Protocol), and DNS (Domain Name System) are examples of ****Stateless Protocols****. 

<mark style="background: #BABD00;">Salient Features of Stateless Protocols</mark>
- Stateless Protocol simplifies the design of the Server.
- The stateless protocol requires fewer resources because the system does not need to keep track of the multiple link communications and the session details.
- In Stateless Protocol each information packet travels on its own without reference to any other packet.
- Each communication in Stateless Protocol is discrete and unrelated to those that precedes or follow.

### <mark style="background: #BABD00;">What is Stateful Protocol?</mark>

In Stateful Protocol If client send a request to the server then it expects some kind of response, if it does not get any response then it resend the request. FTP (File Transfer Protocol), TCP, and Telnet are the example of Stateful Protocol. 

<mark style="background: #BABD00;">Salient Features of Stateful Protocol:</mark>
- Stateful Protocols provide better performance to the client by keeping track of the connection information.
- Stateful Application require Backing storage.
- Stateful request are always dependent on the server-side state.
- TCP session follow stateful protocol because both systems maintain information about the session itself during its life.

### <mark style="background: #BABD00;">Comparisons Between Stateless and Stateful Protocol</mark>

![](https://i.imgur.com/85ibE2V.png)
![](https://i.imgur.com/LRKLAa0.png)

### <mark style="background: #BABD00;">Conclusion</mark>

Basically, there are two types of protocols: Stateless and Stateful Each type has its benefits and pitfalls that qualify it for use in some contexts and not others. Since these protocols do not retain session specific details, the simplicity in design of servers and the management of resources is well adopted especially in application that do not necessarily require session information of clients. On the other hand, stateful protocols possess better interactivity by maintaining session information that is advantageous for those applications that require session continuity and reliability. By elucidating these differences, one is better placed to determine the right protocol for budgeting purposes and in meeting the profound demands of the business’s specific network.

### <mark style="background: #BABD00;">Difference Between Stateless and Stateful Protocol – FAQs</mark>

<mark style="background: #BABD00;">What is the key benefit of using stateless protocols?</mark>
The main advantage concerning the employment of stateless protocols can be recognized in its relative simplicity and the fairly low demands put on the resources necessary. Since the session information is not required to be stored on the server, it also means that the design is eased and the server load is less.

<mark style="background: #BABD00;">How do stateful protocols enhance client-server communication?</mark>
Stateful protocols improve the engagement between devices because it holds information regarding the connection between the engaging requests which in turn makes the engagement to be much more continuous and reliable as compared to stateless. For cases where it is necessary to monitor particular active sessions, this is quite helpful.

<mark style="background: #BABD00;">Can you give an example of when to use a stateless protocol?</mark>
Connectionless protocols are appropriate for HTTP for web browsing where every request from the client does not depend on the other as the connection will not be persistent. As a result, it should be okay for mainly, low-risk/low-value, operational type activities.

<mark style="background: #BABD00;">Can you give an example of when to use a stateless protocol?</mark>
Reliable protocols are ideal in any system where the context of the session must be constantly kept and used such in the case of FTP or Telnet where the two entities must talk to each other in a one-to-one fashion.

# <mark style="background: #BABD00;">Why use serverless computing? | Pros and cons of serverless</mark>

[Link](https://www.cloudflare.com/en-gb/learning/serverless/why-use-serverless/)

### <mark style="background: #BABD00;">Why use serverless computing?</mark>

Serverless computing offers a number of advantages over traditional cloud-based or server-centric infrastructure. For many developers, serverless architectures offer greater scalability, more flexibility, and quicker time to release, all at a reduced cost. With serverless architectures, developers do not need to worry about purchasing, provisioning, and managing backend servers. However, serverless computing is not a magic bullet for all web application developers.

### <mark style="background: #BABD00;">How does serverless computing work?</mark>

Serverless computing is an architecture in which a vendor provides backend services as they are needed. To learn more about serverless computing, see [What is serverless computing?](https://www.cloudflare.com/learning/serverless/what-is-serverless/)

### <mark style="background: #BABD00;">What are the advantages of serverless computing?</mark>

<mark style="background: #BABD00;">No server management is necessary:</mark>
Although 'serverless' computing does actually take place on servers, developers never have to deal with the servers. They are managed by the vendor. This can reduce the investment necessary in DevOps, which lowers expenses, and it also frees up developers to create and expand their applications without being constrained by server capacity.

<mark style="background: #BABD00;">Developers are only charged for the server space they use, reducing cost:</mark>
As in a 'pay-as-you-go' phone plan, developers are only charged for what they use. Code only runs when backend functions are needed by the serverless application, and the code automatically scales up as needed. Provisioning is dynamic, precise, and real-time. Some services are so exact that they break their charges down into 100-millisecond increments. In contrast, in a traditional 'server-full' architecture, developers have to project in advance how much server capacity they will need and then purchase that capacity, whether they end up using it or not.

<mark style="background: #BABD00;">Serverless architectures are inherently scalable:</mark>
Imagine if the post office could somehow magically add and decommission delivery trucks at will, increasing the size of its fleet as the amount of mail spikes (say, just before Mother's Day) and decreasing its fleet for times when fewer deliveries are necessary. That's essentially what serverless applications are able to do.

Applications built with a serverless infrastructure will scale automatically as the user base grows or usage increases. If a function needs to be run in multiple instances, the vendor's servers will start up, run, and end them as they are needed, often using containers. (The function will start up more quickly if it has been run recently – see 'Performance may be affected' below.) As a result, a serverless application will be able to handle an unusually high number of requests just as well as it can process a single request from a single user. A traditionally structured application with a fixed amount of server space can be overwhelmed by a sudden increase in usage.

<mark style="background: #BABD00;">Quick deployments and updates are possible:</mark>
Using a serverless infrastructure, there is no need to upload code to servers or do any backend configuration in order to release a working version of an application. Developers can very quickly upload bits of code and release a new product. They can upload code all at once or one function at a time, since the application is not a single monolithic stack but rather a collection of functions provisioned by the vendor.

This also makes it possible to quickly update, patch, fix, or add new features to an application. It is not necessary to make changes to the whole application; instead, developers can update the application one function at a time.

<mark style="background: #BABD00;">Code can run closer to the end user, decreasing latency:</mark>
Because the application is not hosted on an [origin server](https://www.cloudflare.com/learning/cdn/glossary/origin-server/), its code can be run from anywhere. It is therefore possible, depending on the vendor used, to run application functions on servers that are close to the end user. This reduces latency because requests from the user no longer have to travel all the way to an origin server. [Cloudflare Workers](https://www.cloudflare.com/products/cloudflare-workers/) enables this kind of serverless latency reduction.

### <mark style="background: #BABD00;">What are the disadvantages of serverless computing?</mark>

<mark style="background: #BABD00;">Testing and debugging become more challenging:</mark>
It is difficult to replicate the serverless environment in order to see how code will actually perform once deployed. Debugging is more complicated because developers do not have visibility into backend processes, and because the application is broken up into separate, smaller functions. The [Cloudflare Workers Playground](https://cloudflareworkers.com/) is a sandbox that helps reduce friction in testing and debugging

<mark style="background: #BABD00;">Serverless computing introduces new security concerns:</mark>
When vendors run the entire backend, it may not be possible to fully vet their security, which can especially be a problem for applications that handle personal or sensitive data.

Because companies are not assigned their own discrete physical servers, serverless providers will often be running code from several of their customers on a single server at any given time. This issue of sharing machinery with other parties is known as 'multitenancy' – think of several companies trying to lease and work in a single office at the same time. Multitenancy can affect application performance and, if the multi-tenant servers are not configured properly, could result in data exposure. Multitenancy has little to no impact for networks that sandbox functions correctly and have powerful enough infrastructure. For instance, Cloudflare runs a 15-Tbps network with enough excess capacity to mitigate service degradation, and all [serverless functions](https://blog.cloudflare.com/introducing-cloudflare-workers/) hosted by Cloudflare run in their own sandbox (via the [Chrome V8 engine](https://blog.cloudflare.com/introducing-cloudflare-workers/)).

<mark style="background: #BABD00;">Serverless architectures are not built for long-running processes:</mark>
This limits the kinds of applications that can cost-effectively run in a serverless architecture. Because serverless providers charge for the amount of time code is running, it may cost more to run an application with long-running processes in a serverless infrastructure compared to a traditional one.

<mark style="background: #BABD00;">Performance may be affected:</mark>
Because it's not constantly running, serverless code may need to 'boot up' when it is used. This start-up time may degrade performance. However, if a piece of code is used regularly, the serverless provider will keep it ready to be activated – a request for this ready-to-go code is called a 'warm start.' A request for code that hasn't been used in a while is called a 'cold start.'

Cloudflare Workers largely avoids the cold-starting issue by using the Chrome V8 engine, which in most cases is able to start up and run JavaScript code in under 5 milliseconds. If the code is already running, the response time is under a millisecond. [Learn more about the performance of different serverless platforms](https://www.cloudflare.com/learning/serverless/serverless-performance/).

<mark style="background: #BABD00;">Vendor lock-in is a risk:</mark>
Allowing a vendor to provide all backend services for an application inevitably increases reliance on that vendor. Setting up a serverless architecture with one vendor can make it difficult to switch vendors if necessary, especially since each vendor offers slightly different features and workflows. ([Cloudflare Workers](https://www.cloudflare.com/products/cloudflare-workers/) are easier to migrate because they are written in JavaScript and written against the widely used service workers API.)

### <mark style="background: #BABD00;">Who should use a serverless architecture?</mark>

Developers who want to decrease their go-to-market time and build lightweight, flexible applications that can be expanded or updated quickly may benefit greatly from serverless computing.

Serverless architectures will reduce costs for applications that see inconsistent usage, with peak periods alternating with times of little to no traffic. For such applications, purchasing a server or a block of servers that are constantly running and always available, even when unused, may be a waste of resources. A serverless setup will respond instantly when needed and will not incur costs when at rest.

Also, developers who want to push some or all of their application functions close to end users for reduced latency will require at least a partially serverless architecture, since doing so necessitates moving some processes out of the origin server.

### <mark style="background: #BABD00;">When should developers avoid using a serverless architecture?</mark>

There are cases when it makes more sense, both from a cost perspective and from a system architecture perspective, to use dedicated servers that are either self-managed or offered as a service. For instance, large applications with a fairly constant, predictable workload may require a traditional setup, and in such cases the traditional setup is probably less expensive.

Additionally, it may be prohibitively difficult to migrate legacy applications to a new infrastructure with an entirely different architecture.

### <mark style="background: #BABD00;">How does Cloudflare help developers build serverless architectures?</mark>

[Cloudflare Workers](https://www.cloudflare.com/products/cloudflare-workers/) is a product that enables developers to write JavaScript functions and deploy them at the edge of the Cloudflare network. This makes it possible to run application code in a serverless architecture as close to the end user as possible, minimizing latency.

# <mark style="background: #BABD00;">What is a Message Broker?</mark>

[Link](https://www.ibm.com/topics/message-brokers)

A message broker is software that enables applications, systems and services to communicate with each other and exchange information.

The message broker does this by translating messages between formal messaging protocols. This allows interdependent services to “talk” with one another directly, even if they were written in different languages or implemented on different platforms.

Message brokers are software modules within messaging middleware or message-oriented middleware (MOM) solutions. This type of middleware provides developers with a standardized means of handling the flow of data between an application’s components so that they can focus on its core logic. It can serve as a distributed communications layer that allows applications spanning multiple platforms to communicate internally.

Message brokers can validate, store, route, and deliver messages to the appropriate destinations. They serve as intermediaries between other applications, allowing senders to issue messages without knowing where the receivers are, whether or not they are active, or how many of them there are. This facilitates decoupling of processes and services within systems.

In order to provide reliable message storage and guaranteed delivery, message brokers often rely on a substructure or component called a [message queue](https://www.ibm.com/topics/message-queues) that stores and orders the messages until the consuming applications can process them. In a message queue, messages are stored in the exact order in which they were transmitted and remain in the queue until receipt is confirmed.

Asynchronous messaging refers to the type of inter-application communication that message brokers make possible. It prevents the loss of valuable data and enables systems to continue functioning even in the face of the intermittent connectivity or latency issues common on public [networks](https://www.ibm.com/topics/networking). Asynchronous messaging guarantees that messages will be delivered once (and once only) in the correct order relative to other messages.

Message brokers may comprise queue managers to handle the interactions between multiple message queues, as well as services providing data routing, message translation, persistence, and client state management functionalities.

# <mark style="background: #BABD00;">What is a Message Queue?</mark>

[Link](https://aws.amazon.com/message-queue/)

A message queue is a form of asynchronous service-to-service communication used in serverless and microservices architectures. Messages are stored on the queue until they are processed and deleted. Each message is processed only once, by a single consumer. Message queues can be used to decouple heavyweight processing, to buffer or batch work, and to smooth spiky workloads.

Below are several resources to help you better understand message queues in the broad sense. To learn about message queues on AWS, visit our [Amazon Simple Queue Service (SQS)](https://aws.amazon.com/sqs) website.

### <mark style="background: #BABD00;">Message Queue Basics</mark>

In modern cloud architecture, applications are decoupled into smaller, independent building blocks that are easier to develop, deploy and maintain. Message queues provide communication and coordination for these distributed applications. Message queues can significantly simplify coding of decoupled applications, while improving performance, reliability and scalability.

Message queues allow different parts of a system to communicate and process operations asynchronously. A message queue provides a lightweight buffer which temporarily stores messages, and endpoints that allow software components to connect to the queue in order to send and receive messages. The messages are usually small, and can be things like requests, replies, error messages, or just plain information. To send a message, a component called a producer adds a message to the queue. The message is stored on the queue until another component called a consumer retrieves the message and does something with it.

![](https://i.imgur.com/GYzhkKO.png)

Many producers and consumers can use the queue, but each message is processed only once, by a single consumer. For this reason, this messaging pattern is often called one-to-one, or point-to-point, communications. When a message needs to be processed by more than one consumer, message queues can be combined with Pub/Sub messaging in a fanout design pattern. See "[What is Pub/Sub messaging?](https://aws.amazon.com/what-is/pub-sub-messaging/)" for details, and visit our [Amazon Simple Notification Service (SNS)](https://aws.amazon.com/migration-acceleration-program/) website for an overview of Pub/Sub messaging on AWS.

# <mark style="background: #BABD00;">What is a key-value database?</mark>

[Link](https://aws.amazon.com/nosql/key-value/)

A [key-value database](https://aws.amazon.com/dynamodb/) is a type of non-relational database, also known as [NoSQL database](https://aws.amazon.com/nosql/), that uses a simple key-value method to store data. It stores data as a collection of key-value pairs in which a key serves as a unique identifier. Both keys and values can be anything, ranging from simple objects to complex compound objects. Key-value databases (or key-value stores) are highly partitionable and allow horizontal scaling at a level that other types of databases cannot achieve.

### <mark style="background: #BABD00;">What are the advantages of key-value databases</mark>

Traditional [relational databases](https://aws.amazon.com/relational-database/) ([SQL databases](https://aws.amazon.com/rds/)) store data in the form of tables containing rows and columns. They enforce a rigid structure on data and are not optimal for every use case. On the other hand, key-value databases are NoSQL databases. They allow flexible database schemas and improved performance at scale for certain use cases. The advantages of key-value stores include:

<mark style="background: #BABD00;">Scalability</mark>
As every user query requires data interaction, databases can often become a bottleneck in application performance. Several strategies to solve the issue, such as replication and [sharding](https://aws.amazon.com/what-is/database-sharding/), add complexity to the application code. Many key-value databases provide built-in support for advanced scaling features. They scale horizontally and automatically distribute data across servers to reduce bottlenecks at a single server.

<mark style="background: #BABD00;">Ease of use:</mark>
Key-value databases follow the object-oriented paradigm that allows developers to map real-world objects directly to software objects. Several programming languages, such as Java, also follow the same paradigm. Instead of mapping their code objects to multiple underlying tables, engineers can create key-value pairs that match their code objects. This makes key-value stores more intuitive for developers to use.

<mark style="background: #BABD00;">Performance:</mark>
Key-value databases process constant read-write operations with low-overhead server calls. Improved latency and reduced response time give better performance at scale. They are based on simple, single-table structures rather than multiple interrelated tables. Unlike relational databases, key-value databases don't have to perform resource-intensive table joins, which makes them much faster.

### <mark style="background: #BABD00;">What are the use cases of key-value databases?</mark>

You can use key-value database systems as the primary database for your application or to handle niche requirements. We give some example key-value database use cases below.

<mark style="background: #BABD00;">Session management:</mark>
A session-oriented application, such as a web application, starts a session when a user logs in to an application and is active until the user logs out or the session times out. During this period, the application stores all user session attributes either in the main memory or in a database. User session data may include profile information, messages, personalized data and themes, recommendations, targeted promotions, and discounts.

Each user session has a unique identifier. Session data is never queried by anything other than a primary key, so a fast key-value store is a better fit for session data. In general, key-value databases may provide smaller per-page overhead than relational databases.

<mark style="background: #BABD00;">Shopping cart:</mark>
An e-commerce website may receive billions of orders per second during the holiday shopping season. A key-value database can handle the scaling of large amounts of data and extremely high volumes of state changes, while also servicing millions of simultaneous users through distributed processing and storage. Key-value stores also have built-in redundancy, which can handle the loss of storage nodes.

<mark style="background: #BABD00;">Metadata storage engine:</mark>
Your key-value store can act as an underlying storage layer for higher levels of data access. For example, you can scale throughput and concurrency for media and entertainment workloads such as real-time video streaming and interactive content. You can also build out your game platform with player data, session history, and leader-boards for millions of concurrent users.

<mark style="background: #BABD00;">Caching:</mark>
You can use a key-value database for storing data temporarily for faster retrieval. For example, social media applications can store frequently accessed data like news feed content. In-memory data caching systems also use key-value stores to accelerate application responses.

### <mark style="background: #BABD00;">How do key-value databases work</mark>

Key-value databases work by organizing all data as a set of key-value pairs. You can think of the key as a question and the value as the answer to the question. In the example below, the primary key is a composite of two keys, Product ID and Type. The Product ID is the partition key which describes the partition in which the item will be stored. The Type is the sort key, which determines the order in which items will be stored in disk. The combination of the Partition Key and the Sort Key forms a unique primary key, which maps to a single value in the database.

In this example, the data object book has attributes like title, author, and publishing date. Every book data object has a key called ``BookID``. You can directly link the ``BookID`` and associated book object in the key-value store. In addition, you can retrieve data by looking up the ``BookID`` in the table. Also, each item has its own schema, making key-value stores highly flexible for storing data of varying structures.

![](https://i.imgur.com/xY4i81N.png)

### <mark style="background: #BABD00;">What are the features of key-value databases</mark>

Depending on the solution you choose, your key-value store can provide several additional features as listed below.

<mark style="background: #BABD00;">Support for complex data types:</mark>
Key-value stores provide support for defined data types like integers and text. However, many of them can also support more complex objects like arrays, nested dictionaries, images, videos, and semi-structured data. By giving the database more information about your data, there is room for more storage and query performance optimization.

<mark style="background: #BABD00;">No need for table joins:</mark>
Key-value databases don't need to perform any resource-intensive table joins. Their flexibility accommodates all the needed information in a single table. This is one of the reasons key-value stores perform so well.

<mark style="background: #BABD00;">Sorted keys:</mark>
A key-value store can sort keys so that data is stored systematically and for implementing partitioning. For example, keys may be sorted:
- Alphabetically or numerically
- Chronologically
- By data size

Consider a key-value store that uses the customer's email address as the unique key. Email addresses can be sorted alphabetically, so all data for A-J email lists are stored on server 1, K-S on server 2, and so on.

<mark style="background: #BABD00;">Secondary key support:</mark>
Some key-value stores allow you to define two or more different keys or secondary indexes to access the same data. For example, you can store customer data by key email address and key phone number.

<mark style="background: #BABD00;">Replication:</mark>
Many key-value stores offer built-in replication support by automatically copying data across multiple storage nodes. This helps with auto-recovery from disasters; you still have your data in case of server failure.

<mark style="background: #BABD00;">Partitioning:</mark>
Partitioning is how you distribute data across nodes. Many key-value databases provide default partitioning options. Some also give you the option to define input parameters for your partitions. For example, you could partition numerical keys into groups of 1000. Advanced key-value databases also provide automatic support for distributing your key-value database across multiple geographical locations. This improves application availability and reliability because you can respond to queries close to the user's location.

<mark style="background: #BABD00;">ACID support:</mark>
Atomicity, Consistency, Isolation, and Durability ([ACID](https://docs.aws.amazon.com/athena/latest/ug/acid-transactions.html)) are database properties that ensure data accuracy and reliability in all circumstances. For instance, if you are making multiple changes to your data in a sequence, atomicity requires that all changes go through in order. If one change fails, everything fails.

Advanced key-value databases provide native, server-side support for ACID. This simplifies the developer experience of making coordinated, all-or-nothing changes to multiple items both within and across tables. With transaction support, developers can extend the scale, performance, and enterprise benefits to a broader set of mission-critical workloads.

### <mark style="background: #BABD00;">What are the limitations of key-value databases</mark>

Key-value databases do require some trade-offs, as with any kind of technology choice.

<mark style="background: #BABD00;">Absence of complex queries:</mark>
As key-value databases don't support complex queries, developers must work around this in the code. Data operations are mainly through simple query language terms like get, put, and delete. There are limitations to how much you can filter and sort data before accessing it.

<mark style="background: #BABD00;">Schema mismanagement:</mark>
Key-value store design does not enforce a schema on developers. Anyone can modify the schema in the database program. Development teams have to plan the data model systematically to avoid long-term problems. The lack of a tight schema also means that the application is responsible for the proper interpretation of the data it consumes, often referred to as 'schema on read'.

# <mark style="background: #BABD00;">What is a GitOps workflow?</mark>

Managing IT infrastructure can be challenging, but teams that use well-known software development practices, including version control, code review, and CI/CD pipelines, find the process more convenient. By using config files, the same infrastructure environment is deployed each time. Many teams know that this workflow increases efficiency, collaboration, and stability, but they may wonder what it means to adopt GitOps.

### <mark style="background: #BABD00;">Three components of GitOps workflows</mark>

[Link](https://about.gitlab.com/topics/gitops/gitops-workflow/)

As a software development framework, GitOps has three main parts to its workflow, including infrastructure as code, merge requests, and CI/CD pipelines.

### <mark style="background: #BABD00;">1. Infrastructure as code (IaC)</mark>

[IaC Link](https://about.gitlab.com/topics/gitops/gitops-workflow/#-infrastructure-as-code-iac)

The first step in a GitOps workflow is defining all [infrastructure as code](https://about.gitlab.com/topics/gitops/infrastructure-as-code/). IaC automates the IT infrastructure provisioning by using configuration files. IaC is a DevOps practice that supports teams to version infrastructure to improve consistency across machines to reduce deployment friction. Infrastructure code undergoes a similar process as application code with touchpoints in continuous integration, version control, testing, and continuous deployment. Automation leads to more [efficient](https://about.gitlab.com/blog/2020/04/17/why-gitops-should-be-workflow-of-choice/) development, increased consistency, and [faster](https://about.gitlab.com/blog/2021/02/24/production-grade-infra-devsecops-with-five-minute-production/) time to market.

Managing [infrastructure](https://about.gitlab.com/blog/2020/11/09/lessons-in-iteration-from-new-infrastructure-team/) has traditionally been a manual process involving large teams maintaining physical servers. Each machine often has its own configuration, leading to snowflake environments. With infrastructure as code, teams have increased visibility, consistency, stability, and scalability.

### <mark style="background: #BABD00;">2. Merge requests (MRs)</mark>

[MRs Link](https://about.gitlab.com/topics/gitops/gitops-workflow/#-merge-requests-mrs)

Declarative tools, such as Kubernetes, enable config files to be [version controlled](https://about.gitlab.com/blog/2020/11/12/migrating-your-version-control-to-git/) by Git, an open source version control system that tracks code changes. Using a Git repository as the single source of truth for infrastructure definitions, GitOps benefits from a robust audit trail. The second aspect of GitOps workflows involve merge requests, which serve as the [change function](https://about.gitlab.com/blog/2020/10/13/merge-request-reviewers/) for infrastructure updates.

Teams collaborate in merge requests through [code reviews](https://about.gitlab.com/blog/2021/01/25/mr-reviews-with-vs-code/), comments, and suggestions. A merge commits to the [main](https://about.gitlab.com/blog/2021/03/10/new-git-default-branch-name/) branch and acts as an audit log. Built-in rollback features enable teams to revert to a desired state and explore innovative ways to approach difficult challenges. Merge requests facilitate experimentation and provide a safe way for team members to receive fast [feedback](https://about.gitlab.com/blog/2021/03/18/iteration-and-code-review/) from their peers and subject matter experts.

### <mark style="background: #BABD00;">3. Continuous integration and continuous deployment (CI/CD)</mark>
[CI/CDL ink](https://about.gitlab.com/topics/gitops/gitops-workflow/#-continuous-integration-and-continuous-deployment-cicd)

GitOps automates infrastructure management using a Git workflow with [effective](https://about.gitlab.com/blog/2020/07/29/effective-ci-cd-pipelines/) continuous integration and continuous deployment. After code is merged to the main branch, the CI/CD pipeline initiates the [change](https://about.gitlab.com/blog/2021/02/22/pipeline-editor-overview/) in the environment. Manual changes and human error can cause configuration drift and snowflake environments, but GitOps automation and continuous deployment overwrites them so the environment always [deploys](https://about.gitlab.com/blog/2021/02/05/ci-deployment-and-environments/) a consistent desired state.

# <mark style="background: #BABD00;">The 3 Core principles of ZeroTrust</mark>

[Link](https://www.twingate.com/blog/the-3-core-principles-of-zero-trust)

Zero Trust has been a topic of cybersecurity for over two decades, gaining prominence in 2010 when John Kindervag championed the concept.

Today, as cyber threats evolve and organizational perimeters expand with remote work and cloud integration, [interest in Zero Trust is higher than ever](https://trends.google.com/trends/explore?date=all&geo=US&q=zero%20trust&hl=en). This makes it a perfect opportunity to revisit the robust foundations of Zero Trust Network Access (ZTNA).

![](https://i.imgur.com/F0TR3W4.png)

In this guide, we’ll delve into the three fundamental principles of Zero Trust: Least Privilege Access, Always Verify, and Risk Mitigation. Each principle is critical for building a resilient and dynamic security environment where threats are not only recognized but also effectively contained. Join us as we explore how these principles can fortify your organization against the ever-changing landscape of cyber threats.

- `Least Privilege Access`
- `Always Verify`
- `Risk Mitigation`

### <mark style="background: #BABD00;">What is Zero Trust Security?</mark>

  
Zero Trust Security is a cybersecurity strategy that challenges the conventional perimeter-based security models, which have increasingly shown their limitations in the face of modern cyber threats and evolving work environments. Traditional security models operate under the assumption that everything inside an organization’s network can be trusted. However, this assumption has become flawed due to the rising sophistication of cyber attacks and the fact that insiders can often be threats themselves.

In the face of evolving cyber threats and changing work environments, traditional perimeter-based security models are proving inadequate. Enter ZTNA, a paradigm shift in cybersecurity that embodies the principle of “never trust, always verify.”  
  

### <mark style="background: #BABD00;">Least Privilege Access</mark>

In a Zero Trust architecture, access controls are dynamically and strictly enforced to ensure robust security. Let's explore the five distinct levels of access that are particularly relevant within a Zero Trust framework:

1. **No Access:** This is the default setting for any user or device. Access is not granted until explicit authentication and authorization are achieved, reinforcing the security from the ground up.

2. **Public Access:** This level allows users to access publicly available information or resources without the need for authentication. It's designed for maximum accessibility while still maintaining overarching security protocols.

3. **General Access:** Within an organization, general access typically includes access to basic organizational tools such as email. This level is meant for day-to-day operational activities by regular staff members.

4. **Administrative Access:** Reserved for IT and security personnel, this is the highest level of access. It includes comprehensive privileges over all systems and applications, enabling these authorized users to modify, delete, or configure high-level settings as required for system management and security.

5. **Privileged Access:** At this level, users and systems are granted only the minimum levels of access—or permissions—necessary to perform specific functions. This careful allocation of privileges is crucial for minimizing the attack surface and limiting the potential damage from security breaches or insider threats. This foundational principle of granting the least privilege necessary to complete your tasks is the core of the Zero Trust model.

Each of these access levels plays a vital role in the enforcement of Zero Trust principles, ensuring that security is maintained through meticulous control over who can access what within your network.

### <mark style="background: #BABD00;">Always Verify</mark>

In the Zero Trust model, the concept of implicit trust is completely abandoned in favour of constant verification. This approach operates under the assumption that a security breach is already present within your system.

Consequently, Zero Trust protocols strictly limit access privileges to only those necessary for specific tasks and continuously scan for signs of malicious activity. Implementing Zero Trust can significantly mitigate your risks associated with data breaches, ransomware, and insider threats.

Although this model imposes stricter access controls, it streamlines your organization’s cybersecurity framework, facilitating a more manageable and secure system environment. This enhanced security architecture is crucial for safeguarding your data and assets.  
  

### <mark style="background: #BABD00;">Risk Mitigation</mark>

To effectively minimize the blast radius within a network, the Zero Trust framework advocates for an 'assume breach' approach. By segmenting the network into smaller, secure zones, this strategy enhances control over access and sharply curtails the possibility for threats to move laterally within the system.

This segmentation not only restricts access to sensitive areas but also contains potential breaches to isolated segments, dramatically reducing the overall risk and impact of security threats. This proactive and compartmentalized approach is essential for robustly defending against and swiftly responding to cybersecurity threats.

As our VP of engineering would explain:

"Imagine your computer network is like a city, and each service or application is a building within that city. The 'blast radius' refers to how much damage a potential security breach could cause—just like how far the impact of an explosion might reach in a real city.

In cybersecurity, if a hacker gains unauthorized access to part of the network, the blast radius is the extent to which they can move from that entry point to other parts of the network. With a larger blast radius, hackers can access more data and cause more damage. By limiting the blast radius, you're essentially building walls or barriers between different parts of your "city" (or network). If one barrier is compromised, only those within that area would be impacted. The damage doesn't spread to other buildings behind other barriers."

TL;DR: the blast radius in cybersecurity is about the damage a breach can cause in a network. Strategies like network segmentation contain breaches and minimise this damage.