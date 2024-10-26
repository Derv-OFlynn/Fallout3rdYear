### <mark style="background: #BABD00;">Information Security: Terminology:</mark>

<mark style="background: #BABD00;">Information Security Goals: CIA Triad</mark>  
- Confidentiality, Integrity, and Availability  
- A security framework for logical and physical resources  

<mark style="background: #BABD00;">Authentication, Authorization, and Auditing (AAA):</mark> An Access security framework for distributed systems  

<mark style="background: #BABD00;">Defense-in-Depth:</mark> Provides multiple layers of defense  

<mark style="background: #BABD00;">Trusted Computing Base (TCB):</mark> Defines boundary between security-critical and non critical parts of an information system  

<mark style="background: #BABD00;">Encryption:</mark> Conversion of data into a form that cannot be used by unauthorised users

### <mark style="background: #BABD00;">Basic information security terminology, which will assist in understanding VDC and Cloud security include:</mark> 

<mark style="background: #BABD00;">CIA triad:</mark> A security framework for an information system has three primary goals: Confidentiality, Integrity, and Availability of physical and logical resources. This is commonly known as CIA triad.  

<mark style="background: #BABD00;">AAA:</mark> The security framework for an information system should provide authentication and authorisation capabilities. Auditing assesses the effectiveness of security mechanisms.  

<mark style="background: #BABD00;">Defense-in-Depth:</mark> It is a risk management strategy which provides multiple layers of defense against attacks.  

<mark style="background: #BABD00;">Trusted Computing Base (TCB):</mark> TCB of an information system is the set of all components that are critical to its security. Vulnerabilities occurring inside the TCB might jeopardise the security of the entire system. This way, TCB essentially defines a boundary for security-critical and non critical parts of an information system; for example, kernel services of an OS are more critical for its security than application level services. Therefore, kernel services are part of a TCB for an OS, whereas application level services need not be a part of it.  

<mark style="background: #BABD00;">Encryption:</mark> It is the conversion of data into a form that cannot be easily understood by unauthorized users. Decryption is the process of converting encrypted data back into its original form. Encryption is used to enforce confidentiality, privacy, and integrity.  

The following slides provide details on some of the above mentioned concepts.

### <mark style="background: #BABD00;">CIA Triad:</mark>

<mark style="background: #BABD00;">Confidentiality:</mark>  
- Provides required secrecy of information  
- Ensures that only authorized users have access to data (information)  

<mark style="background: #BABD00;">Integrity:</mark> Ensures that unauthorized changes to data are not allowed  

<mark style="background: #BABD00;">Availability:</mark> Ensures that authorized users have reliable and timely access to data

### <mark style="background: #BABD00;">Authentication, Authorisation and Auditing</mark>

<mark style="background: #BABD00;">Authentication:</mark>
- Is a process to ensure that a user’s credentials (for example identity) are genuine  
- Ensures that no illegitimate access is allowed  
- A special method for authentication is Multi-factor authentication  

<mark style="background: #BABD00;">Authorisation:</mark>  
- Is a process to give specific access rights to a user to resources  
- Defines the scope of the access rights of a user on a resource; for example, read-only access or read-write access  

<mark style="background: #BABD00;">Auditing:</mark> Is a process to evaluate the effectiveness of security enforcement mechanisms

In an information system security framework, authentication and authorization capabilities are required to ensure legitimate access to data.  

Authentication is a process to ensure that a user’s or asset’s credentials (for example identity) are genuine so that no illegitimate access to information is allowed. Multi-factor authentication is a special method for authentication, which considers multiple factors together for authenticating a  
user.  

Authorisation is a process to grant specific access rights to a user on resources. Authorisation defines the limits of the access rights of a user on a resource; for example, read-only access or read-write access on a file.  

Finally, auditing is a process to evaluate the effectiveness of security enforcement mechanisms.

<mark style="background: #BABD00;">Observability</mark> is the managing, monitoring and observing  your log to see if something malicious is happening.

### <mark style="background: #BABD00;">Multi-factor Authentication:</mark>

<mark style="background: #BABD00;">Considers multiple factors together for authentication</mark>  
- First factor: What does a user know? For example, a password 
- Second factor: What does a user have? For example, a secret key generated by a physical token, in possession of the user  
- Third factor: Who is the user? For example, a biometric signature  

Access is granted only when all the specified factors are validated

