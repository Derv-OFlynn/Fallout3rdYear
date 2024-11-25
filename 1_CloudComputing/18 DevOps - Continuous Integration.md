### <mark style="background: #BABD00;">Continuous Integration:</mark>  
  
<mark style="background: #BABD00;">Continuous Integration (CI)</mark> is a development practice that requires different developers in a team to integrate code into a shared repository several times a day.  

Each check-in is then verified by an automated build, allowing teams to detect problems early.  

While automated testing is not strictly part of CI it is typically implied.  

By integrating regularly, you can detect errors quickly, and locate them more easily.

Every developer is expected to do a "smoke test" on the work they've done. They commit it to a private repo and integrate it to the main repo.

![](https://i.imgur.com/vTeG43e.png)

Build process should be no more than 10 mins. If it is lonfer, introduce a multi-stage build process.

### <mark style="background: #BABD00;">Productivity:</mark>

Because you’re integrating so frequently, there is significantly less back-tracking to discover where things went wrong, so you can spend more time building features.  

Continuous Integration is cheap relative to not integrating continuously is expensive.  

If you don’t follow a continuous approach, you’ll have longer periods between integrations. This makes it exponentially more difficult to find and fix problems.  

Such integration problems can easily knock a project off-schedule, or cause it to fail altogether.

### <mark style="background: #BABD00;">Benefits:</mark>  

Say goodbye to long and tense integrations.  

Increase visibility enabling greater communication.  

Catch issues early and nip them in the bud. CI doesn't get rid of bugs, but it does make them dramatically easier to find and remove.  

Spend less time debugging and more time adding features.  

Stop waiting to find out if your code’s going to work  

Reduce integration problems allowing you to deliver software more rapidly

![](https://i.imgur.com/IVXsSLO.png)

### <mark style="background: #BABD00;">Practices:</mark>  

Maintain a single source repository  

Automate the build.  

Make your build self-testing.  

Every commit should build on an integration machine.  

Keep the build fast. (10 mins or less).

Test in a clone of the production environment.  

Make it easy for anyone to get the latest executable version.

### <mark style="background: #BABD00;">How to do it:</mark>  

Developers check out code into their private workspaces.  

When done, commit the changes to the repository.  

The CI server monitors the repository and checks out changes when they occur.  

The CI server builds the system and runs unit and integration tests.  

The CI server releases deployable artefacts for testing.  

The CI server assigns a build label to the version of the code it just built.  

The CI server informs the team of the successful build.  

If the build or tests fail, the CI server alerts the team. The team fixes the issue at the earliest opportunity.  

Continue to continually integrate and test throughout the project

Semantic Versioning: Three numbers. Major (1st number) when you make incompatible API changes. Minor (2) version when you add functionality in a backward compatible manner. Patch (3rd number) is for bugfixes. e.g. 1.7.2
### <mark style="background: #BABD00;">Team Responsibilities:</mark>  

Check in frequently.  

Don’t check in broken code  

Don’t check in untested code.  

Don’t check in when the build is broken.  

Don’t go home after checking in until the system builds.  

Always maintain a correct consistent state.

![](https://i.imgur.com/jL7Vagp.png)

### <mark style="background: #BABD00;">Automate the Build:</mark>

What exactly do we mean by ‘Automate the build’?  

Getting the sources turned into a running system can often be a complicated process involving compilation, moving files around, loading schemas into the databases, and so on.  

However like most tasks in this part of software development it can be automated - and as a result should be automated. Asking people to type in strange commands or clicking through dialog boxes is a breeding ground for mistakes.  

A common mistake is not to include everything in the automated build.  

<mark style="background: #BABD00;">Rule of thumb:</mark> anyone should be able to bring in a virgin machine, check the sources out of the repository, issue a single command, and have a running system on their machine.

### <mark style="background: #BABD00;">Keep the Build Fast:</mark>

One primary goal of Continuous Integration is to provide  
rapid feedback.  

A CI activity whereby a build takes a long time is counter-productive.  

Most consider a build that takes an hour to be totally unreasonable. 10 minutes is reasonable.  

Recall - It's worth putting in concentrated effort to make it happen, because every minute you reduce off the build time is a minute saved for each developer every time they commit. Since CI demands frequent commits, this adds up to a lot of time.  

One approach to reducing overall build time is to use a multi-stage build process.

### <mark style="background: #BABD00;">CI/CD Pipeline:</mark>

![](https://i.imgur.com/Csy2L12.png)

### <mark style="background: #BABD00;">Acknowledgements:</mark>

The majority of the content in these slides were taken from the following online resources:  

DevOps Fundamentals - Introduction to DevOps by by Thiago Almeida and David Tesar. (Microsoft)  

http://www.itproguy.com/devops-practices  

https://www.thoughtworks.com/insights/blog/infrastructure-code-reason-smile  

https://www.red-gate.com/simple-talk/sysadmin/powershell/powershell-desired-state-configuration-the-basics/  

https://martinfowler.com/articles/continuousIntegration.html  

https://puppet.com/solutions/infrastructure-as-code  

https://www.thoughtworks.com/continuous-integration