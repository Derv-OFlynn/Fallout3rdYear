![](https://i.imgur.com/YoZlMzc.png)

### <mark style="background: #AD21D9;">Topics:</mark>

- Intents (Implicit, Explicit)  
- Passing Data  
- Permissions  
- Navigation

### <mark style="background: #AD21D9;">Application Structure:</mark>

Due to the limited screen space of devices applications are structured as a collection of activities connected by intents  

Activities take up a full screen and are responsible for displaying a UI and interacting with the user  

Intents are responsible for launching and returning from activities and communicating data between the two  

### <mark style="background: #AD21D9;">Activities:</mark>

All applications in Android are required to use the full screen of the device. This has two effects  
- gives the largest space possible for displaying a UI 
- takes full control of the CPU to give the fastest response time  

If it is not possible to use a single activity to represent the full functionality of the application then there needs to be a mechanism to transfer from one to another

### <mark style="background: #AD21D9;">What is an intent?</mark>

Intents are objects that provide the language/description of an operation to be performed.  

An Intent (your intention for the app) is constructed by the activity that wants some work done. Received by another activity that can perform that work.

![](https://i.imgur.com/BcpJdCP.png)

![](https://i.imgur.com/Z3V6nCg.png)

### <mark style="background: #AD21D9;">Intents:</mark>

Used to link from one activity to the next  

An intent asks the android system to start a new activity for this application  

Intents can also have data attached to them to either seed the new activity or contain results to be returns from an activity  

<mark style="background: #AD21D9;">However, there are two different classes of intent:</mark>  
- Explicit  
- Implicit

### <mark style="background: #AD21D9;">Two Flavours: Implicit and Explicit:</mark>

<mark style="background: #AD21D9;">Explicit</mark>  
- Navigation – Launch a specific activity  
- ``Intent(Context packageContext, Class <?> cls)``  

Create an intent for a specific activity. Pass intent to ``startActivity()`` method.

<mark style="background: #AD21D9;">Implicit:</mark>
- Specify what you want done and the System chooses the app for you  
	- ``Intent(String action)``  
	- ``Intent(String action, Uri uri)``  
- Create an Intent with action. Or create Intent with action and other parameters such as Data  in the form of Uri Pass intent to ``startActivity()`` method

### <mark style="background: #AD21D9;">Explicit Intent:</mark>

An explicit intent is one where you know the fully qualified name of the activity you wish to start.  

Generally, you will use this to refer to activities that are in your own application  

Or if there is an external application you use where you know the fully qualified name of the activity to start

### <mark style="background: #AD21D9;">Implicit Intent:</mark>

An implicit intent is one where you have data you need to display or interact with however, you do not know how to do this  

With such an intent android will try to find another external application that is capable of rendering the content or interacting with it  

Thus there is the possibility that a compatible application may not be present  

This has implications for application design

From an OS perspective, applications are expected to do a single job and do it well.  

If they need support for different types of data then they should hand that to a separate application instead of self-implementing  

The idea is that by removing duplicate functionality applications are small, bug-free, and integrate with each other.  

Thus if you need some common functionality to try linking up to another application  

Reduces the amount of code you need to write and increases reliability.

### <mark style="background: #AD21D9;">Start - Explicit Way:</mark>

If you know the name of the Activity, use an Explicit Intent  
1. Create an Intent  
2. Use the Intent to start the Activity– Method call is ``startActivity()`` (Code taken from ``HelloAndroidWithLogin``)

```Kotlin
// Create an explicit Intent for starting the HelloAndroid Activity  
//need context and the calling class for Constructor  
val helloAndroidIntent = Intent(this,HelloWorld::class.java)  
// Use the Intent to start the HelloAndroid Activity  
startActivity(helloAndroidIntent)
```

### <mark style="background: #AD21D9;">Class Demo HelloAndroidWithLogin:</mark>

``LoginScreen`` Activity calls ``HelloAndroid`` Activity  
Code Available on BrightSpace
![](https://i.imgur.com/EEqQEu6.png)

### <mark style="background: #AD21D9;">Activity Manifest:</mark>

All Activities must be registered in the Activity Manifest to be launched  

For the activity launcher to start an activity, the  
activity needs to be registered in the Android  
manifest with the correct intent filter  

Activities that are launched explicitly must also be declared in the Manifest file

Review the ``HelloAndroidWithLogin`` code

![](https://i.imgur.com/FTLBxJS.png)

### <mark style="background: #AD21D9;">Start - Implicit Way:</mark>

To ask Android to find an Activity to handle your request, use an implicit Intent  
1. <mark style="background: #AD21D9;">Create an Intent:</mark> Constructor take a String Action and Data Value specified as a URI  
2. Use the Intent to <mark style="background: #AD21D9;">start the Activity</mark> i.e. Google Maps

```Kotlin
Intent(String action, Uri uri)  
// Create an Intent with action and Data.  
Intent geoIntent = new  
Intent(android.content.Intent.ACTION_VIEW,  
Uri.parse("geo:0,0?q=" + address));  
//It takes two parameters: an action value specified  
//as a String and a data value specified as a URI  
startActivity(geoIntent)
```

### <mark style="background: #AD21D9;">Class Demo:</mark>

MapLocation  

Implicit Intents: - start Google Maps  

Constructor Values found at https://developer.android.com/guide/components/intents-common

![](https://i.imgur.com/j63tV23.png)

### <mark style="background: #AD21D9;">Implicit Intents - Examples of String Actions:</mark>

Each implicit intent must have an action 

The action describes what must be done  

Common actions are view, edit or dial  

In addition to actions, an intent has other fields such as datatype, category, URI  

Look at the ``ImplicitIntents`` Code

![](https://i.imgur.com/m2ShnvJ.png)

### <mark style="background: #AD21D9;">Intent Resolution - Implicit Intent</mark>

Illustration of how an implicit intent is delivered through the system to start another activity: 
1. Activity A creates an Intent with an action description and passes it to ``startActivity()`` 
2. The Android System searches all apps for an intent filter that matches the intent. 
3. When a match is found the system starts the matching activity (Activity B) by invoking its ``onCreate()`` method and passing it the Intent.  
Ref:  http://developer.android.com/guide/components/intents-filters.html

### <mark style="background: #AD21D9;">Example of Google Maps Intent Filter:</mark>

As you already know, the ``MapLocation`` application got ``GoogleMaps`` to do its work, i.e. to show an address on a Map. 

The Intent filter specified in the Google Map application would have been similar to the following:

```XML
<intent-filter...>  
<action android:name="android.intent.action.VIEW"/>  
<category android:name="android.intent.category.DEFAULT"/>  
<category android:name="android.intent.category.BROWSABLE"/>  
<data android:scheme="geo”/>  
<intent-filter>
```

Action: ACTION_VIEW  

Categories: DEFAULT, BROWSABLE  

Data: URIs with the geo scheme This means that the component can be used to display geographical locations to the user, and it can be launched from a web browser or by other apps using an implicit intent with the ACTION_VIEW action and a geo URI.  
- Example If an app sends an implicit intent with the ACTION_VIEW action and a URI like geo:0,0?q=TUD+Dublin+Ireland, the system will search for components with an intent filter that matches these criteria.  
- If the provided intent filter is present in an activity's manifest, that activity will be considered a candidate to handle the intent.

### <mark style="background: #AD21D9;">Permissions:</mark>

The Implicit Intents example needed a permission for the timer. This permission is placed in the Manifest file  
```Kotlin
<uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
```  

Android permissions control an app’s access to user data and device features.  

They ensure apps only access the data they need to function.  

Protect user privacy and prevent unauthorized access.

<mark style="background: #AD21D9;">Normal Permissions: (Set Timer)</mark>  
- Grant access to less sensitive information (e.g., Internet).  
- Automatically granted by the system.  

<mark style="background: #AD21D9;">Dangerous Permissions:</mark>  
- Access more sensitive data (e.g., location, camera).Require explicit user approval.

### <mark style="background: #AD21D9;">Sending and Receiving Data with Intents:</mark>

<mark style="background: #AD21D9;">putExtra()</mark> – for passing data  

<mark style="background: #AD21D9;">Data</mark> - Data can be added to an intent object before it is started via the ``putExtra()`` method. Data is added in the form of key-value pairs. Data (Username) was passed from the Login Screen to the ``HelloAndroid`` Screen in the ``HelloAndroidWithLogin`` code.

```Kotlin
// Use the Intent to start the HelloAndroid Activity  
//add text  
helloAndroidIntent.putExtra("UserName", uname.text.toString())  
startActivity(helloAndroidIntent)
```

### <mark style="background: #AD21D9;">How it works: A passing to B:</mark>

<mark style="background: #AD21D9;">In Activity A (sender);</mark>  
- Create the Intent object  
- Put data into that Intent  
- Start the new Activity with startActivity()  

<mark style="background: #AD21D9;">In Activity B (receiver):</mark>  
- Get the Intent object that Activity was started with  
- Retrieve the data or extras from the Intent object

### <mark style="background: #AD21D9;">Navigation:</mark>

<mark style="background: #AD21D9;">Activity Stack:</mark>  
- When a new Activity is <mark style="background: #AD21D9;">started</mark>, the previous Activity is <mark style="background: #AD21D9;">stopped</mark> and pushed on the Activity back stack  
- <mark style="background: #AD21D9;">Last In First Out</mark> Stack - when the current Activity ends, or the user presses the Back button, it is popped from the stack and the previous Activity resumes

### <mark style="background: #AD21D9;">Back Navigation:</mark>
- Provided by the device's Back button  
- Controlled by the Android System's back 
- Back Stack preserves the history of recently viewed screens. 
- Back Stack contains all the Activity objects that have been launched by the user in reverse order for the current task  
- Each task has its own Back Stack  
- Switching between tasks activates that task's backstack