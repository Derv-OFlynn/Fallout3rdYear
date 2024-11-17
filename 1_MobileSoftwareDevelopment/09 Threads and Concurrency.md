### <mark style="background: #AD21D9;">MultiTasking:</mark>

<mark style="background: #AD21D9;">Nowadays, we multitask all the time:</mark>
1. Read and scroll text of Web page while graphics load.
2. Print document in background while opening another for editing.
3. Reply to email while new message with large file is quietly downloaded.

Threads make all this convenience possible.

### <mark style="background: #AD21D9;">Recap:</mark>

When <mark style="background: #AD21D9;">OS</mark> starts running a program, it creates a new <mark style="background: #AD21D9;">process</mark>.
- A process is a program that is currently executing.
- Every process has at <mark style="background: #AD21D9;">least one</mark> thread running within it.
- When JVM is started, a new process is created

<mark style="background: #AD21D9;">You might think of Java code execution as:</mark>
1. starting with main() method
2. following a path until all statements are completed.

This is an example of a single thread.

2nd thread is always running in JVM i.e. garbage collection thread.

<mark style="background: #AD21D9;">If program includes GUI, JVM starts more threads:</mark>
1. One in charge of delivering GUI events to methods in program
2. Another responsible for painting GUI window.

### <mark style="background: #AD21D9;">In Java:</mark>

Steps to create and run new thread in Java are:
1. Extend ``Java.lang.Thread`` class. Implement run method in this subclass.
2. Create an object of this subclass.
3. Call start method on this object

### <mark style="background: #AD21D9;">In Kotlin:</mark>

```Kotlin
class MyThread : Thread() {
	override fun run() {
		for (i in 0 until 100) {
			println("Thread!")
		}
	}
}
```

```Kotlin
fun main() {
	val t = MyThread()
	t.start()
	
	for (i in 0 until 100) {
		println("Main!")
	}
}
```

### <mark style="background: #AD21D9;">Multithreading:</mark>

