Two lectures, one lab a week

Dr Abubakr Siddiq

Kotlin, not Java for Android devices as Kotlin is recommended for android.

Using Android, not iOS

50% CA, 50% Exam

CA:
- App assignment at end of semester. Given around week 5, should have around 6 weeks to finish it. The project is about anything you like. - 30%
- Lab marks for weekly labs - 20%

Compulsory to pass the written exam in order to pass the module.

First lab about debugging, logs and version control

### <mark style="background: #AD21D9;">Mobile apps vs. Web apps</mark>

Mobile apps and web apps are <mark style="background: #AD21D9;">NOT</mark> the same thing.

A <mark style="background: #AD21D9;">web app</mark> is a website that is designed fluidly, responding to being viewed on a smartphone i.e. Bootstrap grid.

<mark style="background: #AD21D9;">Native mobile apps</mark> are built for a platform such as iPhone or Android. They are installed via an app store and access to system resources (GPS, camera).

<mark style="background: #AD21D9;">Web apps need an active internet connection</mark> to run, whereas mobile apps may work offline.

Mobile apps are faster but require updates regularly. Web needs no updates.

<mark style="background: #AD21D9;">Mobile apps are more expensive</mark> but faster, and tend to be more advanced in terms of features and functionality.

<mark style="background: #AD21D9;">Native mobile apps are built using specific languages</mark> and Integrated Development Environments (IDEs). Apple devices run on the iOS native operating system and built with Objective-C or Swift using X-Code. Android is usually made using Java or Kotlin and the Eclipse IDE.

Apple and Google also provide their own development tools, interface elements and software development kits (SDK)

<mark style="background: #AD21D9;">Advantages of mobile-first Web Apps:</mark>
- <mark style="background: #AD21D9;">Immediacy</mark> - web apps are instantly available.
- <mark style="background: #AD21D9;">Compatibility</mark> - web apps are compatible across devices.
- <mark style="background: #AD21D9;">Upgradability</mark> - web apps can be updated instantly.
- <mark style="background: #AD21D9;">Reachability</mark> - web apps can be found easily.


<mark style="background: #AD21D9;">(Former) advantages of mobile:</mark>
- Can work offline (games, etc.) → Progressive Web Apps 
- Can use the camera, GPS, etc. → Browser HTML5 APIs
	- navigator.geolocation.getCurrentPosition,
	- navigator.mediaDevices.getUserMedia...  
- Can lead to a better user experience

### <mark style="background: #AD21D9;">Mobile interaction Design Patterns:</mark>

- Vertical stack  
- Generous borders  
- Thumbnail-and-text lists  
- Loading indicators  
- Filmstrip (swipe navigation)  
- Touch tools (show after touch)  
- Infinite list (append more)  
- Text clear button

