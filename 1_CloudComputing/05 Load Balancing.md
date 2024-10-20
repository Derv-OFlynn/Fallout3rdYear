#CloudComputing
### <mark style="background: #BABD00;">Load Balancing:</mark>

All inbound traffic to a web role passes through a stateless load balancer, which distributes client requests among the role instances.  

Individual role instances do not have public IP addresses, and are not directly addressable from the Internet. (This is why you can’t ‘Ping’ the IP addresses).  

Web roles are stateless, so that any client request can be routed to any role instance.  

A Status-check event is raised every 15 seconds. This can be used to indicate if the role is ready to receive traffic, or is busy and should be taken out of the load balancer rotation.

![](https://i.imgur.com/heN0psc.png)

### <mark style="background: #BABD00;">Elasticity:</mark>

<mark style="background: #BABD00;">Elasticity – What is it?</mark> 
The degree to which a system is able to adapt to workload changes by provisioning and deprovisioning resources in an automated manner, such that at each point in time the available resources match the current demand as closely as possible.  

<mark style="background: #BABD00;">Elasticity is automated scalability.</mark>  
Scalability provides the ability to increase (or decrease) the amount of resources in scaling up (more powerful instances) or out (additional instances), which is usually done through manual intervention.  

Elasticity does the same but in an automated manner, independent from human interaction.

### <mark style="background: #BABD00;">Types of Auto Scaling:</mark>

![](https://i.imgur.com/q4Kkywn.png)

### <mark style="background: #BABD00;">Vertical Auto Scaling:</mark>  

Often referred to as scaling-up or scaling down.  

Requires that you modify the hardware (expand or reduce its capacity and performance).  

Or redeploy the solution using alternative hardware that has the appropriate capacity and performance.  
Vertical scaling is often a disruptive process that requires making the system temporarily unavailable while it is being redeployed .  

<mark style="background: #BABD00;">Not a common approach in the Cloud Industry!</mark>

### <mark style="background: #BABD00;">Horizontal Auto Scaling:</mark>  

Often referred to as scaling-in or scaling-out.  

Requires deploying the solution on additional or fewer resources, which are typically commodity resources rather than high-powered systems.  

The solution can continue running without interruption while these resources are provisioned.  

When the provisioning process is complete, copies of the elements that comprise the solution can be deployed on these additional resources and made available.  

If demand drops, the additional resources can be reclaimed after the elements using them have been shut down cleanly.  

<mark style="background: #BABD00;">The most common approach to implementing Elasticity in the Cloud.</mark>

### <mark style="background: #BABD00;">AWS Auto Scaling:</mark>

![](https://i.imgur.com/FegnUtZ.png)