![](https://i.imgur.com/dn5v5Dv.png)

### <mark style="background: #AD21D9;">In General:</mark>

3 threads T1, T2, and T3 running on machine with 2 processors.

First, processor 1 runs T1 and the other T2

Then processor 2 switches to run T3.

T2 simply pauses, until its next time slice on a processor.

![](https://i.imgur.com/sMEdPWh.png)

### <mark style="background: #AD21D9;">Lifecycle of a thread:</mark>

![](https://i.imgur.com/FmU75gg.png)

### <mark style="background: #AD21D9;">Modifying the UI with Threads:</mark>

We can do a lot of different operations using the thread class but if we try to modify the UI then we will most likely get an error.

However, Android allows you to use the method ``.runOnUiThread`` to modify the UI directly from a thread

```Kotlin
private fun yourMethodName() {
	Thread {
		try {
			yourActivity.runOnUiThread {
				txtview.text = "some value"
				edittext.setText("some new value")
			}
			} catch (e: Exception) {
				// print the error here
				e.printStackTrace()
		}
	}.start()
}
```

### <mark style="background: #AD21D9;">Back to Android!</mark>

Having a great <mark style="background: #AD21D9;">idea</mark> is a start towards making a cool app.

Next is focus on app's performance e.g. users want apps that:
1. Use power <mark style="background: #AD21D9;">sparingly</mark>.
2. Start up <mark style="background: #AD21D9;">quickly</mark>.
3. <mark style="background: #AD21D9;">Respond</mark> quickly to user interaction.

Today we are interested in responsiveness, hence threads.

### <mark style="background: #AD21D9;">Single Process:</mark>

When an app component (e.g. Activity) starts and <mark style="background: #AD21D9;">no other</mark> components running:

Android starts new <mark style="background: #AD21D9;">Linux</mark> process with <mark style="background: #AD21D9;">single</mark> thread of execution.

By default, all components of app run in the <mark style="background: #AD21D9;">same</mark> process and thread (called “Main" thread).

### <mark style="background: #AD21D9;">Main Thread:</mark>

Independent <mark style="background: #AD21D9;">path of execution</mark> in a running program

Code is executed <mark style="background: #AD21D9;">line by line</mark>.

App runs on Java thread called "main" or "UI thread"
1. <mark style="background: #AD21D9;">Draws</mark> UI on the screen
2. <mark style="background: #AD21D9;">Responds</mark> to user actions by handling UI events

Must be Fast!

Hardware updates screen every 16 milliseconds

UI thread has 16 ms to do all its work

If it takes too long, app stutters or hangs

![](https://i.imgur.com/2Zmy4iV.png)


If the UI waits <mark style="background: #AD21D9;">too long</mark> for an operation to finish, it becomes unresponsive. After 5 seconds of this… The framework shows an <mark style="background: #AD21D9;">Application Not Responding (ANR)</mark> dialog

<mark style="background: #AD21D9;">There are two rules that android uses to determine if an app is unresponsive:</mark>
- Must process a user input event < 5 seconds
- ``BroadcastReceiver`` must finish processing an intent < 10 seconds regardless of source

![](https://i.imgur.com/4SC07RN.png)


### <mark style="background: #AD21D9;">Rules – Consequences of non-observance:</mark>

If you do not respect these rules and adapt your applications in response you can expect the following to happen to your application
- It will be killed by android for being irresponsive
- Your application may lose data as a result
- Eventually users will become frustrated with your application and will uninstall it and replace it by something else

### <mark style="background: #AD21D9;">How Rules affect the App Developer?</mark>

Required to keep your application as responsive as possible

A form of multithreading

Where expensive and long running operations are run on a separate background thread

Leaves the UI thread available for responding to user input events

### <mark style="background: #AD21D9;">Long Running Tasks:</mark>
- Network operations
- Long calculations
- Downloading / uploading files
- Processing images
- Loading data

### <mark style="background: #AD21D9;">Background Threads:</mark>

Execute long running tasks on a <mark style="background: #AD21D9;">background</mark> / worker thread

![](https://i.imgur.com/rbBzP9U.png)

### <mark style="background: #AD21D9;">2 Golden Rules:</mark>

<mark style="background: #AD21D9;">Do not block the UI thread:</mark>
- Complete all work in less than 16 ms for each screen
- Run slow non-UI work on a non-UI thread

Do not access the Android UI toolkit from outside the UI thread. Do UI work only on the UI thread

### <mark style="background: #AD21D9;">Worker Threads:</mark>

As we know, <mark style="background: #AD21D9;">vital</mark> not to block UI thread.

Operations that are <mark style="background: #AD21D9;">not</mark> instantaneous, should be done in threads.

However, we can <mark style="background: #AD21D9;">only</mark> update UI from UI thread.

Android offers <mark style="background: #AD21D9;">several</mark> solutions to this e.g. ``View.post(Runnable)``

### <mark style="background: #AD21D9;">Post Runnable:</mark>

```Kotlin
fun onClick(v: View) {
	Thread(Runnable {
		// A potentially time consuming task.
		val bitmap = processBitMap("image.png")
		
		imageView.post {
			imageView.setImageBitmap(bitmap)
		}
	}).start()
}
```

Background operation is done from <mark style="background: #AD21D9;">separate</mark> thread

``ImageView`` is always manipulated from UI thread.

This kind of code can get complicated and difficult to <mark style="background: #AD21D9;">maintain</mark>.

A better solution is the use of <mark style="background: #AD21D9;">Java Threads for Java</mark> and <mark style="background: #AD21D9;">coroutines for Kotlin</mark>, which simplifies the whole process.

### <mark style="background: #AD21D9;">Services:</mark>

<mark style="background: #AD21D9;">There are four different types of app components:</mark>
- Activities (already covered)
- Services
- Broadcast receivers
- Content providers (not related to multithreading)

Each type serves a distinct purpose and has a distinct lifecycle that defines how the component is created and destroyed.

An application component that can perform long-running operations in the background and does not provide a user interface

In other words: A Service is an Android component that is, almost exactly, an Activity with no UI. Why services? And do we actually need them now?

Started manually via API, or via IPC

### <mark style="background: #AD21D9;">Do You Really Need a Service?</mark>

Services run continuously, draining battery, so use sparingly!

If you only need to perform something in the background while user interacts with your app, just use threads!

### <mark style="background: #AD21D9;">Service Types:</mark>

<mark style="background: #AD21D9;">Started:</mark> A service is "started" when an application component (such as an activity) starts it by calling ``startService()``

<mark style="background: #AD21D9;">Bound:</mark> A service is "bound" when an application component binds to it by calling ``bindService()``

### <mark style="background: #AD21D9;">Started Service:</mark>

Started by ``startService()``

Runs in background indefinitely until it stops itself with ``selfStop()`` or stopped by ``stopService()``

Separate from activity that started it

Does not return any result to the caller

Identified by implementing ``onStartCommand()``

### <mark style="background: #AD21D9;">Bound Service:</mark>

Bound when called with ``bindService()``

Offers client-server interface allowing interaction, get requests, send results

Identified by implementing ``onBind()``

Runs as long as another application component is bound to it (can be multiple). When all unbind, the service is destroyed

### <mark style="background: #AD21D9;">Services:</mark>

<mark style="background: #AD21D9;">Services can be both started and bound at the same time:</mark>
- Implemented both ``onStartCommand()`` and ``onBind()``
- Requires both ``serviceStop()`` or ``selfStop()`` AND all app component to unbind to be destroyed

By default service runs within the main thread of the application!

### <mark style="background: #AD21D9;">Service Methods:</mark>

- ``onCreate()``
- ``onBind()``
- ``onStartCommand()``
- ``onDestroy()``

![](https://i.imgur.com/ceCooKa.png)

### <mark style="background: #AD21D9;">Services - Uses:</mark>

Used when need to keep something running in background while application is not running
- Polling for notifications for a user
- Facebook app (amongst others) are capable of sending you notifications even though the application is not active

Or used for monitoring something without the need for a foreground application e.g. Battery monitors

### <mark style="background: #AD21D9;">Sending notifications to the user:</mark>

When a service is running, it can notify the user of events using:
- snackbar notifications or
- status bar notifications.

A snackbar notification is a message that appears on the surface of the current window for only a moment before disappearing.

A status bar notification provides an icon in the status bar with a message, which the user can select in order to take an action

### <mark style="background: #AD21D9;">Services -Manifest File:</mark>

Like activities, all services must be declared in the manifest file

If an application tries to start an undeclared services, it is considered a security risk and is immediately killed

To declare a service, you must use the ``<service />`` tag

### <mark style="background: #AD21D9;">Broadcast Receiver:</mark>

A broadcast receiver is a component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements.

Listeners could subscribe in order to get notification of events that were of interest.

``BroadcastReceivers`` have proved to be too expensive and too prone to security problems to be used pervasively.

They remain mostly a tool used by the system to signal applications of important events.

### <mark style="background: #AD21D9;">Kotlin Coroutine:</mark>

A coroutine is like a lightweight thread that lets you run multiple pieces of code asynchronously.

Using coroutines means that you can launch a background job without the rest of the code having to wait around for it to complete.

Coroutines can be suspended and resumed mid-execution. This means you can have a long-running task, which you can execute little-by-little. You can pause it any number of times, and resume it when you’re ready again.

### <mark style="background: #AD21D9;">Implementation:</mark>

Mark the targeted method with suspend

``Suspend fun insert()``

Launch the coroutine in background

``yourClass.launch(){x.insert()}``

You can also use asynch instead of launch where:
- <mark style="background: #AD21D9;">launch:</mark> fire and forget
- <mark style="background: #AD21D9;">async:</mark> perform a task and return a result

More is here https://developer.android.com/kotlin/coroutines/coroutines-adv

### <mark style="background: #AD21D9;">WorkManager:</mark>

There are times when you’ll want your app to process data in the background.

This might be because it needs to access storage, for example, or it needs to download a large file.

You can use Kotlin coroutines for tasks that need to be executed immediately.

But what if you want to defer the task, or have a long-running task that must continue to run, even if the device restarts?

### <mark style="background: #AD21D9;">Use WorkManager to schedule deferrable tasks</mark>

If you want to schedule a task to run in the background, you can use Android’s ``WorkManager`` API.

It’s designed for potentially long-running tasks that are guaranteed to run even if the user quits the app or restarts the device.

 You can even use WorkManager to run tasks when certain constraints are met, such as when WiFi is available, or chain complex tasks together.

More on https://developer.android.com/topic/libraries/architecture/workmanager