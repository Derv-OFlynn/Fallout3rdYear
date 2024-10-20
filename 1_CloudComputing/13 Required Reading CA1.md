# <mark style="background: #BABD00;">Week 2:</mark>

### <mark style="background: #BABD00;">NIST Definition of Cloud Computing:</mark>

<mark style="background: #BABD00;">NIST:</mark> National Institute of Standards and Technology (USA)

<mark style="background: #BABD00;">Cloud computing</mark> is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.  

This cloud model is composed of five essential characteristics, three service models, and four deployment  models.  

#### <mark style="background: #BABD00;">Essential Characteristics:</mark>  

<mark style="background: #BABD00;">On-demand self-service.</mark> A consumer can unilaterally provision computing capabilities, such as server time and network storage, as needed automatically without requiring human interaction with each service provider.  

<mark style="background: #BABD00;">Broad network access.</mark> Capabilities are available over the network and accessed through standard  mechanisms that promote use by heterogeneous thin or thick client platforms (e.g., mobile phones, tablets, laptops, and workstations).  

<mark style="background: #BABD00;">Resource pooling.</mark> The provider’s computing resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand. There is a sense of location independence in that the customer generally has no control or knowledge over the exact location of the provided resources but may be able to specify location at a higher level of abstraction (e.g., country, state, or datacenter). Examples of resources include storage, processing, memory, and network bandwidth.  

<mark style="background: #BABD00;">Rapid elasticity.</mark> Capabilities can be elastically provisioned and released, in some cases automatically, to scale rapidly outward and inward commensurate with demand. To the consumer, the capabilities available for provisioning often appear to be unlimited and can be appropriated in any quantity at any time.  

<mark style="background: #BABD00;">Measured service.</mark> Cloud systems automatically control and optimize resource use by leveraging a metering capability<sup>1</sup> at some level of abstraction appropriate to the type of service (e.g., storage, processing, bandwidth, and active user accounts). Resource usage can be monitored, controlled, and reported, providing transparency for both the provider and consumer of the utilized service.  

#### <mark style="background: #BABD00;">Service Models:</mark>  

<mark style="background: #BABD00;">Software as a Service (SaaS).</mark> The capability provided to the consumer is to use the provider’s applications running on a cloud infrastructure<sup>2</sup>. The applications are accessible from various client devices through either a thin client interface, such as a web browser (e.g., web-based email), or a program interface. The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems, storage, or even individual application capabilities, with the possible exception of limited user-specific application configuration settings. 

<mark style="background: #BABD00;">Platform as a Service (PaaS).</mark> The capability provided to the consumer is to deploy onto the cloud infrastructure consumer-created or acquired applications created using programming languages, libraries, services, and tools supported by the provider<sup>3</sup>. The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems, or storage, but has control over the deployed applications and possibly configuration settings for the application-hosting environment.  

<mark style="background: #BABD00;">Infrastructure as a Service (IaaS).</mark> The capability provided to the consumer is to provision processing, storage, networks, and other fundamental computing resources where the consumer is able to deploy and run arbitrary software, which can include operating systems and applications. The consumer does not manage or control the underlying cloud infrastructure but has control over operating systems, storage, and deployed applications; and possibly limited control of select networking components (e.g., host firewalls).

#### <mark style="background: #BABD00;">Deployment Models:</mark>  

<mark style="background: #BABD00;">Private cloud.</mark> The cloud infrastructure is provisioned for exclusive use by a single organization comprising multiple consumers (e.g., business units). It may be owned, managed, and operated by the organization, a third party, or some combination of them, and it may exist on or off premises.

<mark style="background: #BABD00;">Community cloud.</mark> The cloud infrastructure is provisioned for exclusive use by a specific community of consumers from organizations that have shared concerns (e.g., mission, security requirements, policy, and compliance considerations). It may be owned, managed, and operated by one or more of the organizations in the community, a third party, or some combination of them, and it may exist on or off premises.  

<mark style="background: #BABD00;">Public cloud.</mark> The cloud infrastructure is provisioned for open use by the general public. It may be owned, managed, and operated by a business, academic, or government organization, or some combination of them. It exists on the premises of the cloud provider.  

<mark style="background: #BABD00;">Hybrid cloud.</mark> The cloud infrastructure is a composition of two or more distinct cloud infrastructures (private, community, or public) that remain unique entities, but are bound together by standardized or proprietary technology that enables data and application portability (e.g., cloud bursting for load balancing between clouds).

