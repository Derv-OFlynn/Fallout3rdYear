#CloudComputing

### <mark style="background: #BABD00;">What is Docker?</mark>

Docker is an open-source project that automates the deployment of applications inside software containers, by providing an additional layer of abstraction and automation of operating system–level virtualisation on Linux.  - [Source: en.wikipedia.org]  

Docker allows you to package an application with all of its dependencies into a standardised unit for software development.  - [www.docker.com]

### <mark style="background: #BABD00;">The challenge:</mark>

![](https://i.imgur.com/bQAjcRU.png)

<mark style="background: #BABD00;">Results in NXM compatibility nightmare:</mark>

![](https://i.imgur.com/XMT3k90.png)

### <mark style="background: #BABD00;">Docker is a shipping container for code:</mark>

![](https://i.imgur.com/Vx0INie.png)

<mark style="background: #BABD00;">Solves the NXM matrix problem:</mark>

![](https://i.imgur.com/ic5kEeb.png)

### <mark style="background: #BABD00;">Docker Containers:</mark>

Docker container wrap a piece of software in a complete file system that contains everything needed to run:  
- Code, runtime, system tools, system libraries  
- Anything that can be installed on a server  

This guarantees that the software will always run the same, regardless of the environment it is running in.

![](https://i.imgur.com/ByKnuRX.png)

### <mark style="background: #BABD00;">Why containers matter:</mark>

![](https://i.imgur.com/Bjkok23.png)

### <mark style="background: #BABD00;">Docker containers</mark>

<mark style="background: #BABD00;">Lightweight:</mark>
- Containers running on one machine all share the same OS kernel  
- They start instantly and make more efficient use of RAM  
- Images are constructed from layered file systems  
- They can share common files, making disk usage and image downloads much more efficient

<mark style="background: #BABD00;">Open:</mark>
- Based on open standards  
- Allowing containers to run on all major Linux distributions and Microsoft OS with support for every infrastructure

<mark style="background: #BABD00;">Secure:</mark>
- Containers isolate applications from each other and the underlying infrastructure while providing an added layer of protection for the application

### <mark style="background: #BABD00;">Containers vs VMs:</mark>

Containers have similar resource isolation and allocation benefits as VMs but a different architectural approach allows them to be much more portable and efficient

<mark style="background: #BABD00;">Docker Container:</mark>
- It includes the application and all of its dependencies, but share the kernel with other containers.  
- They run as an isolated process in userspace on the host operating system.  
- Docker containers run on any computer, on any infrastructure and in any cloud

![](https://i.imgur.com/Avz94PV.png)

<mark style="background: #BABD00;">VM:</mark>
- Each virtual machine includes the application, the necessary binaries and libraries and an entire guest operating system - all of which may be tens of GBs in size

![](https://i.imgur.com/3roZxCc.png)

### <mark style="background: #BABD00;">Why are docker containers lightweight?</mark>

<mark style="background: #BABD00;">VMs:</mark> Every app, every copy of an app, and every slight modification of the app requires a new virtual server
![](https://i.imgur.com/OW9QmZP.png)

<mark style="background: #BABD00;">Containers:</mark>

![](https://i.imgur.com/7ukDqSv.png)

### <mark style="background: #BABD00;">What are the basics of the Docker system?</mark>

![](https://i.imgur.com/nVGc81q.png)

### <mark style="background: #BABD00;">Changes and Updates:</mark>

![](https://i.imgur.com/YQ9LHL1.png)

### <mark style="background: #BABD00;">How does this help you build better software?</mark>

<mark style="background: #BABD00;">Accelerate Developer Onboarding:</mark>
- Stop wasting hours trying to setup developer environments  
- Spin up new instances and make copies of production code to run locally  
- With Docker, you can easily take copies of your live environment and run on any new endpoint running Docker.

<mark style="background: #BABD00;">Empower Developer Creativity:</mark>
- The isolation capabilities of Docker containers free developers from the worries of using “approved” language stacks and tooling  
- Developers can use the best language and tools for their application service without worrying about causing conflict issues

<mark style="background: #BABD00;">Eliminate Environment Inconsistencies:</mark>
- By packaging up the application with its configs and dependencies together and shipping as a container, the application will always work as designed locally, on another machine, in test or production  
- No more worries about having to install the same configs into a different environment


### <mark style="background: #BABD00;">Easily Share and Collaborate on Applications:</mark>

Docker creates a common framework for developers and sysadmins to work together on distributed applications.

<mark style="background: #BABD00;">Distribute and share content:</mark>
- Store, distribute and manage your Docker images in your Docker Hub with your team  
- Image updates, changes and history are automatically shared across your organization.  

<mark style="background: #BABD00;">Simply share your application with others:</mark>  
- Ship your containers to others without worrying about different environment dependencies creating issues with your application.  
- Other teams can easily link to or test against your app without having to learn or worry about how it works

### <mark style="background: #BABD00;">Getting started with Docker:</mark>

- install Docker  
- run a software image in a container  
- browse for an image on Docker Hub  
- create your own image and run it in a container  
- create a Docker Hub account and an image repository  
- create an image of your own  
- push your image to Docker Hub for others to use

### <mark style="background: #BABD00;">Example: a health and fitness Mobile App:</mark>

You’ve been tasked with creating the REST API for a mobile app for tracking health and fitness  

You code the first endpoint using the development environment on your laptop  

After running all the unit tests and seeing that they passed, you check your code into the Git repository and let the QA engineer know that the build is ready for testing  

The QA engineer dutifully deploys the most recent build to the test environment, and within the first few minutes of testing discovers that your recently developed REST endpoint is broken  

After spending a few hours troubleshooting alongside the QA engineer, you discover that the test environment is using an outdated version of a third-party library, and this is what is causing your REST endpoints to break

<mark style="background: #BABD00;">Slight differences between development, test, stage, and production environments can wreak mayhem on an application</mark>

<mark style="background: #BABD00;">Solution:</mark>
- Traditional approaches for dealing with this problem, such as change management processes, are too cumbersome for today’s rapid build and deploy cycles  
- What is needed instead is a way to transfer an environment seamlessly from development to test, eliminating the need for manual and error prone resource provisioning and configuration.  
- You can create Docker images from a running container. For example, one could launch a container, install a bunch of software packages using a package manager like APT or yum, and then commit those changes to a new Docker image.

<mark style="background: #BABD00;">Solution in Example:</mark>
- First, define a Docker image for launching a container for running the REST endpoint  
- Use this to test our code on a laptop, and the QA engineer can use this to test the code in Google Compute Engine/AWS EC2/Azure VM.  
- The REST endpoints are going to be developed using Ruby and the Sinatra framework, so these will need to be installed in the image  
- The back end will use Google Firestore/Amazon DynamoDB/Azure CosmosDB

![](https://i.imgur.com/rjSx09H.png)