# <mark style="background: #BABD00;">Week 5 - Docker:</mark>

![](https://i.imgur.com/MhqrXXK.png)

"Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers." - [from Wikipedia](https://en.wikipedia.org/wiki/Docker_(software)).

So stripping the jargon we get two definitions:
1. Docker is a set of tools to deliver software in containers.
2. Containers are packages of software.

![](https://i.imgur.com/8GLas4x.png)

# <mark style="background: #BABD00;">Week 8:</mark>

### <mark style="background: #BABD00;">API Gateway -  Qwik Start:</mark>

API Gateway enables you to provide secure access to your services through a well-defined REST API that is consistent across all of your services, regardless of service implementation. 

<mark style="background: #BABD00;">A consistent API:</mark>
- Makes it easy for app developers to consume your services.
- Enables you to change the backend service implementation without affecting the public API.
- Enables you to take advantage of the scaling, monitoring, and security features built into the Google Cloud.

API Gateway sits in front of a deployed backend service and handles all incoming requests.

### <mark style="background: #BABD00;">Pub/Sub: Qwik Start - Console</mark>

Pub/Sub is a messaging service for exchanging event data among applications and services. A producer of data publishes messages to a Pub/Sub topic. A consumer creates a subscription to that topic. Subscribers either pull messages from a subscription or are configured as webhooks for push subscriptions. Every subscriber must acknowledge each message within a configurable window of time.

A publisher application creates and sends messages to a topic. Subscriber applications create a subscriber to a topic to receive messages from it.

Cloud Pub/Sub is an asynchronous messaging service designed to be highly reliable and scalable.

### <mark style="background: #BABD00;">Cloud Run Functions: Qwik Start - Console</mark>

Cloud Run function is a piece of code that runs in response to an event, such as an HTTP request, a message from a messaging service, or a file upload. Cloud events are _things_ that happen in your cloud environment. These might be things like changes to data in a database, files added to a storage system, or a new virtual machine instance being created.

Since Cloud Run functions are event-driven, they only run when something happens. This makes them a good choice for tasks that need to be done quickly or that don't need to be running all the time.

<mark style="background: #BABD00;">For example, you can use a Cloud Run function to:</mark>
- automatically generate thumbnails for images that are uploaded to Cloud Storage.
- send a notification to a user's phone when a new message is received in Pub/Sub.
- process data from a Cloud Firestore database and generate a report.

You can write your code in any language that supports Node.js, and you can deploy your code to the cloud with a few clicks. Once your Cloud Run function is deployed, it will automatically start running in response to events.

Cloud Run functions is a serverless execution environment for event driven services on Google Cloud.

# <mark style="background: #BABD00;">Week 9:</mark>

### <mark style="background: #BABD00;">Network Load Balancer:</mark>

External passthrough Network Load Balancers are regional, layer 4 load balancers that distribute external traffic among backends (instance groups or network endpoint groups (NEGs)) in the same region as the load balancer. These backends must be in the same region and project but can be in different VPC networks. These load balancers are built on [Maglev](https://research.google/pubs/maglev-a-fast-and-reliable-software-network-load-balancer/) and the [Andromeda network virtualization stack](https://cloudplatform.googleblog.com/2014/04/enter-andromeda-zone-google-cloud-platforms-latest-networking-stack.html).

<mark style="background: #BABD00;">External passthrough Network Load Balancers can receive traffic from:</mark>
- Any client on the internet
- Google Cloud VMs with external IPs
- Google Cloud VMs that have internet access through Cloud NAT or instance-based NAT

External passthrough Network Load Balancers are _not proxies_. The load balancer itself doesn't terminate user connections. Load-balanced packets are sent to the backend VMs with their source and destination IP addresses, protocol, and, if applicable, ports, unchanged. The backend VMs then terminate user connections. Responses from the backend VMs go directly to the clients, not back through the load balancer. This process is known as direct server return (DSR).

<mark style="background: #BABD00;">Backend service-based external passthrough Network Load Balancers support the following features:</mark>
- <mark style="background: #BABD00;">Managed and unmanaged instance group backends.</mark> Backend service-based external passthrough Network Load Balancers support both managed and unmanaged instance groups as backends. Managed instance groups automate certain aspects of backend management and provide better scalability and reliability as compared to unmanaged instance groups.
- <mark style="background: #BABD00;">Zonal NEG backends:</mark> Backend service-based external passthrough Network Load Balancers support using zonal NEGs with `GCE_VM_IP` endpoints. Zonal NEG `GCE_VM_IP` endpoints let you do the following:
    - Forward packets to any network interface, not just `nic0`.
    - Place the same `GCE_VM_IP` endpoint in two or more zonal NEGs connected to different backend services.
- <mark style="background: #BABD00;">Support for multiple protocols:</mark> Backend service-based external passthrough Network Load Balancers can load-balance TCP, UDP, ESP, GRE, ICMP, and ICMPv6 traffic.
- <mark style="background: #BABD00;">Support for IPv6 connectivity:</mark> Backend service-based external passthrough Network Load Balancers can handle both IPv4 and IPv6 traffic.
- <mark style="background: #BABD00;">Fine-grained traffic distribution control:</mark> A backend service allows [traffic to be distributed](https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#traffic-distribution) according to a configurable [session affinity](https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#session-affinity), [connection tracking mode](https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#tracking-mode), and [weighted load balancing](https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#weighted-lb). The backend service can also be configured to enable [connection draining](https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#connection_draining) and designate [failover backends](https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#failover) for the load balancer. Most of these settings have default values that let you get started quickly.
- <mark style="background: #BABD00;">Support for non-legacy health checks:</mark> Backend service-based external passthrough Network Load Balancers let you use [health checks](https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#health-checks) that match the type of traffic (TCP, SSL, HTTP, HTTPS, or HTTP/2) that they are distributing.
- <mark style="background: #BABD00;">Google Cloud Armor integration:</mark> Google Cloud Armor supports advanced network DDoS protection for external passthrough Network Load Balancers. For more information, see [Configure advanced network DDoS protection](https://cloud.google.com/armor/docs/advanced-network-ddos).
- <mark style="background: #BABD00;">GKE integration:</mark> If you are building applications in GKE, we recommend that you use the built-in [GKE Service controller](https://cloud.google.com/kubernetes-engine/docs/concepts/service), which deploys Google Cloud load balancers on behalf of GKE users. This is the same as the standalone load balancing architecture described on this page, except that its lifecycle is fully automated and controlled by GKE.
    
<mark style="background: #BABD00;">Related GKE documentation:</mark> 
- [LoadBalancer Service concepts](https://cloud.google.com/kubernetes-engine/docs/concepts/service-load-balancer)
- [Exposing applications using Services](https://cloud.google.com/kubernetes-engine/docs/how-to/exposing-apps)

### <mark style="background: #BABD00;">Application Load Balancer</mark>

This document introduces the concepts that you need to understand how to configure an external Application Load Balancer.

An external Application Load Balancer is a proxy-based Layer 7 load balancer that enables you to run and scale your services behind a single external IP address. The external Application Load Balancer distributes HTTP and HTTPS traffic to backends hosted on a variety of Google Cloud platforms (such as Compute Engine, Google Kubernetes Engine (GKE), Cloud Storage, and so on), as well as external backends connected over the internet or via hybrid connectivity. For details, see [Application Load Balancer overview: Use cases](https://cloud.google.com/load-balancing/docs/application-load-balancer#use-cases).

<mark style="background: #BABD00;">Modes of operation:</mark>
- <mark style="background: #BABD00;">Global external Application Load Balancer</mark> This is a global load balancer that is implemented as a managed service on [Google Front Ends (GFEs)](https://cloud.google.com/docs/security/infrastructure/design#google-frontend-service). It uses the open-source [Envoy proxy](https://www.envoyproxy.io/) to support [advanced traffic management](https://cloud.google.com/load-balancing/docs/https/traffic-management-global) capabilities such as traffic mirroring, weight-based traffic splitting, request/response-based header transformations, and more.
- <mark style="background: #BABD00;">Classic Application Load Balancer:</mark> This is the classic external Application Load Balancer that is global in Premium Tier but can be configured to be regional in Standard Tier. This load balancer is implemented on [Google Front Ends (GFEs)](https://cloud.google.com/docs/security/infrastructure/design#google-frontend-service). GFEs are distributed globally and operate together using Google's global network and control plane.
- <mark style="background: #BABD00;">Regional external Application Load Balancer:</mark> This is a regional load balancer that is implemented as a managed service on the open-source [Envoy proxy](https://www.envoyproxy.io/). It includes [advanced traffic management](https://cloud.google.com/load-balancing/docs/https/traffic-management-regional) capabilities such as traffic mirroring, weight-based traffic splitting, request/response-based header transformations, and more.

### <mark style="background: #BABD00;">IAM Custom Roles:</mark>

Cloud IAM provides the right tools to manage resource permissions with minimum fuss and high automation. You don't directly grant users permissions. Instead, you grant them roles, which bundle one or more permissions. This allows you to map job functions within your company to groups and roles. Users get access only to what they need to get the job done, and admins can easily grant default permissions to entire groups of users.

<mark style="background: #BABD00;">There are two kinds of roles in Cloud IAM:</mark>
- Predefined Roles
- Custom Roles

<mark style="background: #BABD00;">Predefined roles:</mark> are created and maintained by Google. Their permissions are automatically updated as necessary, such as when new features or services are added to Google Cloud.

**Custom roles** are user-defined, and allow you to bundle one or more supported permissions to meet your specific needs. Custom roles are not maintained by Google; when new permissions, features, or services are added to Google Cloud, your custom roles will not be updated automatically. You create a custom role by combining one or more of the available Cloud IAM permissions. Permissions allow users to perform specific actions on Google Cloud resources.

Cloud IAM also provides the ability to create customized Cloud IAM roles. You can create a custom Cloud IAM role with one or more permissions and then grant that custom role to users. Cloud IAM provides a UI and API for creating and managing custom roles.

<mark style="background: #BABD00;">Key Point:</mark> Custom roles enable you to enforce the principle of least privilege, ensuring that the user and service accounts in your organization have only the permissions essential to performing their intended functions.

<mark style="background: #BABD00;">Note:</mark> You can create a custom role at the organization level and at the project level. However, you cannot create custom roles at the folder level.

You create a custom role by combining one or more of the available Cloud IAM permissions. Permissions allow users to perform specific actions on Google Cloud resources.

### <mark style="background: #BABD00;">Importing Data to a firestore database:</mark>

![](https://i.imgur.com/NyigvF8.png)

# <mark style="background: #BABD00;">Week 10:</mark>

### <mark style="background: #BABD00;">Build a Serverless Web App with Firebase</mark>

### <mark style="background: #BABD00;">Hosting a Web App on Google Cloud Using Compute Engine</mark>

There are many ways to deploy web sites within Google Cloud. Each solution offers different features, capabilities, and levels of control. Compute Engine offers a deep level of control over the infrastructure used to run a web site, but also requires a little more operational management compared to solutions like Google Kubernetes Engines (GKE), App Engine, or others. With Compute Engine, you have fine-grained control of aspects of the infrastructure, including the virtual machines, load balancers, and more.

<mark style="background: #BABD00;">Note:</mark> In a production environment, you may want to separate each microservice into their own instance and instance group to allow them to scale independently.

<mark style="background: #BABD00;">Note:</mark> Separate health checks for load balancing and for auto-healing will be used. Health checks for load balancing can and should be more aggressive because these health checks determine whether an instance receives user traffic. You want to catch non-responsive instances quickly so you can redirect traffic if necessary. In contrast, health checking for auto-healing causes Compute Engine to proactively replace failing instances, so this health check should be more conservative than a load balancing health check.

# <mark style="background: #BABD00;">Week 11:</mark>

### <mark style="background: #BABD00;">VPC Networking Fundamentals</mark>

Google Cloud Virtual Private Cloud (VPC) provides networking functionality to Compute Engine virtual machine (VM) instances, Kubernetes Engine containers and App Engine Flex. In other words, without a VPC network you cannot create VM instances, containers or App Engine applications. Therefore, each Google Cloud project has a **default** network to get you started.

You can think of a VPC network the same way you would think of a physical network, except that it is virtualized within Google Cloud. A VPC network is a global resource which consists of a list of regional virtual subnetworks (subnets) in data centres, all connected by a global wide area network (WAN). VPC networks are logically isolated from each other in Google Cloud.

Routes tell VM instances and the VPC network how to send traffic from an instance to a destination, either inside the network or outside of Google Cloud.

Each VPC network comes with some default routes to route traffic among its subnets and send traffic from eligible instances to the Internet.

Each VPC network implements a distributed virtual firewall that you can configure. Firewall rules allow you to control which packets are allowed to travel to which destinations.

Every VPC network has two implied firewall rules that block all incoming connections and allow all outgoing connections.

<mark style="background: #BABD00;">Notice that there are 4 Ingress firewall rules for the default network:</mark>
- default-allow-icmp
- default-allow-internal
- default-allow-rdp
- default-allow-ssh

These firewall rules allow <mark style="background: #BABD00;">ICMP</mark>, <mark style="background: #BABD00;">RDP</mark> and <mark style="background: #BABD00;">SSH</mark> ingress traffic from anywhere (0.0.0.0/0) and all **TCP**, **UDP** and **ICMP** traffic within the network (10.128.0.0/9). The <mark style="background: #BABD00;">Targets</mark>, <mark style="background: #BABD00;">Source filters</mark>, <mark style="background: #BABD00;">Protocols/ports</mark> and <mark style="background: #BABD00;">Action</mark> columns explain these rules.

The <mark style="background: #BABD00;">External IP addresses</mark> for both VM instances are ephemeral. If an instance is stopped, any ephemeral external IP addresses assigned to the instance are released back into the general Compute Engine pool and become available for use by other projects.

When a stopped instance is started again, a new ephemeral external IP address is assigned to the instance. Alternatively, you can reserve a static external IP address, which assigns the address to your project indefinitely until you explicitly release it.

### <mark style="background: #BABD00;">Service Accounts and Roles: Fundamentals</mark>

Service accounts are a special type of Google account that grant permissions to virtual machines instead of end users. Service accounts are primarily used to ensure safe, managed connections to APIs and Google Cloud services. Granting access to trusted connections and rejecting malicious ones is a must-have security feature for any Google Cloud project.

A service account is a special Google account that belongs to your application or a [virtual machine](https://cloud.google.com/compute/docs/instances/) (VM) instead of an individual end user. Your application uses the service account to [call the Google API of a service](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#authorizingrequests), so that the users aren't directly involved.

For example, a Compute Engine VM may run as a service account, and that account can be given permissions to access the resources it needs. This way the service account is the identity of the service, and the service account's permissions control which resources the service can access.

A service account is identified by its email address, which is unique to the account.

 <mark style="background: #BABD00;">User-managed service accounts</mark>
When you create a new Cloud project using Google Cloud console and if Compute Engine API is enabled for your project, a Compute Engine Service account is created for you by default. It is identifiable using the email:

`PROJECT_NUMBER-compute@developer.gserviceaccount.com`

If your project contains an App Engine application, the default App Engine service account is created in your project by default. It is identifiable using the email:

`PROJECT_ID@appspot.gserviceaccount.com`

<mark style="background: #BABD00;">Google-managed service accounts:</mark>
In addition to the user-managed service accounts, you might see some additional service accounts in your project’s IAM policy or in the console. These service accounts are created and owned by Google. These accounts represent different Google services and each account is automatically granted IAM roles to access your Google Cloud project.

<mark style="background: #BABD00;">Google APIs service account:</mark>
An example of a Google-managed service account is a Google API service account identifiable using the email:

`PROJECT_NUMBER@cloudservices.gserviceaccount.com`

This service account is designed specifically to run internal Google processes on your behalf and is not listed in the **Service Accounts** section of the console. By default, the account is automatically granted the project editor role on the project and is listed in the **IAM** section of the console. This service account is deleted only when the project is deleted.

<mark style="background: #BABD00;">Understanding IAM roles:</mark>
When an identity calls a Google Cloud API, Google Cloud Identity and Access Management requires that the identity has the appropriate permissions to use the resource. You can grant permissions by granting roles to a user, a group, or a service account.

<mark style="background: #BABD00;">There are three types of roles in Cloud IAM:</mark>
- <mark style="background: #BABD00;">Primitive roles:</mark> which include the Owner, Editor, and Viewer roles that existed prior to the introduction of Cloud IAM.
- <mark style="background: #BABD00;">Predefined roles</mark> which provide granular access for a specific service and are managed by Google Cloud.
- <mark style="background: #BABD00;">Custom roles:</mark> which provide granular access according to a user-specified list of permissions.

### <mark style="background: #BABD00;">Cloud Run Functions: Qwik Start - Command Line</mark>

A Cloud Run function is a piece of code that runs in response to an event, such as an HTTP request, a message from a messaging service, or a file upload. Cloud events are _things_ that happen in your cloud environment. These might be things like changes to data in a database, files added to a storage system, or a new virtual machine instance being created.

Since Cloud Run functions are event-driven, they only run when something happens. This makes them a good choice for tasks that need to be done quickly or that don't need to be running all the time.

<mark style="background: #BABD00;">For example, you can use a Cloud Run function to:</mark>
- automatically generate thumbnails for images that are uploaded to Cloud Storage.
- send a notification to a user's phone when a new message is received in Pub/Sub.
- process data from a Cloud Firestore database and generate a report.

You can write your code in any language that supports Node.js, and you can deploy your code to the cloud with a few clicks. Once your Cloud Run function is deployed, it will automatically start running in response to events.

<mark style="background: #BABD00;">Note:</mark> Cloud Run functions are event driven, meaning a trigger type must be specified. When deploying a new function, `--trigger-topic`, `--trigger-bucket`, or `--trigger-http` are common trigger events. When deploying an update to an existing function, the function keeps the existing trigger unless otherwise specified.

Serverless lets you write and deploy code without the hassle of managing the underlying infrastructure.