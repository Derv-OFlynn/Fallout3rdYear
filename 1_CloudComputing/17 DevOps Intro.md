<mark style="background: #BABD00;">What is DevOps?</mark>
- Infrastructure As Code 
- Desired State Configuration

### <mark style="background: #BABD00;">Traditional Development and Operations:</mark>

![](https://i.imgur.com/y4sfU1v.png)

![](https://i.imgur.com/0kbQbAj.png)

![](https://i.imgur.com/fe8NI1R.png)

### <mark style="background: #BABD00;">Continuous Integration:</mark>

![](https://i.imgur.com/dGboCXj.png)

![](https://i.imgur.com/xAnMxcl.png)

### <mark style="background: #BABD00;">Testing:</mark>

<mark style="background: #BABD00;">Unit testing:</mark>

Comes from mathematics where the unit circle has a circle of 1.  A unit test should test one thing and one thing only. If expected behaviour = accepted behaviour, it passes. Can be fully automated as it is completely binary in terms of passing/failing.

<mark style="background: #BABD00;">Integration Testing:</mark>

Tests multiple units integrated together. All the way up.

<mark style="background: #BABD00;">System Testing:</mark>

Testing the system at every level beyond core functionality. e.g. performance testing, fuzzy testing.

<mark style="background: #BABD00;">UAT:</mark>

See how user reacts.

### <mark style="background: #BABD00;">DevOps: the three stage conversation:</mark>

![](https://i.imgur.com/gpwcdiI.png)

• Collaboration of People.
• Convergence of Processes.
• Creation/Exploitation of Tools.

### <mark style="background: #BABD00;">DevOps: from individual stand-alone silos to an integrated automated pipeline.</mark>

<mark style="background: #BABD00;">Integration - People and Processes:</mark>

![](https://i.imgur.com/VR6o5lj.png)

The goal is to create a single, integrated seamless automated pipeline of activities.
### <mark style="background: #BABD00;">The consequences of Inefficiency:</mark>

![](https://i.imgur.com/cnDS0NA.png)

### <mark style="background: #BABD00;">DevOps Benefits:</mark>

- Reduces 'Tribal Knowledge'
- Consistency and Repeatability (Automation).
- Speed and Productivity (deploy faster). 
- Reliability.
- Excellence — codify best practices.
- Communication and Fast/frequent feedback.

### <mark style="background: #BABD00;">What does DevOps look like?</mark>

![](https://i.imgur.com/ugmctd7.png)

### <mark style="background: #BABD00;">Fundamental DevOps Principles:</mark>

![](https://i.imgur.com/ByEEok8.png)

### <mark style="background: #BABD00;">DevOps Best Practices:</mark>

- Infrastructure as Code (IaC)
- Continuous Integration
- Automated Testing
- Continuous Deployment
- Release Management
- App Performance Monitoring
- Load Testing & Auto-Scale
- Fast Feedback Loops
- Availability Monitoring
- Change/Configuration Management
- Feature Flags
- Automated Environment De-Provisioning
- Self Service Environments
- Automated Recovery (Rollback & Roll-Forward)
- Hypothesis Driven Development
- Testing in Production
- Fault Injection
- Usage Monitoring/User Telemetry

### <mark style="background: #BABD00;">Infrastructure as Code (IaC):</mark>

<mark style="background: #BABD00;">Many IT teams still rely on:</mark>
- manual configurations
- custom scripts
- outdated tools to manage infrastructure
- resulting in errors and slow deployments

<mark style="background: #BABD00;">By treating your Infrastructure as software:</mark>
- Code can be managed with the same tools and processes as software
- Such as version control, continuous integration, code reviews, automated testing, etc.
- Thus Infrastructure can be changed more easily, rapidly, safely and reliably.

![](https://i.imgur.com/GEDw7w4.png)

<mark style="background: #BABD00;">Programmable Infrastructure (laC):</mark>
- Writing in a high-level descriptive or declarative language.
- To manage configurations and to automate provisioning of resources and the deployment of infrastructure.
- Involves using tried and tested software development practices (including design patterns).
- To not only provision Infrastructure but all the processes governing the management of said Infrastructure.

Differs from <mark style="background: #BABD00;">infrastructure automation</mark>, which just involves replicating steps multiple times and reproducing them on several servers.

<mark style="background: #BABD00;">Programmable Infrastructure (IaC):</mark>
- The knowledge of server provisioning, configuration management and deployment is no longer only with the systems admins.
- Developers can easily engage in the activities, because they can easily write infrastructure code in the languages that they are familiar with.

<mark style="background: #BABD00;">A whole host of tools have sprung up to make the whole process easier:</mark>
- Vagrant, ansible, puppet, Chef, Salt, Terraform, Consul, Bcfg2, CFEngine, etc.
- Many of these tools provide RESTFul APIs that leverage to support any desired degree of interoperability.

![](https://i.imgur.com/vGuVViZ.png)

### <mark style="background: #BABD00;">Idempotent:</mark>

The dictionary definition:- denoting an element of a set that is unchanged in value when multiplied or otherwise operated on by itself.

Idempotence is simply a word that describes an operation that will have the same effect whether you run it once or 1001 times.

Adding one is not idempotent because the result keeps incrementing, but multiplying by one is idempotent because the answer is the same no matter how many times you multiply it!

In the context of Infrastructure as Code, if a virtualized resource or software component is already installed or configured, an idempotent tool will not try to reinstall or reconfigure the component, even if it is given the command to do so.

### <mark style="background: #BABD00;">Advantages:</mark>

Both development and testing become much easier.

The same configuration can be applied to local physical servers or virtualised Cloud based servers.

The ability to use version control on your infrastructure code implies that you can easily track all the changes in your infrastructure environment. Therefore, you have an easier option of rolling back configuration changes to a previous working configuration in case of a problem.

<mark style="background: #BABD00;">Idempotent:</mark> you can go from any arbitrary state to a specific desired state.

### <mark style="background: #BABD00;">Disadvantages:</mark>

Significant planning required upfront before the configuration - such as choosing the right tools.

Bad configurations could get duplicated on all the servers

Configuration drift, in which the server configurations are modified on the machines (for example, through hot-fixes without modifying the original templates), makes configurations on the server and in the template to differ.

This is especially true if strict discipline is not followed.

### <mark style="background: #BABD00;">Desired State Configuration:</mark>

Configurations are documents that describe an environment. Environments typically consist of "nodes", which are commonly virtual or physical machines.

The management and maintenance of servers quickly becomes complex without standardisation.

The danger is that we end up with a plethora of scripts in order to manage a server, all more complicated than the other, and this works.

DSC gives us a declarative model for system configuration management. What that really means is that we can specify how we want a workstation or server (a 'node') to be configured and we leave it to the tool to make it happen on those target 'nodes'. We don't have to specify how we want it to happen.

### <mark style="background: #BABD00;">Benefits of DSC:</mark>

To simplify your sysadmin tasks by configuring one or more devices automatically

To be able to configure machines identically with the aim to standardise them.

To ensure, at a given time, that the configuration of a machine always be identical to its initial configuration, so as to avoid drift.

Deployment on demand as a Cloud strategy, or 'en masse', is largely automated and simplified.

### <mark style="background: #BABD00;">Two Types of architecture with DSC:</mark>

<mark style="background: #BABD00;">Push mode:</mark> the configurations are sent ("pushed") manually towards one or more units that we call "node". This action is done by an administrator.

<mark style="background: #BABD00;">Pull mode:</mark> a "pull server" is created and the nodes contact this server at regular intervals so as to obtain their configuration.

### <mark style="background: #BABD00;">DSC Push Mode:</mark>

![](https://i.imgur.com/OBqEvsC.png)

### <mark style="background: #BABD00;">DSC Pull Mode:</mark>

![](https://i.imgur.com/axdcfNS.png)