![](https://i.imgur.com/83gE9GQ.png)

Multi-factor authentication considers multiple factors before permission to access a resource is granted to the user. Typically the factors considered are:  
- <mark style="background: #BABD00;">First factor:</mark> What does a user know? For example, a password for a log on session will be what a user is required to know.  
- <mark style="background: #BABD00;">Second factor:</mark> What does a user have? For example, a user needs to provide a secret key, generated by a physical device (token), which is under the user’s possession.  
- <mark style="background: #BABD00;">Third factor:</mark> Who is the user? For example, a biometric signature of a user can be considered as an example of who a user is.  

Additional factors can also be considered, for example, “key phrases” unique to the user’s past activity.  

A multi-factor authentication scheme may consider any combination of these factors for authentication. User access is granted only when all the required factors are validated. 

For example, a two-factor authentication could be based upon the first and second factors discussed above and depicted in the diagram on this slide.

### <mark style="background: #BABD00;">Defense-in-Depth:</mark>

<mark style="background: #BABD00;">Defense-in-Depth (DID):</mark>  An information assurance strategy, whereby multiple security measures  
are used to reduce the risk of security threats if one component of the protection gets compromised.

DID is also known as a "layered approach“ to security  

DID gives an organization additional time to detect and respond to an attack. Reduces the scope of a security breach

![](https://i.imgur.com/o4s7aJZ.png)

1. <mark style="background: #BABD00;">Perimeter Security</mark> (Physical Security)  
2. <mark style="background: #BABD00;">Remote Access Controls</mark> (VPN, Authentication, etc.)  
3. <mark style="background: #BABD00;">Network Security</mark> (Firewall, DMZ, etc.)  
4. <mark style="background: #BABD00;">Compute Security</mark> (Hardening, Anti Virus, etc.)  
5. <mark style="background: #BABD00;">Storage Security</mark> (Encryption, Zoning, etc.)

Defense-in-depth represents the use of multiple security defenses to help mitigate the risk of security threats if one component of the defense is being compromised. An example could be an antivirus software installed on individual VM when there is already a virus protection on the firewalls within the same environment. Different security products from multiple vendors may be deployed to defend different potential vulnerable resources within the network.  

Defense-in-depth is an information assurance strategy in which multiple layers of defense are  placed throughout the system. For this reason, it is also known as a “layered approach to security”.  

Because there are multiple measures for security at different levels, defense-in-depth gives additional time to detect and respond to an attack. This reduces the scope of a security breach.  

However, the overall cost of deploying defense-in-depth is often higher, compared to single-layered security mechanisms.

### <mark style="background: #BABD00;">Trusted Computing Base (TCB):</mark>

<mark style="background: #BABD00;">Trusted Computing Base (TCB):</mark> It is the set of all those components that are critical to the security of the system.

Defines boundary for security-critical parts and non-critical parts of a system  

Vulnerabilities occurring inside the TCB might jeopardise the security of the entire system  

Is designed as a combination of hardware and software components  

Careful design and implementation of a system's TCB can significantly improve its overall security

An important design concept while designing a security framework for an information system is the concept of Trusted Computing Base (TCB). TCB of an information system is the set of all components that are critical to its security, in the sense that vulnerabilities occurring inside the TCB might jeopardise the security of the entire system.  
TCB is often the only part of the entire system which runs in a privileged mode, thus enhancing the inherent security of the system. TCB controls and authenticates access to the system resources and verifies system integrity. TCB is usually designed as a combination of hardware and software components. TCB essentially defines a boundary for security-critical and non critical parts of an information system. Careful design and implementation of a system's TCB is of great significance to its overall security.

### <mark style="background: #BABD00;">Encryption:</mark>

<mark style="background: #BABD00;">Encryption:</mark> It is the process of converting data to a form which cannot be used in any meaningful way without special knowledge.

Encryption is a key technique to provide confidentiality and integrity of data  

The unencrypted data is called cleartext (or plaintext) and encrypted data is called ciphertext  

The process of converting the encrypted data back to its original form is called decryption  
- Both encryption and decryption require keys (special knowledge)  
- Keys for encryption and decryption can be the same or different

Encryption is the process of converting data (information) to a form that cannot be used in any meaningful manner without special knowledge. Encryption is a key technique to enable the confidentiality and integrity of data. The non encrypted data, which is given to the encryption process as an input, is called plaintext (cleartext) and the encrypted data, which is an outcome of the encryption process, is called ciphertext. The process of converting the encrypted data back into its original form is called decryption.  

Encryption (and decryption) requires key(s) (special knowledge) or process to apply on data. When the keys for encryption and decryption are the same, it is known as symmetric encryption. When these keys are different (but related), it is known as asymmetric encryption. For data encryption, most often, symmetric encryption is used. Asymmetric encryption is most commonly used to secure separate end points of a connection, for example, Web browser and Web server (using https), VPN client and server, or for transferring a symmetric key.

### <mark style="background: #BABD00;">Security Concerns and Threats:</mark>

This lesson covers security concerns and threats in a VDC (Virtual Data Centre) and Cloud environment from Cloud Service Provider’s (CSP’s) and user’s perspectives.

Virtualisation-specific security concerns are common for all Cloud models  

In public Clouds, there are additional security concerns, which demand specific counter measures  
- Clients have less control to enforce security measures in public Clouds  
- Difficult for CSPs to meet the security needs of all the clients  
- Different clients may have different requirements

Security concerns, which arise specifically due to virtualisation, are common to all Cloud models.  

As compared to VDC or Private Clouds, in Public Clouds, there are additional security concerns which demand specific counter measures. This is because, in a VDC or a Private Cloud, a client has complete control over the resources and can enforce security policies.  

In Public (and hybrid) Clouds, however, clients usually do not have that much control over resources and therefore, enforcement of security mechanisms for a client is comparatively difficult.  

For Cloud Service Providers (CSPs) also, it is not easy to enforce all the security measures that meet the security needs of all the clients, because different clients may have different security demands based upon their objective of using the Cloud services. In public Clouds, there are additional security concerns, which demand special measures.  

From a security perspective, both Cloud users as well as service providers have several concerns and face multiple threats. Some of the concerns and threats are common to both of them. From a CSP perspective, majority of the concerns and threats are common to all Cloud-deployment models. Therefore, in cases where a security concern or threat is specific to a Cloud model (for example Public Cloud, it will be explicitly mentioned.

### <mark style="background: #BABD00;">Security Concerns and Threats:</mark>

<mark style="background: #BABD00;">EXAM NOTICE: THREATS AND CONCERNS ARE DIFFERENT. Also, know how to mitigate it. </mark>

<mark style="background: #BABD00;">Cloud Security Concerns:</mark>  
- Multitenancy  
- Velocity of attack  
- Information assurance  
- Data privacy and ownership  

<mark style="background: #BABD00;">Cloud Security Threats:</mark>  
- VM Theft and VM Escape  
- HyperJacking  
- Data leakage  
- Denial of Service (DoS) attack

Security concerns and threats in a Cloud environment can be classified for CSPs and Cloud users based upon whom that concern or threat affects more.  

For a CSP, the key security concerns are multitenancy and ‘velocity-of-attack’. Though these are also concerns for Cloud users, it is the CSP who needs to adopt suitable counter measures to address these concerns.  

Multitenancy refers to the fact that the Cloud infrastructure, by virtue of virtualization, enables multiple independent clients (tenants) to be serviced using same set of resources. This consequently increases the risks for data confidentiality and integrity.  

These risks are especially more severe in case of Public Cloud environment. This is because, in Public Cloud, services can be used by competing clients as compared to Private Clouds. Also, the number of Cloud users are much higher in Public Clouds.  

The ‘Velocity-of-attack’ in the Cloud refers to a situation where any existing security threat in the Cloud spreads more rapidly and has larger impact than that in the Classic Data Centre (CDC) environments.  

Information assurance, data privacy, and ownership are among the key Cloud security concerns for its users.  

Information assurance covers many related aspects of ensuring that data in a Cloud is “safe”. Data privacy and ownership concerns specifically relate to the risk of an unauthorized data disclosure.  

The key security threats for VDC and Cloud infrastructure include:  
- <mark style="background: #BABD00;">VM theft:</mark> It involves unauthorized copying or movement of a VM.  
- <mark style="background: #BABD00;">VM escape:</mark> Guest OS or an application running on it breaks out and starts interacting directly with the hypervisor.  
- <mark style="background: #BABD00;">HyperJacking:</mark> An attacker installs a rogue hypervisor or Virtual Machine Monitor (VMM) that can take complete control of the underlying server.  
- <mark style="background: #BABD00;">Data leakage:</mark> Refers to the fact that confidential data of a client stored on a third party Cloud is potentially vulnerable to unauthorized loss or manipulation. It is primarily a threat for a Cloud user.  
- <mark style="background: #BABD00;">Denial of Service:</mark> Denial of Service attacks prevent legal users of a system from accessing its services. In Cloud, it could occur when a malicious VM is installed on the same server and consumes all the server resources, thus preventing the other VMs from functioning properly.  

These Cloud security concerns and vulnerabilities will be discussed next.

### <mark style="background: #BABD00;">Security Concern: Multitenancy</mark>

<mark style="background: #BABD00;">Multitenancy is a key security concern in Cloud:</mark>  
- For Cloud Clients: Co-location of multiple VMs in a single server and sharing the same resources increases the attack surface 
- For CSPs: Enforcing uniform security controls and measures is difficult  

<mark style="background: #BABD00;">Mutual client isolation is a key measure against multitenancy-related concerns:</mark>  
- Isolation of VMs  
- Isolation of Data  
- Isolation of network communication

In spite of the benefits offered by multitenancy to a CSP, it is a major security concern for the Cloud clients.  

This is because Cloud infrastructure and services are, by nature, shared among multiple business entities, for example, multiple business units in an organisation or different companies. Co-location of multiple VMs in a single server and sharing the same resources increase the attack surface of vulnerability. This gives rise to a potential security concern for the Cloud users because it makes private data of one client vulnerable to theft by other competing clients who run applications using the same resources.  

There also exists a danger that in the absence of adequate security controls, a tenant application might disrupt operations of other tenants, for example, by launching DoS attacks. An already compromised VM might enable an attacker to compromise the security of other VMs (running on the same server) or of the hypervisor. A compromised guest OS in a VM can also impact other guest OSs in other VMs.  

For CSPs also, multitenancy makes it harder to enforce uniform security controls and counter measures for all the clients.  

Isolation of VMs, data, and network communication related to different clients is a key measure against multitenancy-related concerns. These measures will be discussed later in the module.  

<mark style="background: #BABD00;">Note:</mark> An attack surface refers to various access points/interfaces that an attacker can use to launch an attack; for example, the code within a compute system, which can be executed without requiring any authorisation.

### <mark style="background: #BABD00;">Security Concern: Velocity of Attack</mark>

<mark style="background: #BABD00;">Security threats amplify and spread quickly in a Cloud – known as “Velocity-of-Attack” (VOA) factor</mark>  
- Cloud infrastructure is comparatively larger  
- Similarity in the platforms/components employed by a CSP increases the speed at which an attack can spread  

<mark style="background: #BABD00;">Effects of high VOA</mark>  
- Potential loss due to an attack is comparatively higher  
- It is comparatively more difficult to mitigate the spread of the attack  

To counter the challenge of VOA, CSPs need to adopt more robust security enforcement mechanisms; for example, defense-in-depth

Clouds harness the power of relatively large compute, storage, and network infrastructure, compared to individual data centres. A Public Cloud might consist of thousands of physical servers, network connectivity across large geographic boundaries, and very high capacity storage arrays.  

There also exists homogeneity (similarity) in the platforms and components (for example, the virtualisation software, guest OS) employed by the Cloud service providers.  

Owing to these factors, security threats are amplified more and spread quickly, which is considered as the “velocity of attack” factor in the Cloud. Owing to this factor, security threats can cause much higher levels of losses to the Cloud service providers and to its clients, compared to those in a CDC.  

Mitigating the spread of a threat in a Cloud is also comparatively more difficult than in a CDC environment.  

Because of the potentially high velocity-of-attack, CSPs need to adopt and deploy stronger and robust security enforcement and containment mechanisms, for example, defense-in-depth. Cloud users also need to carefully assess the security services deployed by a CSP before moving operations to the Cloud.

### <mark style="background: #BABD00;">Security Concern: Information Assurance and Data Ownership</mark>

<mark style="background: #BABD00;">Information assurance concerns for Cloud users involves</mark>  
- CIA Triad  
- User Authenticity  
- Authorised use (can operate only with legitimate rights and scope)  

<mark style="background: #BABD00;">Data ownership concerns for Cloud clients:</mark>  
- In Cloud, data belonging to a client is maintained by a CSP, who has access to the data, but is not the legitimate owner of it  
- This raises concern of potential unauthorized data access and misuse  
- Data should be protected using encryption and access control mechanisms

<mark style="background: #BABD00;">The core information assurance concerns for Cloud users include:</mark>  
- <mark style="background: #BABD00;">CIA:</mark> Ensuring confidentiality, integrity, and availability of data in the Cloud.  
- <mark style="background: #BABD00;">Authenticity:</mark> Ensuring that all the users operating on the Cloud are genuine (i.e., their identities have not been fabricated).  
- <mark style="background: #BABD00;">Authorised use:</mark> Ensuring that the Cloud users (clients and CSP administrators) can operate only with legitimate rights and scope.  

Ownership of data is yet another concern for Cloud clients. Ownership issues arise in public Clouds because data belonging to a client is maintained by a CSP who has access to the data but is not the legitimate owner of it. This raises concern of potential misuse of the data for the users because they do not have much control over the data handled by CSP. Data should be protected using encryption. The access control mechanisms for Clouds must be designed to ensure ownership based access rights.

### <mark style="background: #BABD00;">Security Concern: Data Privacy:</mark>

Potential for unauthorised disclosure of private data of a Cloud client  

<mark style="background: #BABD00;">Private data may include:</mark>  
- Individual identity of the client  
- Details of the services requested by the client  
- Proprietary data of the client  

A CSP needs to ensure that private data of its clients is protected from unauthorized disclosure  

Both collection and dissemination of the private data requires protection  

A CSP needs to deploy data privacy mechanisms, which are compliant with the regional legal regulations

Data Privacy is a major concern in Cloud. A CSP needs to ensure that Private and Personally  

Identifiable Information (PII) about its clients is legally protected from any unauthorized disclosure. Private data may include:  
- Individual identity of a Cloud user  
- Details of the services requested by a client  
- Proprietary data of the client  

A CSP needs to ensure that private data of its clients is protected from unauthorized disclosure. Both collection and dissemination of the private data needs protection from any possible unauthorised disclosure, in particular, as per the regional legal requirements.

### <mark style="background: #BABD00;">Security Threat: VM Vulnerabilities</mark>

<mark style="background: #BABD00;">VMs are vulnerable to attack when they are running and when they are powered-off:</mark>  
- A powered-off VM is still available as an image file, which is susceptible to malware infections 
- Unprotected VM migration is vulnerable to network attacks  
- Encryption of VM image files is required as a protection measure when it is powered-off or during its migration  

<mark style="background: #BABD00;">VM templates are also vulnerable to attacks</mark>  
- When new unauthorized VMs are created from a template  
- When a template is modified to infect the VMs  
- To protect, VM templates must be kept encrypted and access should be restricted to privileged users (administrators)

VM templates are vulnerable when they are running and when they are powered-off.  

A powered-off VM is still available as a VM image file that is susceptible to malware infections and patching. If adequate security measures are not deployed, VM migration could expose the migrating VM to various network attacks, for example, eavesdropping and modification.  

VM templates are also vulnerable to attacks; for example, by creating new unauthorized VMs from a template or modifying the templates to infect the VMs that will be provisioned using those templates.  

Protecting VMs from these vulnerabilities require encryption of the VM image files when they are powered off, or while they are migrated. This is beyond the well-defined isolation of VMs, which is generally performed at the hypervisor level. Also, access to the VM templates should be restricted to a limited group of privileged users.

### <mark style="background: #BABD00;">Security Threat: VM Theft:</mark>

<mark style="background: #BABD00;">VM Theft:</mark>  A vulnerability that enables an attacker to copy or move a VM in an unauthorised manner.

Is a result of inadequate controls on VM files allowing unauthorised copies or move operations  

Copy and Move restrictions are essential to safeguard against VM theft  
- These restrictions bind a VM to a specific physical machine  
- A VM with copy and move restriction cannot run on a hypervisor installed on any other server 
- These restrictions use a combination of virtualisation management and storage management services for effective enforcement  
- Limit applying such restrictions to critical/sensitive VMs only

VM theft enables an attacker to copy and/or move a VM in an unauthorised manner. VM theft is a result of inadequate controls on VM files allowing their unauthorised copy or movement. VM theft can cause a very high degree of loss to a Cloud client if its files and data are sensitive in nature.  

Copy and Move restrictions are essential to safeguard against VM theft. Such restrictions effectively bind a VM to a specific (secure) physical machine so that even if there is a forceful copy of the VM, it will not operate on any other machine. A VM with copy and move restrictions cannot run on a hypervisor installed on any other machine. These restrictions use a combination of virtualisation management and storage management services for their effective enforcement.  

Even though these restrictions are essential to safeguard against VM theft, they, on the other hand, might limit the benefit of load balancing of VMs across physical servers. Therefore, it is advisable that copy and move restrictions be applied in a limited way, especially only on those VMs, which are considered security critical/sensitive or are relatively more vulnerable for theft.  

Apart from VM theft, another threat on the VM level is known as ‘VM escape’. Normally, virtual machines are encapsulated and isolated from each other. There is no straightforward way for a guest OS and the applications running on it to break out of the virtual machine boundary and directly interact with the parent hypervisor.  

The process of breaking out and interacting with the hypervisor is called a VM escape. Since the hypervisor controls the execution of all VMs, due to VM escape, an attacker can gain control over every other VM running on it by bypassing security controls that are placed on those VMs.

### <mark style="background: #BABD00;">Security Threat: HyperJacking:</mark>

<mark style="background: #BABD00;">Hyperjacking:</mark>  It enables an attacker to install a rogue hypervisor or Virtual Machine Monitor (VMM) that can take control of the underlying server resources

An attacker can run unauthorized applications on a guest OS without the OS realizing it  

An attacker could control the interaction between the VMs and the underlying server  

Regular security measures are ineffective against hyperjacking  

<mark style="background: #BABD00;">Measures against hyperjacking include:</mark>  
- Hardware-assisted secure launching of the hypervisor  
- Scanning hardware-level details to assess the integrity of the hypervisor and locating the presence of the rogue hypervisor

Hyperjacking is a rootkit level vulnerability that enables an attacker to install a rogue hypervisor or virtual machine monitor that can take complete control of the underlying physical server.  

A rootkit is a malicious program which is installed before an hypervisor or VMM is fully booted on a physical server. This way, a rootkit runs with privileged access and remains invisible to the administrators. After a rootkit is installed, it allows an attacker to mask the ongoing intrusion and maintain privileged access to the physical server by circumventing normal authentication and authorisation mechanisms employed by an OS.  

Using such rogue hypervisor, an attacker can run unauthorised applications on a guest OS without that OS realizing the presence of such an application. With hyperjacking, an attacker can control the interaction between the VMs and the underlying physical machine.  

Regular security measures are ineffective against this rough hypervisor because:  
- Guest OS would remain unaware of the fact that the underlying server has been attacked and  
- The antivirus and firewall applications cannot detect such rogue hypervisor because they are installed over the server itself  

<mark style="background: #BABD00;">Measures against hyperjacking include:</mark>  
- Hardware-assisted secure launching of the hypervisor so that rootkit level malicious programs cannot launch. This involves designing and using a TCB so that the hypervisor gets support at the hardware level itself  
- Scanning the hardware-level details to assess the integrity of the hypervisor and locating the presence of rogue hypervisor. This scanning may include checking the state of the memory and registers in the CPU.

### <mark style="background: #BABD00;">Security Threat: Data Leakage:</mark>

Confidential data stored on a third party Cloud is potentially vulnerable to unauthorized access or manipulation  
- Attacks on service provider’s control systems (for example passwords lists) could make all the clients’ data vulnerable  
- Cloud users must evaluate end-to-end data protection measures by all the concerned parties who have any level of access on the data  

<mark style="background: #BABD00;">Side Channel Attacks (SCA) can be used for data leakage in Cloud:</mark>  
- An SCA extracts information by monitoring indirect activities; for example cache data, keystroke activity, etc.  

<mark style="background: #BABD00;">Cross-VM SCA:</mark>  
- Could reveal information of a client to another malicious client that runs its VMs on the same server  
- Protection against cross VM SCA requires placing only those clients that have no conflicts with one another on the same server

Confidential data stored on a third party Cloud is potentially vulnerable to unauthorized loss or manipulation.  

Third party Cloud refers to the Cloud that is used by a service provider to provide services to its end clients. In such a case, the service provider might not have total control over the Cloud to ensure the confidentiality and integrity of clients’ data.  

An attack on the service provider’s control systems (for example, password lists) could make all of the clients’ data vulnerable and expose the data to malicious uses.  

To mitigate the risk of such data theft, cloud users must evaluate the end-to-end data protection measures adopted by all the concerned parties that have any level of access on their data.  

“Side Channel Attacks” (SCA) can also be used to check data leakage in Cloud.  An SCA extracts information by monitoring indirect activity, for example, keystroke activity, cache data, etc.  

A cross VM SCA involves one VM being used to launch an SCA on another VM running on the same server. A cross VM SCA could reveal information on a client’s critical business activity to a malicious client that runs its VMs on the same server. Protection against such cross VM SCA requires a placement policy that permits clients to install only non-conflicting VMS on the same server. This will, however, reduce resource optimization that virtualization technology offers. It could also add extra service cost to the Cloud clients who demand such privileged services.

### <mark style="background: #BABD00;">Security Threat: Denial of Service Attacks:</mark>

<mark style="background: #BABD00;">Denial of Service (DoS):</mark> It is an attempt to prevent legitimate users from accessing a resource or service.

DoS attacks might affect software applications and network components  

<mark style="background: #BABD00;">A DoS attack involves:</mark>  
- Exhausting resources, for example, network bandwidth or CPU cycles  
- Exploiting weaknesses in communication protocols, for example, resetting of TCP sessions, corrupting domain name server’s cache  

A malicious client VM might be used to launch a DoS attack against the hypervisor or other VMs running on the same hypervisor  

As a protective measure, resource consumption of a VM needs to be restricted

A Denial of Service (DoS) attack is an attempt to make resources or services of an information system unavailable to its authorized users.  

A DoS attack prevents legitimate users from accessing a resource or service. DoS attacks could be targeted against software applications (example OS) and network components including routers or servers.  

Often a DoS attack involves either one or a combination of the following:  
- Attack aims to exhaust computing resources, for example, network bandwidth and CPU cycles. An attack may involve massive quantities of data sent to the target with the intention of consuming bandwidth/processing resources.  
- Attack involves exploiting weaknesses in a protocol to target network resources; for example, resetting of TCP sessions, IP address spoofing, or corrupting DNS server cache.  

A Distributed DoS (DDoS) attack is a special type of DoS attack in which several systems launch coordinated DoS attack on their target(s), thereby causing denial of service to the users of the targeted system(s). In a DDoS attack, the main attacker is able to multiply the effectiveness of the DoS attack by harnessing the resources of multiple collaborating systems. These collaborating systems serve as attack platforms. Typically a DDoS master program is installed on one compute system using a stolen account. Then, at a designated time, the master program communicates to any number of "agent" programs installed on computers anywhere on the network. When the agents receive the command, they initiate the attack.  

In a virtualised environment, a rough VM could be used to launch DoS attack against the hypervisor or other VMs running on the same hypervisor. Such a rough VM could use the internal virtual network for launching the DoS attacks. To protect against such VM based DoS attacks, the resource consumption of a VM should be restricted to specific limits.

### <mark style="background: #BABD00;">Security Mechanisms:</mark>

<mark style="background: #BABD00;">Topics covered in this lesson:</mark>  
- Security at compute level, including securing server, hypervisor, VM, guest OS, and applications  
- Security at network and storage levels, including virtual  firewall, demilitarized zone, and data shredding  
- Intrusion detection in VDC and Cloud  
- Physical Security of the premises  
- Access Control and Identity management services in Cloud

This lesson covers Cloud infrastructure security mechanisms at the compute, network, and storage levels. Under compute level security, the lesson discusses security for server, hypervisor, VM, guest OS, and applications. Next, security at the network level discusses virtual firewall, demilitarized zone, and intrusion detection. Also covered are aspects related to storage security, including securing data-at-rest and data shredding. Next, the lesson discusses measures for physical security of the premises. Finally, the lesson discusses access control mechanisms, including role based access control and identity management techniques such as one-time password, identity federation, and OpenID.

### <mark style="background: #BABD00;">Security at Compute Level:</mark>

Securing a compute system includes:  
- Securing physical server  
- Securing hypervisor  
- Securing VMs  
	- VM Isolation  
	- VM Hardening 
	
- Security at guest OS level  
	- Guest OS Hardening  
	
- Security at application level  
	- Application Hardening

Securing a compute infrastructure includes enforcing security of the physical server, hypervisor, VM, and guest OS.  

Security at the hypervisor level primarily aims at securing hypervisor from the rootkits and malware based attacks and protection of the hypervisor management system. 

VM isolation and hardening are two key techniques for securing VMs. Security at the guest OS level uses sandboxing and hardening as two key methods. Application hardening is used to reduce vulnerability of the applications from getting exploited by malicious attackers. All these security methods are explained in the following slides.

### <mark style="background: #BABD00;">Physical Server Security: Considerations:</mark>

<mark style="background: #BABD00;">Identifying physical server application details including:</mark>  
- Whether server will be used for specific applications or for general purpose  
- The network services provided on the server  
- Users and/or user groups who can operate the server and their access privileges  

<mark style="background: #BABD00;">Deciding protection measures:</mark>  
- Determining authentication and authorization mechanisms  
- Disabling unused hardware such as NICs, USB ports, or drives 
- Physical security

Server security considerations include identifying server application details such as:  
- Deciding whether the server will be used for specific applications (for example backup applications) or for general purpose.  
- Identifying the network services to be provided on server; for example, LAN connection, wireless connection, etc.  
- Identifying users and/or user groups who will be given access rights on the server. This also includes determining their specific access privileges.  

Based upon these details, suitable protection measures need to be decided including the following:  
- Determine user authentication and authorization mechanisms.  
- If the server has unused hardware components such as NICs, USB ports, or drives, they should be removed or disabled. This should also be done in the VM (template).  
- Adequate physical security protection including safety of the premises where the server will be housed.

### <mark style="background: #BABD00;">Hypervisor Security:</mark>

Attacks on the hypervisor impact all the VMs running on it - a single point of security failure  

<mark style="background: #BABD00;">Security measures:</mark>  
- Install hypervisor updates  
- Harden VMs to prevent attacks  

Protection of the hypervisor management system ss critical because an insecure management system can  
- Make existing VMs vulnerable for attacks  
- Enable creation of new malicious VMs  

<mark style="background: #BABD00;">Can be achieved by:</mark>  
- Configuring strong security on the firewall between the management system and the network  
- Providing direct access only to administrators to management server  
- Disable access to management console to prevent unauthorised access

Hypervisor in a virtualized environment presents a single point of security failure for all the VMs running on it. A single breach of the hypervisor places all the guest OSs on these VMs at high risk.  

Rootkits and malware installed below the OS make detection difficult for the antivirus software installed on the guest OS.  

To protect against attacks, security-critical hypervisor updates should be installed at the earliest possible and the VMs hosted on it should be hardened (VM hardening measures are discussed next). Hypervisor services like clipboard, if not used, should be disabled.  

The hypervisor management system must be protected. Malicious attacks and infiltration to the management system can impact all the existing VMs and allow attackers to create new VMs.  

Access to the management system should be restricted only to authorized administrators. Levels of access should be restricted to selected administrators. Furthermore, there must be a separate firewall with strong security installed between the management system and the rest of the network. Yet another measure is to disable access to the management console to prevent unauthorised access.

### <mark style="background: #BABD00;">VM Security Isolation and Hardening:</mark>

<mark style="background: #BABD00;">VM isolation</mark> helps prevent a compromised guest OS and applications running on it from impacting other VMs  

<mark style="background: #BABD00;">VM Hardening:</mark> Hardening is a process of changing the default configuration in order to achieve greater security  

<mark style="background: #BABD00;">Considerations:</mark>  
- Use VM templates to provision new VMs  
- Limit the resources that VM can consume to  prevent DoS attacks  
- Disable unused functions and devices on VM  
- Use a directory service for authentication  
- Perform vulnerability scanning and penetration testing of the guest OS

VM isolation is a key measure that helps in preventing a compromised guest OS from impacting other guest OSs. VM isolation is implemented at the hypervisor level.  

Apart from isolation, VMs should be hardened against security threats. Hardening is a process of changing the default configuration in order to achieve greater security. Some of the key measures for hardening a VM (especially for a VDC or private Cloud environment) include the following:  
- Use VM templates to deploy VMs. When using templates, harden the VM image so that all the deployed VMs have a known security baseline. VM templates should be created with up-to-date VM patches and security updates.  
- In order to avoid DoS attacks, the VM management software should limit the VM’s resources so that a single VM is not allowed to consume all of the server’s resources. 
- Increase in the number of services, ports, and applications running on the VM also increases the area of attack surface. Therefore, unneeded functions and unused devices should be disabled.  
- Configure access permissions for the selected group of administrators. Avoid account sharing by groups of users and strictly control root privileges. Employ directory based authentication to ensure the genuineness of credentials.  
- Take VM backups on a regular basis and schedule point-in-time snapshots to restore a VM to a safe state, in case of an attack.  
- Perform vulnerability scanning of the guest OS regularly to identify existing vulnerabilities. Perform a penetration test to determine the feasibility of an attack and the extent of business impact of the attack. Note that in Public Clouds, usually, penetration tests originating from outside the CSP network are forbidden by the CSP. Therefore, a Cloud user should rely upon the CSP to perform these tests.

![](https://i.imgur.com/ObANoSi.png)

### <mark style="background: #BABD00;">Guest OS and Application Security:</mark>

Guest OS hardening measures include:  
- Deleting unused files and applying the latest patches  
- Applying hardening checklists available for specific OSs 
- Installing the guest OS in TCB mode if the VM is to be used for critical applications  
- Need support from hypervisor in configuring (trusted) virtual hardware component for TCB  

Application hardening measures include disallowing a vulnerable application from  
- Launching any (untrusted) executable file  
- Creating or modifying executable files  
- Modifying sensitive areas of the guest OS, for example, MS Windows registry  

Sandboxing is another important measure for guest OS and application security

Apart from the measures to secure a hypervisor and VMs, VDC and Cloud environment also require further measures on the guest OS and application levels. Hardening is one such important measure which can effectively safeguard guest OS and the applications running on it.  

OS hardening, for example, may involve actions such as configuring system and network components, deleting unused files, and applying the latest patches. There are hardening checklists available for major OSs which administrators should follow to harden the guest OSs deployed in VDC or Cloud. In cases where a VM is to be used for business critical applications, the guest OS should be installed in the TCB mode – an option available with many OSs. Such TCB mode installation, however, requires hypervisor support for configuring trusted virtual hardware components (for example virtual CPU).  

Application hardening helps to prevent exploitation of vulnerabilities in software applications that have not been patched so far. The key steps for hardening a vulnerable application include:  
- <mark style="background: #BABD00;">Disallowing the application from spawning executable files:</mark> One of the methods used by attackers is to make a vulnerable application into spawning executable files of their choice. Therefore, an important action for hardening the application is to disallow it from launching other executables, except those that are trusted.  
- <mark style="background: #BABD00;">Disallowing the application from creating or modifying executable files</mark>: Another technique, which is used by attackers, is to convert the vulnerable application into modifying or creating executable files of their choice in order to insert the malicious code into the system. The malicious code may eventually be executed and activated. Therefore, it is critical that applications are not allowed to modify or create any executable file when they are running.  
- <mark style="background: #BABD00;">Disallowing the application from modifying sensitive areas</mark>: It involves disallowing the application from modifying sensitive areas of the guest OS, for example, registry keys in the Windows OS.

### <mark style="background: #BABD00;">Security at Network Level: Virtual Firewall:</mark>

Securing VM-to-VM traffic running on a server is difficult in a VDC environment:  
- Virtual switches could be invisible to administrators (network and system)  
- Traffic may never leave the server, so it cannot be detected and intercepted  

Virtual Firewall (VF) is a firewall service running on the hypervisor

![](https://i.imgur.com/ja57Gus.png)

A firewall is a security technology designed to permit or deny network transmissions based upon a set of rules. A firewall is implemented on a compute level and limits access between networks and/or systems in accordance with a specific security policy. A firewall is used to protect networks from unauthorised access while permitting only legitimate communications.

In a VDC and Cloud infrastructure, a firewall can also be used to protect hypervisors and VMs; for example, if remote administration is enabled on a hypervisor, access to all the remote administration interfaces should be restricted by a firewall.  

Securing the VM-to-VM traffic running on a server is a key security problem in a VDC environment. Securing this virtual network is a considerable challenge because virtual switches could be invisible to network and/or system administrators, who usually enforce security at the network level.  

Because the virtual network traffic may never leave the server, security administrators cannot observe VM-to-VM traffic, cannot intercept it, and so, cannot know what that traffic is for. Thus, logging of the VM-to-VM network activity within a single server and verification of virtual machine access for regulatory compliance purposes is relatively difficult. Inappropriate use of virtual network resources and bandwidth consumption in VM-to-VM are difficult to monitor or rectify. Therefore, a firewall service, which can be used to monitor and control VM-to-VM traffic, is critically required. It is provided by a Virtual Firewall (VF), which is a firewall service running entirely on the hypervisor. VF provides the usual packet filtering and monitoring of the VM-to-VM traffic. VF gives visibility and control over VM traffic and enforces policies at the VM level.

### <mark style="background: #BABD00;">Security at Network Level: Demilitarised Zone:</mark>

<mark style="background: #BABD00;">Demilitarized Zone (DMZ):</mark> It is a physical or logical (sub)network that limits the exposure of the nodes in the internal network from external networks.

Adds additional layer of security against external attacks  
- An attacker has access only to the DMZ, rather than any other part of the network  
- For practical purposes ,services provided to users on the external networks can be placed in the DMZ  

A virtualised DMZ is a DMZ established in a virtualized environment using virtual network components.

![](https://i.imgur.com/eqA54tN.png)


<mark style="background: #BABD00;">PORT KNOCKING:</mark> Instead of allowing an external user to access an application on a specific port, have a number of ports they must request in a specific order in order to be authenticated. This is also audited.

### <mark style="background: #BABD00;">Securing at Network level:</mark>

<mark style="background: #BABD00;">Data-in-flight:</mark>  
- Data which is being transferred over a network i.e., “moving”  

<mark style="background: #BABD00;">Encryption of Data-in-flight:</mark>  
- Provides confidentiality and integrity  
- Is a key measure against “sniffing” attacks

![](https://i.imgur.com/Kv4f5mZ.png)

Data-in-flight refers to the data transferred over a network, and means that the data is “moving”.  

Encryption of data-in-flight is the key method for providing confidentiality and integrity services. Encryption makes the data indecipherable to an unauthorised user who otherwise may have access to the (encrypted) data. Encryption is indeed a key security measure against “sniffing” attacks. In a sniffing attack, a non recipient malicious device/user accesses the data transmitted over the network.  

Methods used for encrypting data-in-flight include:  
- <mark style="background: #BABD00;">Application-level encryption:</mark> Encryption is applied at the application level where the data is generated. Encrypting at the application level protects data against unauthorized access; for example, Transport Layer Security (TLS) protocol allows client/server applications to enforce encryption service.  
- <mark style="background: #BABD00;">Network-level encryption:</mark> Encryption is applied at the network layer; for example, IPSec, which can be used to encrypt and authenticate each IP packet transmitted over an IP network. The benefit of a network level encryption is that it is independent of the underlying guest OS.

### <mark style="background: #BABD00;">Storage Security in Cloud:</mark>

Major threats to storage system in a VDC and Cloud arise due to compromises at compute, network, and/or physical security levels  

Adequate security at compute and network levels is essential for storage security  

Storage Area Networks(SAN) have their unique vulnerabilities, for example, fabric access to an unauthorized device, WWN spoofing, etc.  

<mark style="background: #BABD00;">WWN Spoofing:</mark>  
- World Wide Name Spoofing  
- It is the way of bypassing authorisation methods in a SAN

Major threats to storage system in a VDC and Cloud environment arise due to compromises at compute, network, and/or physical security levels. This is because an access to storage systems needs to be made by using compute and network infrastructure. Therefore, adequate security measures need to be in place at compute and network levels to ensure storage security. Storage Area Networks (SAN) have their own unique vulnerabilities which can be used to compromise their integrity. These include unauthorized device gaining fabric connection, DoS attack, WWN spoofing which would enable a device to masquerade as a different entity, zoning bypass, etc.  

Security mechanisms that might help to protect storage includes:  
- Access control methods to regulate which users and processes access the data on the storage systems.  
- Zoning and LUN masking  
- Encryption of data-at-rest (on the storage system) and data-in-transit. Data encryption should also include encrypting backups and storing encryption keys separately from the data.  
- WWPN and WWNN LUN masking for restricting access to the storage arrays in a SAN.  
- Data shredding, which removes the traces of the deleted data. It may be performed by both CSP and also by the client.  
- Backup and recovery in case of loss of data.  

Apart from these mechanisms, physical isolation of storage devices from the other hardware and also an isolation of storage traffic from other types of traffic using VLANs and FC zoning would help in protecting storage.  

Moreover, security protection is required for the storage utilised by the hypervisor for VMs, for example, a CFS supporting multiple VMs within a cluster. This may include using separate LUNs for VM components and for VM data and segregating VM traffic from hypervisor storage and management traffic.

### <mark style="background: #BABD00;">Securing Data-at-Rest:</mark>

<mark style="background: #BABD00;">Data-at-rest:</mark> Data which is not being transferred over a  
network  

<mark style="background: #BABD00;">Encryption of Data-at-rest:</mark> 
- Provides confidentiality and integrity services  
- Reduces legal liabilities of a CSP due to an unauthorised disclosure of data on its Cloud  

Full disk encryption is a key method to encrypt data-at-rest residing on a disk

Data-at-rest refers to the data which is not being transferred over a network i.e., is “not moving”. It includes data that resides in databases, file systems, flash drives, memory, networked storage, etc.  

Encryption of Data-at-rest is the key method for providing confidentiality and integrity. Encryption makes the data indecipherable to unauthorized users. Encryption also reduces legal liabilities of a CSP due to an unauthorized disclosure of data on its Cloud because even if the encrypted data becomes accessible to an unauthorised user, it cannot be used in any meaningful way.  

Full disk encryption is the key method used for encrypting data-at-rest residing on a disk. Full disk encryption employs software application or built-in hardware capability to encrypt every bit of data that goes on a disk or disk volume. Disk encryption thus prevents unauthorized access to data storage. For additional security, it can be used in conjunction with file system encryption. Full disk encryption may use either a single key for encrypting the complete disk or different keys for  
encrypting different partitions.

### <mark style="background: #BABD00;">Data Shredding:</mark>

Data which is deleted by a Cloud client or a process, but which leaves traces on the system, can be a potential source of attacks  
- Traces of deleted VMs can provide vital information to an attacker  
- Partially recoverable “deleted data” may reveal client details  

Data shredding permanently removes all the traces of the deleted data and is a critical feature for data security in a Cloud infrastructure  

<mark style="background: #BABD00;">Traces of the deleted data include:</mark>  
- Logs of VM or application executions  
- Logs of old files, folders, and other resources  
- Logs of data communication

Unlike data stored in a privately controlled storage or in a CDC, data and information in a Cloud remain vulnerable even if deleted by the client or a process. This is because this data and information may still have recoverable traces about it on the system, and therefore, can be a potential source of attack. For example, traces of deleted VMs can provide vital information to an attacker about their clients. Partially recoverable “deleted data” from a Cloud storage may also reveal client details.  

Data shredding is therefore a critical measure for data security in a Cloud infrastructure. A data which is shredded cannot be recovered any more. Data shredding removes all the traces of the deleted data including:  
- Logs of deleted VMs including its configuration files and application executions  
- Logs of old files, folders, and other resources  
- Logs of data communication involving deleted VMs

### <mark style="background: #BABD00;">Physical Security in VDC and Cloud:</mark>

<mark style="background: #BABD00;">Restricted Port Access:</mark>  
- Leave unused ports in disabled state  
- Bind specific devices to designated ports  

<mark style="background: #BABD00;">Other types:</mark>
- CCTV based video surveillance  
- 24/7/365 onsite guarded security  
- Biometric authentication based physical access

Cloud customers essentially lose control over physical security when they move to the Cloud, because the actual servers can be anywhere the provider decides to put them. Since physical Cloud infrastructure supports many Cloud clients together, its security is very critical both for the CSP as well as its clients. Policies, processes, and procedures are critical elements of successful physical security that can protect the equipment and data housed in the hosting centre.  

Typical security measures that must be in place for securing physical Cloud infrastructure include:  
- Leaving a port in unconfigured or disabled state so that unknown devices or components cannot connect to the infrastructure. Additionally, bind specific devices to designated ports.  
- Apply MAC/WWPN binding and VLAN restrictions to physical Ethernet switches.  
- 24/7/365 onsite security for the premise where the Cloud physical infrastructure is hosted  
- Biometric authentication based access to the premises  
- Closed circuit TV cameras to monitor activity throughout the facility

### <mark style="background: #BABD00;">Role Based Access Control:</mark>

Resource access (permissions) is given to subjects (users and processes) based upon their roles  
- Role may represent a job function  
- Permissions are associated with the roles  
- Subjects acquire permissions to perform operations on resources based upon the roles assigned to them  

Role Based Access Control (RBAC) can be enabled for Cloud clients by importing user groups using directory services of the client organisation  

CSP may use RBAC to control an administrative access to the hypervisor management system (console)

In a Role Based Access Control (RBAC) model, resource access rights (permissions) are given to subjects (users and processes) based upon their roles. A role may represent a job function, for example, an administrator. Permissions are associated with the roles and subjects are not given any direct permissions. Subjects acquire permissions to perform operations on resources based upon the roles assigned to them.  

For RBAC, users need to be grouped together into roles. As an example, a set of IT administrators can be given permissions to start, stop, and delete VMs that are running in the Cloud. However, there could be a specific subset of production servers that even the IT administrators are not allowed to control.  

To handle sensitive data and compliance requirements, a Cloud needs RBAC capabilities. To achieve this, user groups can be imported using LDAP based Directory Services of the client organization for client installations in Cloud. CSPs may also use RBAC to control administrative access to the hypervisor management system (console).

### <mark style="background: #BABD00;">Identity Management (IM) in Cloud:</mark>

<mark style="background: #BABD00;">One-time passwords:</mark>  
- Every new access request requires new password  
- A measure against “password compromises”  

<mark style="background: #BABD00;">Federated Identity Management is provided as a service on Cloud:</mark>  
- Enables organizations to authenticate their users of Cloud services using the chosen identity provider  
- User identities across different organizations can be managed together to enable collaboration on Cloud  

<mark style="background: #BABD00;">OpenID:</mark>  
- Is an open standard for decentralized authentication and access control  
- Can be used while allowing users to log onto many services using the same digital identity

Identity management is an administrative process that deals with identifying users of an information system. Additionally, identity management also controls access to system resources by placing restrictions using user identities . The key identity management-related aspects in Cloud are as follows:  

<mark style="background: #BABD00;">One-time password:</mark> Because passwords can be compromised, they must be protected. The One-Time Password (OTP) concept demands that a new password be used for each new log on and thus provides necessary security against password compromises. Time-dependent password generated by hardware security tokens (for example, RSA SecureID) is an example of OTP. OTP is specifically useful in situations where likelihood of password compromises are high, for example, remote login based network access.  

<mark style="background: #BABD00;">Federated Identity Management:</mark> Federation is the process of managing the trust relationships among distinct organizations beyond the internal network or administrative boundaries. A federation is an association of organizations that come together to exchange information about their users and resources to enable collaborations and transactions. In a Cloud, Federated Identity Management (FIM) can play a vital role in enabling organizations authenticate their users of Cloud services using the organizations’ chosen identity provider. This would involve exchanging identity  attributes between the CSP and the identity provider in a secure way.  

<mark style="background: #BABD00;">OpenID:</mark> It is an open standard that describes how users can be authenticated in a decentralized manner, obviating the need for services to provide their own ad hoc systems and allowing users to consolidate their digital identities. OpenID enables maintaining single-user credentials for access control and can be used while allowing users to log onto many services using the same digital identity. It allows users to log in once and gain access to resources across participating systems. For example, Google Apps provides cloud identity services to its enterprise customers using OpenID.

### <mark style="background: #BABD00;">Governance, Risks and Compliance:</mark>

This lesson covers governance, risk, and compliance aspects in Cloud. Governance aspects include SLAs and information flow regulations. Risk assessment includes identification of critical assets, potential risks, and the classification of critical assets into risk categories. Compliance includes internal and external policy compliance

<mark style="background: #BABD00;">Governance</mark> refers to the policies, processes, laws, and institutions that define the structure by which companies are directed and managed.  

<mark style="background: #BABD00;">Risk</mark> refers to the effect of uncertainty on business objectives; risk management is a coordinated activity to direct and control an organization, and to realise business potential while managing negative events.  

<mark style="background: #BABD00;">Risk has two separate parts:</mark> Identification and mitigation

<mark style="background: #BABD00;">Compliance</mark> refers to the act of adhering to and demonstrating adherence to external laws and regulations as well as corporate policies and procedures.

An Enterprise GRC (eGRC) solution allow a business to build an efficient, collaborative enterprise governance, risk and compliance (eGRC) program across IT, finance, operations, and legal domains. Such a program enables a business to manage risks, demonstrate compliance, automate business processes, and gain visibility into corporate risk and security controls.

A backup is only as good as your demonstrable ability to restore from that backup

### <mark style="background: #BABD00;">Cloud Governance: Information Flow Regulations</mark>

National and international regulations could constrain the flow of information in Cloud  
- Various legislations specify that sensitive information cannot travel across regional boundaries; for example, European data protection laws impose obligations on handling and processing of data transferred to the U.S.  
- Existing Security standards also apply to Cloud  
- Specific regulations control certain types of information  
Information (data) flow regulations may limit adoption of public Clouds for applications handling sensitive data  

Among various Cloud deployment models, private Clouds offer the maximum information flow regulation

National and international regulations could constrain the flow of information in Cloud. For example, Cloud offers location independence to its clients in terms of where the actual data resides. This might also lead to difficult legal issues; for example, a governmental data on a Cloud, handled abroad by private parties, fall under the foreign jurisdiction. There are various regulations, which specify that sensitive information cannot travel across regional boundaries; for example, European data protection laws impose additional obligations on the handling and processing of data transferred to the U.S.  

Another aspect is that existing security standards may also apply to Cloud; for example, it is recommended that CSPs follow ISO 27001, which is an Information Security Management System standard and formally specifies requirements to bring information security under explicit management control.  

Furthermore, there are regulations that control certain specific types of information. For example, the Administrative Simplification provisions of Health Insurance Portability and Accountability Act (HIPAA) specify security and privacy aspects dealing with medical data in the USA.  

Such information flow regulations may limit adoption of Public Clouds for applications handling sensitive data. For example, governmental agencies might find it difficult to use public Clouds, which could potentially host their data in some other country due to cost advantages.  

Among various Cloud deployment models, private Clouds offer the maximum information flow regulation because the control over data remains fully with the organisation

### <mark style="background: #BABD00;">Cloud Governance: Contract Termination:</mark>

Cloud users need to assess implications of situations when services with a CSP should be terminated  

Termination agreement specifies the closure process  

<mark style="background: #BABD00;">Situations may include:</mark>  
- CSP going out of business  
- CSP cancelling the contract  
- Natural closure of a contract  

<mark style="background: #BABD00;">Key Considerations for a Cloud user:</mark>  
- Developing a contingency plan for handling data  
- Migrating the data, including time to migrate the data  
- Shredding the data on the Cloud after its migration

A client needs to assess implications when the existing business with a CSP needs to be terminated.  

There might exist many situations where such a contract termination is required:  
- The CSP goes out of business and winds up its services  
- The CSP cancels the contract  
- There is a natural closure for the contracted services  

In order to avoid the negative impact of such a closure, there needs to be a formal agreement between a Cloud client and the CSP, which is referred as termination agreement. 

In situations which involve the closure of the Cloud services for a client, the following points should be  
considered:  
- A contingency plan for handling data in the Cloud  
- A process for migrating the data back into the organisation or to another Cloud  
- A prior assessment as to whether the data can be moved over the network in a reasonable amount of time or whether it is necessary to make special arrangements for a physical transfer  

The plan for data destruction (storage, clones, backups) using shredding after the data has successfully moved from the Cloud

### <mark style="background: #BABD00;">Risk Assessment:</mark>

Aims to identify potential risks while operating in a Cloud environment  
- Should be performed before moving to a Cloud  
- Used to determine the actual scope for Cloud adoption

Steps to perform Risk Assessment  
1. Identifying critical and sensitive assets (data, applications, and processes)  
	- <mark style="background: #BABD00;">Critical assets</mark> are necessary for the operation of the business  
	- <mark style="background: #BABD00;">Sensitive assets</mark> are those having high business value  
2. Identifying potential risks  
3. Classifying risks into severity levels  
4. Associating potential risks with critical assets

A risk assessment process aims to identify potential sources of risk while operating in a Cloud environment. This critical process is required before deciding to move operations to Cloud, especially if the decision is related to the Public Clouds.  

<mark style="background: #BABD00;">Various steps involved in this process are:</mark>  
1. <mark style="background: #BABD00;">Identifying critical and sensitive assets:</mark> All the assets (data, applications, and processes) must be carefully evaluated to assess as to how critical or sensitive an asset is for the organisation. Critical assets are necessary for the operation of the business. Sensitive assets are those having high business value for the organisation, for example, Intellectual Property (IP), project plans, and Personally Identifiable Information (PII).  
2. <mark style="background: #BABD00;">Identifying potential risks:</mark> It is important to analyse and identify all the potential risks while operating in a Cloud environment. An example could be the legal situations under which a CSP might have to disclose data belonging to its clients.  
3. <mark style="background: #BABD00;">Classifying risks into severity levels:</mark> After comprehensive classification of the risks associated with operating in Cloud, these risks need to be classified into various severity levels i.e., very high risk, moderately high risk, high risk, low risk, and no risk. These severity levels could alternately be numbered in a certain range, for example, 0 to 5.  
4. <mark style="background: #BABD00;">Associating potential risks with critical assets:</mark> This step involves associating the critical assets with potential risks; for example, employee’s banking records can be identified as critical assets (in step 1), data disclosure could be a risk (identified in step 2) of very high severity level (in step 3). Based upon these, data disclosure risk may be associated with  employee records.  

Based upon the risk assessment for the assets, a client could consider formulating terms and conditions of the contractual agreement with CSP; for example, a client might insist on having its data placed within certain geographical regions by the CSP.

### <mark style="background: #BABD00;">Compliance:</mark>

Cloud adoption and operation for enterprise businesses need to abide by compliance policies    

<mark style="background: #BABD00;">Internal policy compliance:</mark>  
- Controls the nature of IT operations within an organization  
- Needs to maintain same compliance even when operating in Cloud  

<mark style="background: #BABD00;">External regulatory compliance:</mark>  
- Includes legal legislations and industry regulations  
- Controls the nature of IT operations related to flow of data out of an organization  
- May differ based upon the type of information, business, etc.  

Meeting all varied client compliance requirements is difficult for a CSP  

Compared to Private Clouds, the Public Cloud environment makes compliance more challenging

Cloud service adoption and operation for enterprise businesses should abide by compliance policies. There are primarily two types of policies controlling IT operations in an enterprise that requires compliance even after moving operations to Cloud.  

Internal Policy Compliance: Controls the nature of IT operations within an organization. A Cloud client organization needs to maintain same compliance even when operating in Cloud. This would require clear assessment of the potential difficulties in maintaining the compliance in Cloud and a process to ensure that this is effectively achieved.  

External Policy Compliance: Includes legal legislations and industry regulations. These external compliance policies control the nature of IT operations related to the flow of data out of an organization. However, they may differ based upon the type of information (for example, source code versus employee records), business (for example medical services versus financial services), etc.  

Meeting all the varied client compliance requirements is generally difficult for a CSP. Compared to Private Clouds, the Public Cloud environment makes compliance more challenging. Therefore, many enterprises may prefer to adopt the hybrid Cloud deployment model so that they can ensure all the necessary policy compliances.

### <mark style="background: #BABD00;">Summary:</mark>

- VDC and Cloud security concerns and threats  
- Cloud infrastructure security mechanisms at compute, storage, and network levels  
- Access control and identity management mechanisms in Cloud  
- Governance, Risk, and Compliance (GRC) aspects in Cloud including information flow regulations and risk assessment  
- Cloud security best practices including reference architecture for Cloud security

This module covered VDC and Cloud security concerns and threats including multitenancy, data privacy and ownership, and velocity of attack factor.  

Cloud infrastructure security mechanisms at compute, storage, and network levels include securing data using encryption, intrusion detection techniques, and methods to provide physical security.  

Access control mechanism included RBAC. Identity management included one-time password, federated identity management, and OpenID.  

The Governance, Risk, and Compliance (GRC) discussion focused upon various aspects, including information flow regulations and risk assessment process. Finally, the module discussed Cloud security best practices including recommendation of Cloud security Alliance.