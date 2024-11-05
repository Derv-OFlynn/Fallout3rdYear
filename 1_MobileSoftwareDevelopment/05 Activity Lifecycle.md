### <mark style="background: #AD21D9;">Activity Life in Android Applications:</mark>

Manifest File  

Activity Lifecycle  
- Callbacks  
- Instance State  
- Saving and Restoring Activity State

### <mark style="background: #AD21D9;">Introduction:</mark>

Every app project must have an AndroidManifest.xml file.  

It lives at the root of the project source set.  

<mark style="background: #AD21D9;">Describes essential information about your app to:</mark>  
1. Android Build Tools  
2. Android Operating System  
3. Google Play

### <mark style="background: #AD21D9;">Location:</mark>

![](https://i.imgur.com/EwHJqBg.png)

### <mark style="background: #AD21D9;">Rules:</mark>
1. Only ``<manifest>`` and ``<application>`` elements are required. (Must occur only once.) 
2. Most other elements can occur 0 or more times. 
3. All values are set through attributes. 
4. Elements at same level are generally not ordered.

### <mark style="background: #AD21D9;">Example:</mark>
```XML
<?xml version="1.0" encoding="utf-8"?>  
<manifest >  
	<application  
	android:theme = "@style/AppTheme">  
		<activity android:name = ".ActivityA">  
			<intent-filter>  
			</intent-filter>  
		</activity>  
		<activity />  
		<activity />  
	</application>  
</manifest>
```

### <mark style="background: #AD21D9;">Contents:</mark>

Things found inside the manifest file include:
1. <mark style="background: #AD21D9;">Package name:</mark> Used to find pieces of code when building your project.  
2. <mark style="background: #AD21D9;">Components:</mark> (e.g. Activities) Each component must define basic properties e.g. name of Java/Kotlin class.   
3. <mark style="background: #AD21D9;">Capabilities:</mark> Device configurations it can handle and Intent filters (start-up).  
4. <mark style="background: #AD21D9;">Permissions:</mark> For App to access protected parts of the system or other apps.  
5. <mark style="background: #AD21D9;">Features required:</mark> Affects which devices can install the app from Google Play

### <mark style="background: #AD21D9;">Package Name:</mark>

The manifest file's <mark style="background: #AD21D9;">root</mark> element requires an <mark style="background: #AD21D9;">attribute</mark> for your app's package name:

```XML
<manifest xmlns:android = "http://schemas.android.com/apk/res/android" package = "com.example.lifecycle">
```

When building the APK, the package attribute is important e.g. as <mark style="background: #AD21D9;">namespace</mark> for generated R class ``com.example.lifecycle.R``  

It also resolves <mark style="background: #AD21D9;">relative</mark> class names declared in the manifest file e.g. ``com.example.lifecycle.ActivityA``

### <mark style="background: #AD21D9;">Permissions:</mark>

Android apps must <mark style="background: #AD21D9;">request</mark> permission to access:  
- <mark style="background: #AD21D9;">Sensitive</mark> user data (contacts and SMS)  
- Certain system features (<mark style="background: #AD21D9;">camera</mark> and network connection)  

Permissions are requested with a ``<uses-permission>`` <mark style="background: #AD21D9;">element</mark> and identified by a unique label e.g.to send SMS messages

```XML
<uses-permission android:name = "android.permission.SEND_SMS"/>
```

Beginning with API level 23, the user can approve or reject some app permissions at <mark style="background: #AD21D9;">runtime</mark>.  

If the permission is <mark style="background: #AD21D9;">granted</mark>, the app is able to use the protected features. If not, its attempts to access those features <mark style="background: #AD21D9;">fail</mark>.

### <mark style="background: #AD21D9;">App Components:</mark>

For each app component in your app, declare an XML element:  
- Activity  ``<activity>``
- Service  `<service> `
- BroadcastReceiver  `<receiver>`
- ContentProvider  `<provider>`
 
If you <mark style="background: #AD21D9;">subclass</mark> these components without declaring it in the manifest file, the system cannot start it.

When an app issues an <mark style="background: #AD21D9;">Intent</mark> to the system, it locates an app component that can handle it based on ``<intent-filter>`` declarations  
in each app's manifest file.

### <mark style="background: #AD21D9;">Device Compatibility:</mark>

Play Store does not allow app be installed on devices that don't provide required features.  

Hardware or software features your app requires are declared with ``<uses-feature>`` element.

```XML
<uses-feature android:name = "android.hardware.sensor.compass" android:required = "true" />
```

### <mark style="background: #AD21D9;">Activity Lifecycle:</mark>

![](https://i.imgur.com/8TKF5Me.png)

### <mark style="background: #AD21D9;">What is the activity lifecycle?</mark>

The set of <mark style="background: #AD21D9;">states</mark> an Activity can be in during its lifetime, from when it is created <mark style="background: #AD21D9;">until</mark> it is destroyed  

<mark style="background: #AD21D9;">In Google Speak:</mark>  
- A directed graph of all the states an Activity can be in, and the <mark style="background: #AD21D9;">callbacks</mark> associated with transitioning from each state to the next one

![](https://i.imgur.com/yM3OhNJ.png)

<mark style="background: #AD21D9;">States:</mark> Lifecycle state changes are <mark style="background: #AD21D9;">triggered</mark> by user action, configuration changes such as device rotation, or system action.

### <mark style="background: #AD21D9;">Activity Lifecycle Callbacks:</mark>

Only ``onCreate()`` is <mark style="background: #AD21D9;">required</mark>.  

Override the other callbacks to change <mark style="background: #AD21D9;">default</mark> behaviour

### <mark style="background: #AD21D9;">On Create:</mark>

```Kotlin
@Override  
public void onCreate(Bundle savedInstanceState){  
super.onCreate(savedInstanceState);  
// Activity is being created.  
}
```
Called when Activity is first created e.g. user hits <mark style="background: #AD21D9;">launcher</mark> icon.  

Does all <mark style="background: #AD21D9;">static</mark> setup: create views, bind data to lists...  

Only called <mark style="background: #AD21D9;">once</mark> during an activity's lifetime.  

Takes a <mark style="background: #AD21D9;">bundle</mark> with Activity's previously frozen state, if exists.  

Created state is always followed by ``onStart()``

### <mark style="background: #AD21D9;">On Start:</mark>

```Kotlin
@Overrideprotected void onStart() 
{  
	super.onStart();  
	// Activity is about to become visible.  
}
```

Called when the Activity is becoming <mark style="background: #AD21D9;">visible</mark> to user.  

Can be called <mark style="background: #AD21D9;">more than once</mark> during lifecycle.  

Followed by ``onResume()`` if the activity comes to the foreground, or ``onStop()`` if it becomes hidden.

### <mark style="background: #AD21D9;">On Restart:</mark>

```Kotlin
@Override  
protected void onRestart() {  
	super.onRestart();  
// Activity is between stopped and started.  
}
```
Called after Activity has been <mark style="background: #AD21D9;">stopped</mark>, immediately before it is started again.  
- Transient state.  
- Always followed by ``onStart()``.

### <mark style="background: #AD21D9;">On Resume:</mark>

```Kotlin
@Override protected void onResume() 
{  
	super.onResume();  
	// Activity has become visible, it is now "resumed"  
}
```
Called when Activity will start interacting with user.  
Activity has moved to top of the Activity Stack.  

Starts accepting user input.  

Running state.  

Always followed by ``onPause()``.

### <mark style="background: #AD21D9;">On Pause:</mark>

```Kotlin
@Override protected void onPause() 
{  
	super.onPause();  
	// Another activity is taking focus, this one is about to be "paused"  
}
```

Called when system is about to resume a previous Activity.  

Activity is partly visible but user is leaving the Activity.  

Typically used to commit unsaved changes to persistent data, stop animations and anything that <mark style="background: #AD21D9;">consumes resources</mark>.

Implementations must be fast because <mark style="background: #AD21D9;">next</mark> Activity is not resumed <mark style="background: #AD21D9;">until</mark> this method <mark style="background: #AD21D9;">returns</mark>.  

Followed by either ``onResume()`` if the Activity returns back to the front or ``onStop()`` if it becomes invisible to the user.

### <mark style="background: #AD21D9;">On Stop:</mark>

```Kotlin
@Override protected void onStop() 
{  
	super.onStop();  
	// Activity is no longer visible it is now "stopped"  
}
```
Called when the Activity is no longer <mark style="background: #AD21D9;">visible</mark> to the user.  

A <mark style="background: #AD21D9;">new</mark> Activity is being started, an existing one is brought in front of this one, or this one is being destroyed.  

Operations that were too heavy-weight for ``onPause()``  

Followed by either ``onRestart()`` if Activity is <mark style="background: #AD21D9;">coming back</mark> to interact with user, or ``onDestroy()`` if Activity is <mark style="background: #AD21D9;">going away</mark>.

### <mark style="background: #AD21D9;">On Destroy:</mark>

```Kotlin
@Override protected void onDestroy() 
{  
	super.onDestroy();  
	// Activity is about to be destroyed.  
}
```
<mark style="background: #AD21D9;">Final</mark> call before Activity is destroyed.  

User navigates <mark style="background: #AD21D9;">back</mark> to previous Activity, or configuration changes.  

Activity is <mark style="background: #AD21D9;">finishing</mark> or system is destroying it to save space.  

Call ``isFinishing()`` method to check.  

The system may destroy Activity without calling this, so use ``onPause()`` or ``onStop()`` to save data or state.

![](https://i.imgur.com/j9orZ8w.png)

### <mark style="background: #AD21D9;">App Visibility:</mark>

- Created (not visible yet)  
- Started (visible)  
- Resume (visible)  
- Paused(partially invisible)  
- Stopped (hidden)  
- Destroyed (gone from <mark style="background: #AD21D9;">memory</mark>)

### <mark style="background: #AD21D9;">Summary:</mark>

``onCreate()`` - Static initialisation  
``onStart()`` - Activity is becoming visible  
``onRestart()`` - If Activity was stopped (calls ``onStart()``)  
``onResume()`` - Start to interact with user  
``onPause()`` - About to resume previous Activity  
``onStop()`` - No longer visible, but still exists and <mark style="background: #AD21D9;">all state</mark> info preserved  
``onDestroy()`` - Final call before System destroys Activity