<mark style="background: #BABD00;">Footnotes:</mark>
1. 1 Typically this is done on a pay-per-use or charge-per-use basis.  
2. A cloud infrastructure is the collection of hardware and software that enables the five essential characteristics of cloud computing. The cloud infrastructure can be viewed as containing both a physical layer and an abstraction layer. The physical layer consists of the hardware resources that are necessary to support the cloud services being provided, and typically includes server, storage and network components. The abstraction layer consists of the software deployed across the physical layer, which manifests the essential cloud characteristics. Conceptually the abstraction layer sits above the physical layer.
3. This capability does not necessarily preclude the use of compatible programming languages, libraries, services, and tools from other sources.

### <mark style="background: #BABD00;">CONTENT DELIVERY NETWORK:</mark>
#### <mark style="background: #BABD00;">What is a Content Delivery Network (CDN)?</mark>

[Source](https://www.cloudflare.com/en-gb/learning/cdn/what-is-a-cdn/)

A content delivery network (CDN) is a geographically distributed group of servers that caches content close to end users. A CDN allows for the quick transfer of assets needed for loading Internet content, including HTML pages, JavaScript files, stylesheets, images, and videos.

The popularity of CDN services continues to grow, and today the majority of web traffic is served through CDNs, including traffic from major sites like Facebook, Netflix, and Amazon.

A properly configured CDN may also help protect websites against some common malicious attacks, such as [Distributed Denial of Service (DDOS) attacks](https://www.cloudflare.com/learning/ddos/what-is-a-ddos-attack/).

#### <mark style="background: #BABD00;">Is a CDN the same as a web host?</mark>

While a CDN does not host content and can’t replace the need for proper web hosting, it does help [cache](https://www.cloudflare.com/learning/cdn/what-is-caching/) content at the [network edge](https://www.cloudflare.com/learning/serverless/glossary/what-is-edge-computing/), which improves website performance. Many websites struggle to have their [performance](https://www.cloudflare.com/learning/cdn/performance/) needs met by traditional hosting services, which is why they opt for CDNs.

By utilizing caching to reduce hosting bandwidth, [helping to prevent interruptions in service](https://www.cloudflare.com/learning/cdn/cdn-load-balance-reliability/), and [improving security](https://www.cloudflare.com/learning/cdn/cdn-ssl-tls-security/), CDNs are a popular choice to relieve some of the major pain points that come with traditional web hosting.

#### <mark style="background: #BABD00;">What are the benefits of using a CDN?</mark>

Although the benefits of using a CDN vary depending on the size and needs of an Internet property, the primary benefits for most users can be broken down into four different components:

1. <mark style="background: #BABD00;">Improving website load times</mark> - By distributing content closer to website visitors by using a nearby CDN server (among other optimizations), visitors experience faster page loading times. As visitors are more inclined to click away from a slow-loading site, a CDN can reduce bounce rates and increase the amount of time that people spend on the site. In other words, a faster a website means more visitors will stay and stick around longer.

2. <mark style="background: #BABD00;">Reducing bandwidth costs</mark> - Bandwidth consumption costs for website hosting is a primary expense for websites. Through caching and other optimizations, CDNs are able to reduce the amount of data an origin server must provide, thus reducing hosting costs for website owners.

3. <mark style="background: #BABD00;">Increasing content availability and redundancy</mark> - Large amounts of traffic or hardware failures can interrupt normal website function. Thanks to their distributed nature, a CDN can handle more traffic and withstand hardware failure better than many origin servers.

4. <mark style="background: #BABD00;">Improving website security</mark> - A CDN may improve security by providing [DDoS mitigation](https://www.cloudflare.com/learning/ddos/ddos-mitigation/), improvements to security certificates, and other optimizations.

#### <mark style="background: #BABD00;">How does a CDN work?</mark>

At its core, a CDN is a network of servers linked together with the goal of delivering content as quickly, cheaply, reliably, and securely as possible. In order to improve speed and connectivity, a CDN will place servers at the exchange points between different networks.

These [Internet exchange points (IXPs)](https://www.cloudflare.com/learning/cdn/glossary/internet-exchange-point-ixp/) are the primary locations where different Internet providers connect in order to provide each other access to traffic originating on their different networks. By having a connection to these high speed and highly interconnected locations, a CDN provider is able to reduce costs and transit times in high speed data delivery.

![](https://i.imgur.com/p4FOzjp.png)

Beyond placement of servers in IXPs, a CDN makes a number of optimizations on standard client/server data transfers. CDNs place Data Centres at strategic locations across the globe, enhance security, and are designed to survive various types of failures and Internet congestion.

#### <mark style="background: #BABD00;">Latency - How does a CDN improve website load times?</mark>

When it comes to websites loading content, users drop off quickly as a site slows down. CDN services can help to reduce load times in the following ways:
- The globally distributed nature of a CDN means reduce distance between users and website resources. Instead of having to connect to wherever a website’s [origin server](https://www.cloudflare.com/learning/cdn/glossary/origin-server/) may live, a CDN lets users connect to a geographically closer [data centre](https://www.cloudflare.com/learning/cdn/glossary/internet-exchange-point-ixp/). Less travel time means faster service.
- Hardware and software optimizations such as efficient load balancing and solid-state hard drives can help data reach the user faster.
- CDNs can reduce the amount of data that’s transferred by reducing file sizes using tactics such as [minification](https://www.cloudflare.com/learning/performance/why-minify-javascript-code/) and file compression. Smaller file sizes mean quicker load times.
- CDNs can also speed up sites which use [TLS](https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/)/[SSL](https://www.cloudflare.com/learning/ssl/what-is-ssl/) certificates by optimizing connection reuse and enabling TLS false start.

[Explore all the ways a CDN helps websites load faster](https://www.cloudflare.com/learning/cdn/performance/)

#### <mark style="background: #BABD00;">Reliability and redundancy - How does a CDN keep a website always online?</mark>

Uptime is a critical component for anyone with an Internet property. Hardware failures and spikes in traffic, as a result of either malicious attacks or just a boost in popularity, have the potential to bring down a web server and prevent users from accessing a site or service. A well-rounded CDN has several features that will minimize downtime:

- Load balancing distributes network traffic evenly across several servers, making it easier to scale rapid boosts in traffic.
- Intelligent failover provides uninterrupted service even if one or more of the CDN servers go offline due to hardware malfunction; the failover can redistribute the traffic to the other operational servers.
- In the event that an entire data centre is having technical issues, [Anycast](https://www.cloudflare.com/learning/cdn/glossary/anycast-network/) routing transfers the traffic to another available data centre, ensuring that no users lose access to the website.

[Learn more about how a CDN helps keep websites online](https://www.cloudflare.com/learning/cdn/cdn-load-balance-reliability/)

#### <mark style="background: #BABD00;">Data security - How does a CDN protect data?</mark>

Information security is an integral part of a CDN. a CDN can keep a site secured with fresh [TLS/SSL certificates](https://www.cloudflare.com/learning/ssl/what-is-an-ssl-certificate/) which will ensure a high standard of authentication, [encryption](https://www.cloudflare.com/learning/ssl/what-is-encryption/), and integrity. Investigate the security concerns surrounding CDNs, and explore what can be done to securely deliver content. [Learn about CDN SSL/TLS security](https://www.cloudflare.com/learning/cdn/cdn-ssl-tls-security/)

#### <mark style="background: #BABD00;">Bandwidth expense - How does a CDN reduce bandwidth costs?</mark>

Every time an origin server responds to a request, bandwidth is consumed. See how a CDN, like the [Cloudflare CDN](https://www.cloudflare.com/application-services/products/cdn/), cuts down on origin requests and [reduces bandwidth costs](https://www.cloudflare.com/learning/cdn/how-cdns-reduce-bandwidth-cost/).

### <mark style="background: #BABD00;">Serverless Computing:</mark>

#### <mark style="background: #BABD00;">What is serverless computing?</mark>

Serverless computing is a method of providing backend services on an as-used basis. A serverless provider allows users to write and deploy code without the hassle of worrying about the underlying infrastructure. A company that gets backend services from a serverless vendor is charged based on their computation and do not have to reserve and pay for a fixed amount of bandwidth or number of servers, as the service is auto-scaling. Note that despite the name serverless, physical servers are still used but developers do not need to be aware of them.

In the early days of the web, anyone who wanted to build a web application had to own the physical hardware required to run a server, which is a cumbersome and expensive undertaking.

Then came [cloud computing](https://www.cloudflare.com/learning/cloud/what-is-the-cloud/), where fixed numbers of servers or amounts of server space could be rented remotely. Developers and companies who rent these fixed units of server space generally over-purchase to ensure that a spike in traffic or activity will not exceed their monthly limits and break their applications. This means that much of the server space that gets paid for can go to waste. Cloud vendors have introduced auto-scaling models to address the issue, but even with auto-scaling an unwanted spike in activity, such as a [DDoS Attack](https://www.cloudflare.com/learning/ddos/what-is-a-ddos-attack/), could end up being very expensive.

![](https://i.imgur.com/Gtd4R3y.png)

Serverless computing allows developers to purchase backend services on a flexible ‘pay-as-you-go’ basis, meaning that developers only have to pay for the services they use. This is like switching from a cell phone data plan with a monthly fixed limit, to one that only charges for each byte of data that actually gets used.

The term ‘serverless’ is somewhat misleading, as there are still servers providing these backend services, but all of the server space and infrastructure concerns are handled by the vendor. Serverless means that the developers can do their work without having to worry about servers at all.

#### <mark style="background: #BABD00;">What are backend services? What’s the difference between frontend and backend?</mark>

[Source](https://www.cloudflare.com/en-gb/learning/serverless/what-is-serverless/)

Application development is generally split into two realms: the frontend and the backend. The frontend is the part of the application that users see and interact with, such as the visual layout. The backend is the part that the user doesn’t see; this includes the server where the application's files live and the database where user data and business logic is persisted.

![](https://i.imgur.com/yZlc8Zm.png)

For example, let’s imagine a website that sells concert tickets. When a user types a website address into the browser window, the browser sends a request to the backend server, which responds with the website data. The user will then see the frontend of the website, which can include content such as text, images, and form fields for the user to fill out. The user can then interact with one of the form fields on the frontend to search for their favorite musical act. When the user clicks on ‘submit’, this will trigger another request to the backend. The backend code checks its database to see if a performer with this name exists, and if so, when they will be playing next, and how many tickets are available. The backend will then pass that data back to the frontend, and the frontend will display the results in a way that makes sense to the user. Similarly, when the user creates an account and enters financial information to buy the tickets, another back-and-forth communication between the frontend and backend will occur.

#### <mark style="background: #BABD00;">What kind of backend services can serverless computing provide?</mark>

Most serverless providers offer database and storage services to their customers, and many also have [Function-as-a-Service (FaaS)](https://www.cloudflare.com/learning/serverless/glossary/function-as-a-service-faas/) platforms, like [Cloudflare Workers](https://www.cloudflare.com/developer-platform/workers/). FaaS allows developers to execute small pieces of code on the [network edge](https://www.cloudflare.com/learning/serverless/glossary/what-is-edge-computing/). With FaaS, developers can build a modular architecture, making a codebase that is more scalable without having to spend resources on maintaining the underlying backend. [Learn more about FaaS >>](https://www.cloudflare.com/learning/serverless/glossary/function-as-a-service-faas/)

#### <mark style="background: #BABD00;">What are the advantages of serverless computing?</mark>

- <mark style="background: #BABD00;">Lower costs</mark> - Serverless computing is generally very cost-effective, as traditional cloud providers of backend services (server allocation) often result in the user paying for unused space or idle CPU time.
- <mark style="background: #BABD00;">Simplified scalability</mark> - Developers using serverless architecture don’t have to worry about policies to scale up their code. The serverless vendor handles all of the scaling on demand.
- <mark style="background: #BABD00;">Simplified backend code</mark> - With FaaS, developers can create simple functions that independently perform a single purpose, like making an API call.
- <mark style="background: #BABD00;">Quicker turnaround</mark> - Serverless architecture can significantly cut time to market. Instead of needing a complicated deploy process to roll out bug fixes and new features, developers can add and modify code on a piecemeal basis.

Learn more about [the benefits of serverless computing.](https://www.cloudflare.com/learning/serverless/why-use-serverless/)

#### <mark style="background: #BABD00;">How does serverless compare to other cloud backend models?</mark>

A couple of technologies that are often conflated with serverless computing are Backend-as-a-Service and Platform-as-a-Service. Although they share similarities, these models do not necessarily meet the requirements of serverless.

<mark style="background: #BABD00;">Backend-as-a-service (BaaS)</mark> is a service model where a cloud provider offers backend services such as data storage, so that developers can focus on writing front-end code. But while serverless applications are event-driven and run on the edge, BaaS applications may not meet either of these requirements. [Learn more about BaaS >>](https://www.cloudflare.com/learning/serverless/glossary/backend-as-a-service-baas/)

<mark style="background: #BABD00;">Platform-as-a-service (PaaS)</mark> is a model where developers essentially rent all the necessary tools to develop and deploy applications from a cloud provider, including things like operating systems and middleware. However PaaS applications are not as easily scalable as serverless applications. PaaS also don’t necessarily run on the edge and often have a noticeable start-up delay that isn’t present in serverless applications. [Learn more about PaaS >>](https://www.cloudflare.com/learning/serverless/glossary/platform-as-a-service-paas/)

<mark style="background: #BABD00;">Infrastructure-as-a-service (IaaS)</mark> is a catchall term for cloud vendors hosting infrastructure on behalf of their customers. IaaS providers may offer serverless functionality, but the terms are not synonymous. [Learn more about IaaS >>](https://www.cloudflare.com/learning/cloud/what-is-iaas/)

#### <mark style="background: #BABD00;">What is next for serverless?</mark>

Serverless computing continues to evolve as serverless providers come up with solutions to overcome some of its drawbacks. One of these drawbacks is cold starts.

Typically when a particular serverless function has not been called in a while, the provider shuts down the function to save energy and avoid over-provisioning. The next time a user runs an application that calls that function, the serverless provider will have to spin it up fresh and start hosting that function again. This start-up time adds significant latency, which is known as a ‘cold start’.

Once the function is up and running it will be served much more rapidly on subsequent requests (warm starts), but if the function is not requested again for a while, the function will once again go dormant. This means the next user to request that function will experience a cold start. Up until fairly recently, cold starts were considered a necessary trade-off of using serverless functions.

Cloudflare Workers has addressed this problem by spinning up serverless functions in advance, during the [TLS handshake](https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/). Since Workers functions spin up at the edge in a very short amount of time, even shorter than the time required to complete the handshake, the result is an [FaaS platform with zero cold starts](https://blog.cloudflare.com/eliminating-cold-starts-with-cloudflare-workers/). To get started with Cloudflare Workers, see our [Developer documentation](https://developers.cloudflare.com/workers/).

As more and more of the drawbacks of using serverless get addressed and the popularity of edge computing grows, we can expect to see serverless architecture becoming more widespread.

# <mark style="background: #BABD00;">Week 3:</mark>

### <mark style="background: #BABD00;">Network Physical Components:</mark>

<mark style="background: #BABD00;">Network Adapter:</mark> A network adapter is the component of a computer’s internal hardware that is used for communicating over a network with another computer. It enable a computer to connect with another computer, server or any networking device over an LAN connection. A network adapter can be used over a wired or wireless network.  

<mark style="background: #BABD00;">Network Router:</mark> Resides at the Network Layer. Data Transmission Form is a Packet. Uses IP address. Used for connecting two or more networks. A router is a networking device that connects a local network to other local networks. Routers connect two or more logical subnets, which do not necessarily map one-to-one to the physical interfaces of the router.  

<mark style="background: #BABD00;">Network Bridge:</mark> A network bridge is a computer networking device that creates a single  aggregate network from multiple communication networks or network segments. This function is called network bridging. Bridging is distinct from routing. Routing allows multiple networks to communicate independently and yet remain separate, whereas bridging connects two separate networks as if they were a single network. In the OSI model, bridging is performed in the data link layer (layer 2).  

<mark style="background: #BABD00;">Network Switch:</mark> Resides at the Data Link Layer. Data transmission form is a Frame. Uses MAC address. Used for connecting two or more nodes in the same network (L2) or different network (L3). A network switch is a computer networking device that is used to connect many devices together on a computer network. A switch is considered more advanced than a hub because a switch will send on a msg to device that needs or request it. Allow connections to multiple devices, manage ports, manage VLAN security settings.  

<mark style="background: #BABD00;">Network Hub (or Repeater):</mark> Also called repeaters — are even less advanced that switches; while a hub broadcasts the same data to all its ports, a network switch forwards data only to those devices that the data is intended for. Network hubs do not manage any traffic coming through them; they only broadcast — or repeat — packets from an incoming port to all other ports.

# <mark style="background: #BABD00;">How HTTPS works:</mark>

[Source for Comic](https://howdns.works/)

Computers and other devices communicate using IP addresses to identify each other on the internet.

Humans can't remember IP addresses, so they use words. e.g. google.com

The domain name system (DNS) brings the two together and gets you to your destination.

The resolver server is usually your <mark style="background: #BABD00;">ISP</mark> (Internet service provider). All resolvers must know where to locate the root server.

The root server knows where to locate the .COM TLD server. TLD stands for Top-Level Domain.

There are 13 root servers that exist today. Root servers sit at the top of the DNS hierarchy.

![](https://i.imgur.com/PNkgGG2.png)

The root servers are scattered around the globe and operated by 12 independent organisations. They are named [letter].root-servers.net where [letter] ranges from A to M.

```
a.root-servers.net 
b.root-servers.net 
.... 
m.root-servers.net
```

This doesn't mean that we have only 13 physical servers to support the whole internet! Each organisation provides multiple physical servers distributed around the globe.

The coordination of most top-level domains (TLDs) belong to the Internet Corporation for Assigned Names and Numbers (ICANN). It is the largest TLD on the internet.

The .COM TLD was one of the first created in 1985.

<mark style="background: #BABD00;">When a user types something into the browser:</mark>
1. The browser checks its cache
2. If the url is not there, it asks the OS
3. The OS checks its cache
4. If the OS does not have the url cached, it asks the resolver to search for the url
5. The resolver checks its cache
6. If the resolver does not have the url cached, it asks the root server
7. The root server does not cache urls but it does know where to find the TLD server and passes this to the resolver
8. The resolver asks the TLD server for the ip address of the server
9. The TLD server will return either the ip address or the nameservers of the url
10. The resolver asks the name server for the ip address it resolves to 

### <mark style="background: #BABD00;">How HTTPS works:</mark>

<mark style="background: #BABD00;">HTTPS:</mark> HyperText Transfer Protocol Secure
[Source for Comic](https://howhttps.works/why-do-we-need-https/)

<mark style="background: #BABD00;">We need HTTPs for 3 reasons:</mark>
- Privacy
- Integrity
- Innovation

When you browse to a website without HTTPS, anyone on your network can sniff your traffic

Integrity is needed so that your traffic cannot be changed by malicious actors. This is often called a man-in-the-middle attack. Integrity means that the message is not manipulated on the way to its destination.

Identification means that I can check that this message is coming from the correct entity. A digital signature attached to a message can identify the sender.

And when you are browsing the web, identification means that the site that you are visiting is indeed the one you think it is.

HTTPS, via SSL certificates, ensures you are connected exactly with the receiver you would expect.

HTTPS needs a way to provide privacy, integrity, and identification on the web. That mechanism is called 'encryption'.

<mark style="background: #BABD00;">Symmetric encryption:</mark>
- One key used to encrypt data
- Anyone with the key can open the box
- the data is scrambled through a series of steps.
- It was transformed and spread out multiple times. Each time obfuscating the message further.
- To decrypt a message, we just need to apply the same steps, but in reverse order.
- The encryption key is mixed in with the message, so even if you know the encryption algorithm, without the key, the message is still nonsense.
- One main issue with symmetric keys is that they are hard to share safely.

![](https://i.imgur.com/0mXDfah.png)

![](https://i.imgur.com/owCsIMt.png)

<mark style="background: #BABD00;">Asymmetric keys:</mark>
- you have 2 keys.
- One key is public, the other one is private. They are paired and work together.
- Only the private key can open a box locked with the public key pair.
- This is great not only for privacy, but also for identification since we know for sure that only the owner of the 2 keys can open the message.

When you view a website with https, your browser will display a lock on the address bar.
- Your browser communicated with a server, where the website is hosted, and they both established a secure connection to transmit messages.
- They needed to agree on how to communicate securely. If the negotiation is not successful, your browser lets you know by showing an error or warning.
- If an agreement is reached, your browser is happy to display a padlock on the address bar.

This process, the negotiation between a browser and a server, is called 'the handshake'.

<mark style="background: #BABD00;">The handshake:</mark>
1. <mark style="background: #BABD00;">Client Hello:</mark> The client sends a list of SSL/TLS versions and encryption algorithms that it can work with to the server.
2. <mark style="background: #BABD00;">Server Hello:</mark> The server chooses the best SSL/TLS version and encryption algorithm among the ones the client sent it, and based on its preferences. The server replies with its certificate, which includes its public key, so the client can verify who the server is.
3. <mark style="background: #BABD00;">Client Key Exchange:</mark> The client checks the server's certificate to make sure they are legit. The client generates a 'pre-master key' so they can both use it later when they generate a unique key. The client encrypts that pre-master key with the server's public key and then sends it.
4. <mark style="background: #BABD00;">Change cipher spec.</mark> The server uses its private key to decrypt the pre-master key. Now they both generate the same 'shared secret' that they are going to use as a symmetric key. The client sends a test and the server responds.

When the exchange of data is encrypted with SSL/TLS, then we call it HTTPS. The 'S' stands for Secure.

<mark style="background: #BABD00;">SSL</mark> stands for 'Secure Sockets Layer'. A protocol created by Netscape in 1995.

Netscape gave control of SSL protocol to the IETF: Internet Engineering Task Force. Before 1999 ended, IETF released TLS version 1.0 (Which was really SSL 3.1).

SSL was renamed to <mark style="background: #BABD00;">TLS:</mark> Transport Layer Security.

<mark style="background: #BABD00;">A certificate authority (CA) is a third-party organization with 3 main objectives:</mark>
1. Issuing certificates.
2. Confirming the identity of the certificate owner.
3. Providing proof that the certificate is valid.

Becoming a CA is an intense task of security requirements and audits. You need to be trusted to be accepted into a root store - a database of trusted CAs

Apple, Windows, and Mozilla run their own root stores that they pre-install in your computer or device.

<mark style="background: #BABD00;">Three types of CA:</mark>
- <mark style="background: #BABD00;">Domain validated:</mark> The certificate just verifies the domain name, and nothing else. 
- <mark style="background: #BABD00;">Organization validated:</mark> The certificate requires the validation and manual verification of the organization behind the certificate.
- <mark style="background: #BABD00;">Extended validation.</mark> The certificate requires an exhaustive verification of the business.

All valid certificates result in the browser displaying a secure badge in the browser bar. EV certificates generally display the company name as well.

When a CA issues a certificate, they sign the certificate with their root certificate pre-installed in the root store. Most of the time it's an intermediate certificate signed with a root certificate.

![](https://i.imgur.com/2t8fp3E.png)

If the root certificate is compromised, it's easier to revoke the intermediate certificates, since the root certificates are installed on each device.

### <mark style="background: #BABD00;">SAN: What is LUN?</mark>

[Source](https://www.purestorage.com/knowledge/what-is-lun-storage.html)

It’s common for servers to have multiple storage devices. A logical unit number (LUN) assigns a unique value to each drive. A LUN can be assigned to a group of drives configured as a single volume, a partition on a drive, or the entire drive itself. A LUN value can be automatically assigned or manually assigned by an administrator. In this article, we take a look at how LUNs work and the benefits and downsides of using them.  

#### <mark style="background: #BABD00;">What Is a LUN in Storage?</mark>

A LUN (logical unit number) is a unique identifier that defines a storage partition in a [storage area network (SAN)](https://www.purestorage.com/knowledge/what-is-storage-area-network.html) environment for data organization and access. It’s important to note that a LUN is a component in storage organization and not a type of storage device itself. A LUN is a numeric value that points to a physical disk or a logical set of disks. Storage LUNs can also point to a logical set of partitions.

The purpose of a LUN is for clients to make requests from storage space and retrieve data. Usually, LUNs refer to SAN storage, so client computers can map network drives, request data from network storage, or store data on the SAN. Users do not address a LUN when mapping a drive, so only administrators manage LUN identifiers.

#### <mark style="background: #BABD00;">How Does a LUN Work?</mark>

When you build a new server or add a drive to a server, you must partition it. Partitioning forces you to choose a file system. You can choose to make the entire drive space a part of the partition, use only some of the drive space for a partition, or create a logical volume from a group of drives. A LUN can be assigned to the new partition or a set of partitions.

When a server has several disks configured as a RAID (redundant array of independent disks) on SCSI (Small Computer System Interface) ports, the server uses a LUN to communicate with the right storage unit. LUN assignment is common with SCSI disks, but a storage area network (SAN) with other storage ports (e.g., SATA or SAS) could be configured as a RAID and connected via a Fibre Channel where a LUN is assigned.

For a user, the LUN is seen as a single-mounted storage device even if several partitions or a RAID of disks represent a single LUN. A server accessing internal storage needs the LUN to identify the right disk to read to or write from. LUNs assigned to a SAN are necessary for client computers to mount the right disk and assign it a name (e.g., X or Z as a drive letter).

It’s possible for a single LUN to identify thousands of logical volumes, especially in a SAN environment. Administrators can assign a LUN to SAN volumes or the SAN unit can automatically assign a LUN to storage. LUNs can be reassigned by administrators later after bootup to customize configurations to meet certain setup requirements.

#### <mark style="background: #BABD00;">Alternatives and Implementations of LUN Storage</mark>

Every server or network storage device has a LUN so that operating systems can identify a volume to read or write to disks. For many enterprise environments, large network storage devices use RAID storage, which means that several disks could be represented by a single LUN. A large SAN with several disks configured as a single volume could also have a single LUN.

Unless you use older [SCSI technology](https://blog.purestorage.com/purely-technical/iscsi-setup-with-flasharray/) on your personal computer, you only find LUN storage in older SAN or server hardware. Newer SATA (Serial Advanced Technology Attachment) drives are used in servers and personal computers, but SCSI was replaced with SAS (Serial Attached SCSI) or [iSCSI](https://blog.purestorage.com/purely-informational/iscsi-vs-fc-vs-fcoe-choosing-the-right-storage-protocol-for-your-business/) (Internet Small Computer System Interface). Enterprise systems may use SATA or SAS depending on the type of storage and speeds necessary to support a large volume of read and write requests.

#### <mark style="background: #BABD00;">Benefits of Using LUN Storage</mark>

Although a LUN represents some or all of a disk’s storage capacity, it does not always represent a single disk. LUN management software lets administrators choose LUN values for specific disks or volumes, but counting the number of LUN storage values does not represent the total number of disks. The operating system on the remote computer using the LUN can mount it as a drive, so the storage can be given a user-friendly name, usually a letter (e.g., Z drive or X drive).

LUN management lets administrators better control SAN disks and capacity. Enterprise networks use several large-capacity drives to hold petabytes of data, and a LUN lets a workstation mount a single LUN as a user-friendly drive letter. These drive letters often have logical organization (e.g., storage for accounting or sharing documents company-wide) with user-friendly volume letters that most employees know when they transfer documents to network drives.

Although a LUN enables mounting drives and resource sharing on a local device, it does not offer any security. Administrators are still responsible for creating user groups and assigning appropriate permissions to each user group for data access control. Most organizations assign a different drive letter to each user group so there’s no confusion for employees about the purpose of each mounted drive. For example, the X drive might be used for sharing files with anyone within the organization, while the Z drive might represent a link to personal file spaces that only a single employee can access.

#### <mark style="background: #BABD00;">Potential Downsides of a LUN</mark>

A LUN is a numeric assignment for SCSI or a Fibre Channel, but a LUN is often associated with a SAN using a RAID system. A standard user will not run into LUN assignments, but administrators working with legacy hardware might find LUN management challenging. Remember that a LUN represents a slice of storage in a SAN, but it does not always represent a single disk or partition. LUN assignments can be manual or automatic, but most administrators use SAN software to manage LUN values.

Any downsides to LUN are management related. Initial setup might be somewhat convenient, but any new space added to the SAN must be given a LUN or added to existing volumes so that current storage capacity can be expanded. Some administrators might struggle to add new disks to a LUN depending on the operating system and SAN configuration. Most operating systems have an interface to make it somewhat convenient to add storage to current capacity, but administrators might find that they need to troubleshoot when new disks aren’t recognized by the system.

LUNs aren’t always assigned in a SAN or NAS environment. RAID volumes can also exist on a physical server where administrators can assign a LUN. An operating system running on a virtual machine can also use a LUN. Administrators should create a LUN strategy to ensure that reads and writes are optimized for performance. Too many applications and users writing to the same LUN can cause performance degradation, so ensure that LUNs are assigned with performance in mind.

#### <mark style="background: #BABD00;">Conclusion</mark>

Logical unit numbers (LUNs) play an indispensable role in the realm of block storage, serving as a pivotal link between physical storage resources and the data they hold. As we've explored, LUNs facilitate the efficient and flexible allocation of storage space, allowing for the dynamic management of data in various environments, from small-scale setups to large data centres. 

Administrators working with enterprise solutions might find themselves working with LUN management, typically in a large SAN environment. For systems that use SCSI RAID environments, LUN assignment is a component in mounting drives on servers and client workstations. 

Understanding LUNs is just one piece of knowledge crucial for anyone involved in storage administration or data management as it provides the foundational knowledge required for efficient storage utilization and data retrieval. The management and support of your storage infrastructure can consume precious IT resources. Learn how [Pure Professional Services](https://www.purestorage.com/services.html) can help reduce the administrative overhead of managing your storage arrays.