![](https://i.imgur.com/lCEtsPJ.png)

### <mark style="background: #AD21D9;">6G:</mark>
- It is expected to start in 2030.  
- 6G will have 1TB per second, 1000 times less latency, and 99.9% world coverage.  
- 6G is about transmitting data at ultra-high frequencies  
- Short waves which can transmit a lot of information but with short reach.  
- For more information: https://www.6gchannel.com/items/6g-white-paper-networking/

### <mark style="background: #AD21D9;">Programming Language Evolution</mark>

<mark style="background: #AD21D9;">1st Generation:</mark>
- Simple Programmes
- Sequential lines of code
- Hard to manage and leads to code duplication

<mark style="background: #AD21D9;">2nd Generation:</mark>
- Code broken up into <mark style="background: #AD21D9;">functions</mark>
- Also known as subroutines
- Easier to manage and minimises code duplication.

<mark style="background: #AD21D9;">3rd Generation:</mark>
- OO & Classes
- Group functions into classes
- Classes represent real world functionality
- Objects = Data and Functionality

### <mark style="background: #AD21D9;">What is a framework?</mark>

A platform that helps to build computer applications

Provides necessary components to build tools that have a similar architecture

Generally the tools are for a similar purpose

<mark style="background: #AD21D9;">Examples of frameworks:</mark>
- Node.js - online applications
- Java RMI is used for distributed systems
- Scikit-learn, PyTorch and Keras are frameworks based on Python for machine learning.
- Android Developer Studio to learn how to build apps on Android.
- GIMP and Photoshop - picture editing

<mark style="background: #AD21D9;">Characteristics of a good framework:</mark>
- Easy to use
- Does not contain redundant functions
- Well documented
- Uses best practices
- Code is optimised
- Allows reusable components
- Easy to compile and debug

<mark style="background: #AD21D9;">Why use a framework?</mark>
- Increases productivity
- People that have learned it do not need to learn it again
- Allows focusing on the particularities of the project, not the generic repetitive code
- Reduces costs
- By using conventions the code is understandable by others

<mark style="background: #AD21D9;">Challenges of using a framework:</mark>
- May not have all functionalities
- May not be the best solution for small applications
- Vulnerability in a framework applies to all the applications created on that framework
- Learning curve makes you unproductive at the beginning of the process
- Senior people can be less willing to change into a new framework. Some people can be very reluctant.

### <mark style="background: #AD21D9;">Smartphone Application development</mark>

<mark style="background: #AD21D9;">Design you apps with these in mind:</mark>
- Never before has so much functionality been made available to developers in one device
- Smartphones are extremely personal devices
- Limited memory, CPU and storage
- Replacing wallets
- Smartphone OSs are becoming embedded in many things
- Smartphones have a very limited battery power

### <mark style="background: #AD21D9;">What is Android?</mark>

Android is a mobile OS based off a modified Linux kernel 

Free and open source OS. Licensed under Apache 2.0 and GPL 2 since Oct 2008, including network & telephony stacks

Purchased by Google in 2005, Android is now developed by Open Handset Alliance (but de-facto by Google, which is controlling the development process and doing the lion's share of work)

### <mark style="background: #AD21D9;">Why study android development?</mark>

Most popular OS

71% usage in global market

62% usage in Ireland

Android License -> business friendly licenses (Apache/MIT):
- Can freely extend it
- Variety of purposes
- Rewrite and include expensive libraries.  
- You have access to the entire source code:  
- Understand the core functionality.  
- Add secret sauces without sharing.

In brief, there is no need to license Android, you can start using and modifying it today.

### <mark style="background: #AD21D9;">Android Assumptions:</mark>
- Purpose built platform for mobile devices
- Always going to be limited in terms of memory
- Designed to run on all sorts of physical devices
- Nothing is predefined -> chipset, screen size, etc
- Its core is designed to be portable.

### <mark style="background: #AD21D9;">Android Activity Framework:</mark>

The activity class provides a number of call-backs that allow the activity to know that a state has changed

![](https://i.imgur.com/29gJtMs.png)



### <mark style="background: #AD21D9;">Android Layer architecture:</mark>

<mark style="background: #AD21D9;">System Apps</mark> -> these are applications. Google comes with default apps. Google codes their apps before converting to bytecode.

<mark style="background: #AD21D9;">Java API frameworks</mark> -> provides tools for executing the apps. Such as activity manager, video players, or internal browser.

<mark style="background: #AD21D9;">Native C/C++ libraries | Android Runtimes</mark> -> They are in C/C++ because they are more efficient. Heavy lifiting. 
- Hardware Layer Application (HLA)
- Linux Kernel

![](https://i.imgur.com/RstMTdC.png)



### <mark style="background: #AD21D9;">Google Play:</mark>

Developers can write apps, extending the functionality of Android-powered devices

Android Market is an online app store run by Google  

Other stores are possible and they exist (Amazon App Store, others)  

Apps are developed in Java language working with Google-developed libraries  
- Other ports are in progress (so far unofficially), including PHP(?), Go  
- NDK for C/C++ is already available

Over 2bln devices in use (2020)

Around 1.5mln new activations everyday

Ireland:
- 1.6mln users

<mark style="background: #FF5582A6;">FINISH ^</mark>

### <mark style="background: #AD21D9;">Why Android has become dominant:</mark>

<mark style="background: #AD21D9;">Users:</mark>
- Excellent budget/feature variation choice
- Very well integrated into other google services that people use (Search, mail, etc)
- Hundreds of thousands of apps available


### <mark style="background: #AD21D9;">Developer Workflow Basics:</mark>

<mark style="background: #AD21D9;">Setup:</mark>
- Android studio
- Create your project

<mark style="background: #AD21D9;">Write your app:</mark>
- Start with basic project in android studio and build on it
- This is what we focus on

<mark style="background: #AD21D9;">Build and Run:</mark>
- Either use an emulator or Android device

<mark style="background: #AD21D9;">Debug, Profile and test:</mark>
- We will need to learn about the tools you should use
- Need to make sure your app is performing well

<mark style="background: #AD21D9;">Publish:</mark>
- Google play standard

![](https://i.imgur.com/WGThiyH.png)


### <mark style="background: #AD21D9;">Mobile vs. Desktop:</mark>

- Many will only have developed for desktop environments
- Significant differences between both platforms

Exercise:
- 5 mins do a bit of research for 

<mark style="background: #AD21D9;">Main Differences:</mark>
- CPU power and architecture.  
- GPU power and architecture.  
- Storage space and speed  
- Screen size, resolution and density.  
- User interaction  
- Power sources

<mark style="background: #AD21D9;">Why this matters:</mark>
- A good developer is one who can make robust efficient code.  
- A great developer is one who can make robust efficient code that takes full advantage of the architecture on which it is built  
- If you want to produce the best code you need to know your architectures

<mark style="background: #AD21D9;">CPU Power and Archictecture:</mark>
- Optimisations specific to x86 will no longer work
- You will have significantly less power available. Thus, you must be even more efficient and/or offload to the cloud/servers
- Emphasis on efficiency is stronger on mobile. ARM will not execute instructions as quickly as x86 (even if clock speeds for ARM are higher than x86)
- Anywhere you see the opportunity for efficiency, take it

<mark style="background: #AD21D9;">Storage Space and speed:</mark>
- Storage also presents significant differences
- Desktop uses magnetic rotating storage but is moving to SSD. Space is generally 512GB to 4TB range
- Mobile is all SSD. Space is generally between 64GB and 128GB but moving towards 256GB.
- The amount of data you can store on mobile is significantly reduced
- Cannot assume everyone has loads of storage for your application
- Keep your apps small and only include what is necessary

<mark style="background: #AD21D9;">Screen size, Resolution and density:</mark>

Biggest difference between desktop and mobile

Phones and tablets mainly differ in two dimensions
1. Physical size of screen (4 to 10 inches)
2. The resolution of the screen (800x480 to 2560x1600)

Matters on mobile because everything is fullscreen by default, Meaning your application must adapt to many screen sizes.

Apps need to adjust UI based on physical screen size and pixel dimensions

Raster images need multiple copies at different resolutions to account for different densities.

Image scaling is expensive and can lead to blockiness/blurriness

Even if a device has a higher res, you may not be able to pack a dense UI. You are also limited by physical space.

If your application is to also run on a tablet you should adjust your UI to take advantage of the physical space  

From a development standpoint apps should take account of physical dimensions first then display density  

Build your app and UI for a phone (4 to 6 inches) first then for tablets (7 to 10 inches) after  

Easier to add extra functionality into a UI than cut it down

### <mark style="background: #AD21D9;">Interaction between user and device:</mark>

On desktop, interaction is generally through the use of a pointer

This offers single pixel precision meaning UIs can be smaller and denser

On mobile, interaction is through touch

The area of pixels is not as precise as a pointer

Meaning that controls must be larger to compensate for the area of touch, leading to lower UI density

When added to reduced screen size, your UIs have very little space to display information

Need to determine if every piece of information is necessary

Your controls must also be large enough for your users to comfortably interact with further reducing your space

### <mark style="background: #AD21D9;">Power Source:</mark>

Another significant difference is the power sources used

Desktop machines have access to AC so power is not a concern

Mobile batteries are limited by battery life

Battery technology has not advanced as quickly as CPU over the last 20 years.

Most devices can manage a day on battery with active user management

Because users are aware of their battery, they will not like apps that eat battery life

Thus, more reason to be efficient

``Better performance = less overall usage = longer battery life``  

Remember every action you take on a mobile device will cost battery