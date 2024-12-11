Most apps require more than one screen

So far, we’ve just looked at how to create single-screen apps. This is fine for simple applications

What about more complex apps?

### <mark style="background: #AD21D9;">Fragments:</mark>

Introduced in Android 3.0

Gives the developer more control

Allows for greater flexibility in dealing with different screen sizes

Designed to create UI reusability

![](https://i.imgur.com/KktqWYG.png)

Designed to create a more dynamic / flexible design environment for large android devices such as Tablets.

With the development of larger/high density screens for android phones such, they have begun to be used for many apps, that want to support smaller and larger screens with content that can adapt automatically to screen size, beyond the standard android resource model.

<mark style="background: #AD21D9;">A fragment is:</mark>
- like a kind of subactivity that’s displayed inside an activity’s layout.
- It has Java/Kotlin code that controls its behavior, and an associated layout that defines its appearance.
- Fragments can't live on their own. They must be hosted by an activity or another fragment.

<mark style="background: #AD21D9;">While your activity is in the STARTED lifecycle state or higher:</mark>
- fragments can be added, replaced, or removed.
- And you can keep a record of these changes in a back stack that is managed by the activity, so that the changes can be reversed.

### <mark style="background: #AD21D9;">Creating a fragment:</mark>

Similar to creating an Activity, you create a subclass of Fragment

Its call back methods mirror Activity but you should implement the following methods
- ``onCreate()``: Initialise the components of the fragment page
- ``onCreateView()``: This is where you create the UI and return it as a view object
- ``onPause()``: Commit any changes. Pause/ release any resources that you are using

```Kotlin
class ExampleFragment : Fragment(R.layout.example_fragment)
```

### <mark style="background: #AD21D9;">Fragment lifecycle:</mark>

Can be downward and upward as well.

``OnCreateView()`` is the method in which we can inflate our view

We can only reference the view components ``onViewCreated()``

![](https://i.imgur.com/1NhQ2a2.png)

### <mark style="background: #AD21D9;">Fragment within an Activity Layout:</mark>

To display a fragment, you need to add it to an activity’s layout.

You add a fragment to a layout using a ``<fragment>`` tag.

You specify which fragment you want to display by setting the ``android:name`` attribute to the fully qualified fragment name, including its package.

Think of the ``<fragment>`` as a placeholder for where the fragment’s layout should be inserted

### <mark style="background: #AD21D9;">Example of a Fragment setup in a layout xml file:</mark>

```Kotlin
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
	android:orientation="horizontal"
	android:layout_width="match_parent"
	android:layout_height="match_parent"
>
	
	<fragment android:name="com.example.news.ArticleListFragment"
		android:id="@+id/list"
		android:layout_weight="1"
		android:layout_width="0dp"
		android:layout_height="match_parent" 
	/>
	
	<fragment android:name="com.example.news.ArticleReaderFragment"
	android:id="@+id/viewer"
	android:layout_weight="2"
	android:layout_width="0dp"
	android:layout_height="match_parent" 
	/>
</LinearLayout>
```

### <mark style="background: #AD21D9;">Fragment within an Activity Layout:</mark>

The use of ``<fragment>`` tag is suitable only for static fragments

What if the activity has multiple fragments to switch between them?

Then, a container should be used, usually a ``<frameLayout>`` tag is used to reserve a place for multiple fragments.

```XML
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
	android:orientation="horizontal"
	android:layout_width="match_parent"
	android:layout_height="match_parent"
>
	<frameLayout
		android:id="@+id/fargmentFrame"
		android:layout_weight="1"
		android:layout_width="0dp"
		android:layout_height="match_parent" 
	/>
</LinearLayout>
```

### <mark style="background: #AD21D9;">Managing Fragments:</mark>

``FragmentManager`` is the class responsible for performing actions on your app's fragments, such as adding, removing, or replacing them and adding them to the back stack.

Calling it by using ``getFragmentManager()``

You can then find your fragment by tag or ID
- ``findFragmentById()``
- ``findFragmentByTag()``

You can pop fragments directly off the back stack or register a listener to monitor such changes.
- ``popBackStack()``
- ``addOnBackStackChangedListener()``

### <mark style="background: #AD21D9;">Fragment Transactions:</mark>

Fragments are great to setup applications where you may want multiple windows , but if you are on a smaller screen, how do you swap between fragments.

This is achieved by <mark style="background: #AD21D9;">Fragment Transactions</mark>

First an instance of ``FragmentTransaction`` must be gotten from the <mark style="background: #AD21D9;">Fragment Manager</mark>.

```Kotlin
FragmentManager fragmentManager = getFragmentManager();

FragmentTransaction fragmentTransaction = fragmentManager.beginTransaction();
```

Once you have the transaction object, you can call
- ``add(), remove() or replace()``

But you must ``commit()`` before anything will happen , for example

```Kotlin
// Create new fragment and transaction
Fragment newFragment = new ExampleFragment();
FragmentTransaction transaction = getFragmentManager().beginTransaction();
// Replace whatever is in the fragment_container view with this fragment,
// and add the transaction to the back stack
transaction.replace(R.id.fragment_container, newFragment);
transaction.addToBackStack(null);
// Commit the transaction
transaction.commit();
```

### <mark style="background: #AD21D9;">Fragments communicating with its host Activity:</mark>

A fragment can get a reference to the activity that is hosting it by call ``getActivity()`` method , for example :

```Kotlin
View listView = getActivity().findViewById(R.id.list);
```

Alternatively an Activity can gain access to the fragment is running by calling.

```Kotlin
ExampleFragment fragment = 
(ExampleFragment) getFragmentManager().findFragmentById(R.id.example_fragment);
```

### <mark style="background: #AD21D9;">Notes:</mark>

Fragments don’t have a findViewById() method

<mark style="background: #AD21D9;">The Fragment class isn’t a subclass of Activity.</mark>

Even though fragments have a lot in common with activities, the Fragment class doesn’t extend Activity so it doesn’t inherit any of its methods.

Instead, the Fragment class defines its own set of methods.

While many of these look identical to the ones that activities inherit, it doesn’t include methods like ``findViewById()``.

### <mark style="background: #AD21D9;">Summary:</mark>

A fragment has Java/Kotlin code and a layout.

Every fragment extends the Fragment class or one of its subclasses.

Add a fragment statically to an activity’s layout using a ``<fragment>``, or dynamically using a ``<frameLayout>`` placeholder.

``onCreateView()`` gets called each time Android needs the fragment’s layout.

The Fragment class doesn’t extend Activity.

Fragments don’t have a ``findViewById()`` method