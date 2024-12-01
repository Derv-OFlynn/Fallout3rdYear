### <mark style="background: #BABD00;">What is Continuous Delivery (CD) ?</mark>

Continuous Delivery is the ability to get changes of all types - including new features, configuration changes, bug fixes and experiments—into production, or into the hands of <mark style="background: #BABD00;">users</mark>, <mark style="background: #BABD00;">safely</mark> and quickly in a <mark style="background: #BABD00;">sustainable</mark> way.  

Our goal is to make deployments whether of a large-scale distributed system, a complex production environment, an embedded system, or an app—predictable, routine affairs that can be performed on demand.  

We achieve all this by ensuring our code is always in a deployable state, even in the face of teams of thousands of developers making changes on a daily basis.

![](https://i.imgur.com/Vbn2Y7g.png)

### <mark style="background: #BABD00;">Why Continuous Delivery?</mark>

It is often assumed that if we want to deploy software more frequently, we must accept lower levels of stability and reliability in our systems. 

High performance teams consistently deliver services faster and more reliably than their low performing competition.  

CD provides an distinct competitive advantage for organizations who embrace it

### <mark style="background: #BABD00;">Benefits of Continuous Delivery?</mark>

<mark style="background: #BABD00;">There are six key benefits of Continuous Delivery:</mark>  
- Low risk releases.  
- Faster time to market.  
- Higher Quality.  
- Lower costs.  
- Better Products.  
- Happier Teams.
- Low risk releases  

The primary goal of continuous delivery is to make software deployments painless, low-risk events that can be performed at any time, on demand.  

By applying patterns such as blue-green deployments it is relatively straightforward to achieve zero-downtime deployments that are undetectable to users  
- a pattern is "a named strategy for solving a recurring problem". 
- describes the core of the solution to the problem in such a way that you can use this solution a million times over without ever doing it the same way twice.

<mark style="background: #BABD00;">Blue-Green Deployments:</mark>  
- One of the challenges with automating deployment is the cut-over itself, taking software from the final stage of testing to live production.  
- You usually need to do this quickly in order to minimize downtime.  
- The blue-green deployment approach does this by ensuring you have two production environments, as identical as possible.

![](https://i.imgur.com/Wlr1m68.png)

Blue-green deployment also gives you a rapid way to rollback - if anything goes wrong you switch the router back to your blue environment.

<mark style="background: #BABD00;">Faster time to market:</mark>  
- It’s not uncommon for the integration and test/fix phase of the traditional phased software delivery lifecycle to consume weeks or even months.  
- By automating the build and deployment, environment provisioning, and regression testing processes, We also avoid the large amounts of re-work that plague the phased approach.

<mark style="background: #BABD00;">Higher Quality:</mark>  
- When developers have automated tools that discover regressions within minutes, teams are freed to focus their effort on user research and higher level testing activities such as exploratory testing, usability testing, and performance and security testing.  
- By building a deployment pipeline, these activities can be performed continuously throughout the delivery process, ensuring quality is built in to products and services from the beginning.

<mark style="background: #BABD00;">Higher Quality:</mark>  
- When developers have automated tools that discover regressions within minutes, teams are freed to focus their effort on user research and higher level testing activities such as exploratory testing, usability testing, and performance and security testing.  
- By building a deployment pipeline, these activities can be performed continuously throughout the delivery process, ensuring quality is built in to products and services from the beginning.

<mark style="background: #BABD00;">Better Products:</mark>  
- Continuous delivery makes it economic to work in small  batches.  
- We can get feedback from users throughout the delivery lifecycle based on working software.  
- Techniques such as <mark style="background: #BABD00;">A/B testing</mark> enable us to take a hypothesis-driven approach to product development whereby we can test ideas with users before building out whole features  
- This means we can avoid the 2/3 of features we build that deliver zero or negative value to our businesses.

### <mark style="background: #BABD00;">Benefits of Continuous Delivery?</mark>

<mark style="background: #BABD00;">A/B Testing:</mark>
![](https://i.imgur.com/qfyWeco.png)

<mark style="background: #BABD00;">Happier Teams:</mark>  
- Continuous Delivery makes releases less painful and reduces team burnout.  
- When we release more frequently, software delivery teams can engage more actively with users, learn which ideas work and which don’t, and see first-hand the outcomes of the work they have done.  
- By removing the low-value painful activities associated with software delivery, we can focus on what we care about most - delivering value to our customers.

### <mark style="background: #BABD00;">Five Principles of Continuous Delivery:</mark>

<mark style="background: #BABD00;">There are five principles at the heart of continuous delivery:</mark>  
- Build quality in.  
- Work in small batches.  
- Computers perform repetitive tasks, people solve problems.  
- Relentlessly pursue continuous improvement.  
- Everyone is responsible.

<mark style="background: #BABD00;">Build Quality In:</mark>  
- W. Edwards Deming, a key figure in the history of the Lean movement offered 14 key principles for management.  
- Principle three states, “Cease dependence on inspection to achieve quality. Eliminate the need for inspection on a mass basis by building quality into the product in the first place.”  
- It’s much cheaper to fix problems and defects if we find them immediately—ideally before they are ever checked into version control, by running automated tests locally
- Creating and evolving feedback loops to detect problems as early as possible is an essential and never-ending work in continuous delivery.  
- If we find a problem in our exploratory testing, we must not only fix it, but then ask: How could we have caught the problem with an automated acceptance test?  
- When an acceptance test fails, we should ask: Could we have written a unit test to catch this problem?

<mark style="background: #BABD00;">Work in Small Batches:</mark>  
- In traditional phased approaches to software development, handoffs from dev to test or test to IT operations consist of whole releases: months worth of work by teams consisting of tens or hundreds of people.  
- In Continuous Delivery, we take the opposite approach, and try and get every change in version control as far towards release as we can, getting comprehensive feedback as rapidly as possible.  
- Working in small batches has many benefits. It reduces the time it takes to get feedback on our work, makes it easier to triage and remediate problems, increases efficiency and motivation, and prevents us from succumbing to the sunk cost fallacy.
- <mark style="background: #BABD00;">Suck Cost Fallacy:</mark> Reasoning that further investment is  warranted on the fact that the resources already invested will be lost otherwise, not taking into consideration the overall losses involved in the further investment (Short term thinking).  
- The reason we work in small batches is because of the large fixed cost of handing off changes.  
- A key goal of continuous delivery is to change the economics of the software delivery process to make it economically viable to work in small batches so we can obtain the many benefits of this approach.

### <mark style="background: #BABD00;">Computers perform repetitive tasks, people solve problems. </mark> 

One of the earliest philosophical ideas of the Toyota tradition is jidoka, sometimes translated as "automation with a human touch."  

Jidoka is one of the two pillars of the Toyota Production System along with just-in-time.  

The goal is for computers to perform simple, repetitive tasks, such as regression testing, so that humans can focus on problem-solving.  

Thus computers and people complement each other.

### <mark style="background: #BABD00;">Toyota Jidoka</mark>  

Jidoka sometimes is called autonomation, meaning automation with human intelligence.  

This is because it gives equipment the ability to distinguish good parts from bad autonomously, without being monitored by an operator.  

This eliminates the need for operators to continuously watch machines and leads in turn to large productivity gains because one operator can handle several machines, often termed multi-process handling.

![](https://i.imgur.com/AAxJSDX.png)

### <mark style="background: #BABD00;">Computers perform repetitive tasks, people solve problems.</mark>  

Many people worry that automation will put them out of a job.  

This is not the goal. There will never be a shortage of work in a successful company.  

Rather, people are freed up from mindless drudge-work to focus on higher value activities.  

This also has the benefit of improving quality, since humans are at their most error-prone when performing mindless tasks

### <mark style="background: #BABD00;">Relentlessly pursue continuous improvement:</mark>  

Continuous improvement, or kaizen in Japanese, is another key idea from the Lean movement.  

“Kaizen opportunities are infinite. Don’t think you have made things better than before and be at ease... This would be like the student who becomes proud because they bested their master two times out of three in fencing..... it is important to have the attitude in our daily work that just underneath one kaizen idea is yet another one” - Taiichi Ohno (Toyota Lean)  

Don’t treat transformation as a project to be embarked on and then completed so we can return to business as usual. Treats improvement work as an essential part of their daily work, and where nobody is satisfied with the status quo.

### <mark style="background: #BABD00;">The continuous improvement cycle:</mark>

![](https://i.imgur.com/dWTwwAC.png)

### <mark style="background: #BABD00;">Everyone is responsible:</mark>  

In high performing organizations, nothing is "somebody else’s problem"  

Developers are responsible for the quality and stability of the software they build. Operations teams are responsible for helping developers build quality in.  

Everyone works together to achieve the organizational level goals, rather than optimizing for what’s best for their team or department.

<mark style="background: #BABD00;">People make local optimizations that reduce the overall performance of the organization often because:</mark>  
- poor management systems such as annual budgeting cycles
- incentives that reward the wrong behaviours  
- rewarding developers for increasing their velocity or writing more code.  
- rewarding testers based on the number of bugs they find

<mark style="background: #BABD00;">Most people want to do the right thing:</mark>  
- However, they will adapt their behaviour based on how they are rewarded.  
- Therefore, it is very important to create fast feedback loops from the things that really matter:  
- how customers react to what we build for them, and the impact on our organization

### <mark style="background: #BABD00;">Continuous delivery rests on three foundations:</mark> 

Comprehensive configuration management  

Continuous integration (covered in previous session).  

Continuous testing.

### <mark style="background: #BABD00;">Comprehensive Configuration Management:</mark>

<mark style="background: #BABD00;">The Goals of Configuration Management.</mark>  
- <mark style="background: #BABD00;">Reproducibility:</mark> We should be able to provision any environment in a fully automated fashion, and know that any new environment reproduced from the same configuration is identical.  
- <mark style="background: #BABD00;">Traceability:</mark> We should be able to pick any environment and be able to determine quickly and precisely the versions of every dependency used to create that environment.  
- We also want to be able to compare previous versions of an environment and see what has changed between them.

### <mark style="background: #BABD00;">The Benefits of Configuration Management:</mark>  
- Disaster recovery  
- Auditability  
- Higher quality  
- Response to defects  
- Capacity management

<mark style="background: #BABD00;">Disaster recovery:</mark> When something goes wrong with one of our environments, for example a hardware failure or a security breach, we need to be able to reproduce that environment in a deterministic amount of time in order to be able to restore service  

<mark style="background: #BABD00;">Auditability</mark> (related to System Integrity): be able to show the path backwards from every deployment to the elements it came from, including their version.  

Comprehensive configuration management, combined with deployment pipelines, enable this.

<mark style="background: #BABD00;">Higher quality:</mark>  
- The software delivery process is often subject to long delays waiting for development, testing and production environments to be prepared.  
- When this can be done automatically from version control, we can get feedback on the impact of our changes much more rapidly, enabling us to build quality in to our software

<mark style="background: #BABD00;">Response to defects:</mark>  
- When we discover a critical defect, or a vulnerability in some component of our system, we want to get a new version of our software released as quickly as possible. 
- Many organizations have an emergency process for this type of change which goes faster by bypassing some of the testing and auditing.  
- This presents an especially serious dilemma in safety-critical systems.  
- Our goal should be to be able to use our normal release process for emergency fixes—which is precisely what continuous delivery enables, on the basis of comprehensive configuration management.

### <mark style="background: #BABD00;">Continuous Testing:</mark>

The key to building quality into our software is making sure we can get fast feedback on the impact of changes.  

Traditionally, extensive use was made of manual inspection of code changes and manual testing (normally done in a phase following "dev complete"). This approach has several limitations: 
- Manual regression testing takes a long time, is expensive, and creates a bottleneck prevents us releasing software more frequently.  
- Manual tests and inspections are not very reliable, since humans are notoriously poor at performing repetitive tasks.  
- Software evolves all the time, but the test document does not evolve to match

Our goal is to run many different types of tests—both manual and automated—continually throughout the delivery process

![](https://i.imgur.com/CykgCmJ.png)

Once we have continuous integration and test automation in place, we create a deployment pipeline (the key pattern in continuous delivery).  

In the deployment pipeline pattern, every change runs a build that:  
- creates packages that can be deployed to any environment and  
- runs unit tests (and possibly other tasks such as static analysis)  

giving feedback to developers in the space of a few minutes.  

Packages that pass this set of tests have more comprehensive automated acceptance tests run against them.

### <mark style="background: #BABD00;">Deployment Pipeline:</mark>

Once we have packages that pass all the automated tests, they are available for self-service deployment to other environments for activities such as exploratory testing, usability testing, and ultimately release.  

Complex products and services may have sophisticated deployment pipelines; a simple, linear pipeline is shown on the next slide

<mark style="background: #BABD00;">Sequence Diagram:</mark>
![](https://i.imgur.com/VDuDKkw.png)

<mark style="background: #BABD00;">Conceptual diagram:</mark>
<!--⚠️Imgur upload failed, check dev console-->
![[Pasted image 20241129135127.png]]

### <mark style="background: #BABD00;">Deployment Pipeline – Release Candidates:</mark> 

In the deployment pipeline, every change is effectively a release candidate.  

The job of the deployment pipeline is to catch known issues.  

If we can’t detect any known problems, we should feel comfortable releasing any packages that have gone through it.  

If we aren’t, or if we discover defects later, it means we need to improve our pipeline, perhaps adding or updating some tests.


### <mark style="background: #BABD00;">Deployment Pipeline – Parallelize the Activities.</mark>  

Our goal should be to find problems as soon as possible, and make the lead time from check-in to release as short as possible.  

Thus we want to parallelize the activities in the deployment pipeline, not have many stages executing in series.  

There is also a feedback process: if we discover bugs in exploratory testing, we should be looking to improve our automated tests.  

If we discover a defect in the acceptance tests, we should be looking to improve our unit tests (most of our defects should be discovered through unit testing).

### <mark style="background: #BABD00;">Canary Deployments – what is it?</mark>

A deployment strategy that gradually rolls out a new version to a subset of users.  
- Release to 5% of users  
- Monitor metrics and feedback  
- Expand to 25%, continue to monitor metrics and feedback  
- If all is well, then release to 100% of users.  

Allows monitoring for issues before a full-scale release..  

Inspired by the practice of using canaries in coal mines to detect danger early.  

More and more commonly used in Kubernetes, CI/CD and GCP, AWS and Azure pipelines.

### <mark style="background: #BABD00;">Canary Deployments: Benefits, Limitations and Best Practices</mark>

<mark style="background: #BABD00;">Benefits:</mark>  
- Reduces risk of widespread failure.  
- Enables real-world testing with minimal impact.  
- Improves confidence in releases 
- Early Feedback. Canary deployments shorten feedback loops on new features delivered to target environments.  

<mark style="background: #BABD00;">Limitations:</mark>  
- Added Complexity: Teams have two environments to maintain, as well as additional application code, services, and components.  
- Technical Challenges: Routing to subsets of users for new versions can be error-prone, time-consuming, and complex.  
- Less Control: The more software runs on the client side, the less amenable it is to canary deployments.  

<mark style="background: #BABD00;">Best Practices:</mark>  
- Use robust monitoring and alerting systems  
- Automate rollbacks for faster response to issues.  
- Communicate clearly with stakeholders.

### <mark style="background: #BABD00;">Blue Green Deployments vs Canary Deployments:</mark>

![](https://i.imgur.com/nIy8tpL.png)

### <mark style="background: #BABD00;">Implementing Continuous Delivery:</mark>

![](https://i.imgur.com/5XLj1GW.png)
