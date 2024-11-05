### <mark style="background: #AD21D9;">What is a list view?:</mark>

A <mark style="background: #AD21D9;">ViewGroup</mark> that displays scrollable items

![](https://i.imgur.com/O5BuZnL.png)

![](https://i.imgur.com/ReiW8kR.png)

<mark style="background: #AD21D9;">Three Parts of a ListView:</mark>
- The ``ListView`` itself (aka a ``ViewGroup``)  
- List items (Each row/item in the list. Each item is a layout consisting of a View or ``ViewGroup``.)  
- Data for each item

### <mark style="background: #AD21D9;">ListItem:</mark>

Since the ``ListItem`` can be a ``ViewGroup``, we have the power to display very simple or extremely complex layouts for each item.  
- A ``TextView``  
- A ``TextView`` and ``ImageView``  
- A ``TextView`` and ``CheckBox``  
- A ``TextView`` and ``Button``  
- A ``TextView``, ``ImageView``, ``CheckBox``, ``Button``, and ``RatingBar``, etc

### <mark style="background: #AD21D9;">Where does the Data come from?</mark>

``ListViews`` receive data via <mark style="background: #AD21D9;">Adapters</mark>.  

The <mark style="background: #AD21D9;">Adapter</mark> behaves as the middleman between the data source and the ``ListView``.

<mark style="background: #AD21D9;">The job of an Adapter:</mark>  
- The <mark style="background: #AD21D9;">Adapter</mark> fetches data from the source.  
- Creates the layout that represents each list item.  
- Takes the data fetched from the source places it into the list item layout.  
- Returns a list item to the ``ListView``.

### <mark style="background: #AD21D9;">How an adapter works:</mark>

```Kotlin
Array<String> mMovies = { "Inception", "Spider Man", "Shawshank Redemption", "Fast and Furious",  "The Terminal" }
```

![](https://i.imgur.com/Oernst8.png)

<mark style="background: #AD21D9;">Data source for Adapters:</mark>
1. Arrays  
2. Content Provider - Used to get Calendar and Contact info from phone.  
3. Database Cursor

### <mark style="background: #AD21D9;">Types of Adapters:</mark>

<mark style="background: #AD21D9;">ArrayAdapter:</mark>  
- Works with Arrays  
- Can handle any Java Object as input  
- Uses the ``.toString()`` method of the ``JavaObject`` to obtain text for list item.  

<mark style="background: #AD21D9;">SimpleCursorAdapter:</mark>  
- Works with a Content Provider and Database Cursor

### <mark style="background: #AD21D9;">AdapterView:</mark>

``ListView`` derives from ``AdapterView``  

``AdapterViews`` are Views that use Adapters.  

There are several other ``AdapterView`` subclasses that behave much like ``ListView``.

<mark style="background: #AD21D9;">Subclasses of AdapterView:</mark>
1. AdapterViewFlipper  
2. GridView  
3. Spinner  
4. Gallery  
5. StackView  
6. ExpandableListView

### <mark style="background: #AD21D9;">Modifying your List:</mark>

<mark style="background: #AD21D9;">How do I add more items?</mark>  
``add(T Object)`` – Adds the specified object to the end  of the array.  

<mark style="background: #AD21D9;">How can I add a set of items?</mark>  
``addAll(T... items)`` – Adds the specified items at the end of the array.  

<mark style="background: #AD21D9;">How do I clear all items?</mark>  
``clear()`` – Remove all elements from the list

![](https://i.imgur.com/0A6bvdy.png)

### <mark style="background: #AD21D9;">ListActivity:</mark>

Useful when your Activity only supports a <mark style="background: #AD21D9;">single</mark> list.  

``ListActivity`` was designed to simplify the handling of ``ListViews``.

<mark style="background: #AD21D9;">Standard ListActivity:</mark>
- ``ListActivity`` has a default layout that consists of a single full-screen list in the centre of the screen.  
- ``ListActivity`` does not require that you assign it a layout resource via ``setContentView()``. ``ListActivity`` handles that for you.

<mark style="background: #AD21D9;">Custom ListActivity:</mark>
- If you want to include more views than just a ``ListView`` in your Activity, you may call ``setContentView()`` yourself with your own layout.  
- In this case, your layout <mark style="background: #AD21D9;">MUST</mark> contain a ``ListView`` with the ``android:id`` attribute  set to ``@android:id/list``

<mark style="background: #AD21D9;">ListActivity helper methods:</mark> 
- List Item Click events  
- Setting the ``ListView``’s adapter

<mark style="background: #AD21D9;">ListActivity click handling:</mark>
- When using a ``ListActivity``, you don’t need to implement an ``onItemClickListener()``.  
- ``ListActivity`` already implements one for you.  
- Simply @Override ``ListActivity``’s ``onListItemClick()`` to handle list click events.

<mark style="background: #AD21D9;">Setting the ListView's adapter with ListActivity:</mark>
- ``ListActivity`` provides the ``setListAdapter()`` method.  
- Internally calls ``setAdapter()`` on the ``ListView`` for the ``ListActivity``

<mark style="background: #AD21D9;">Initial impression of ListView:</mark>
- The ListView probably creates a view for each list item and only displays the item currently on screen.

<mark style="background: #AD21D9;">Example:</mark>

```Kotlin
Array<String> mMovies = { "Bill and Ted's Excellent Adventures", "Teen Wolf", "Honey I shrunk the kids","Texas Chainsaw Massacre", "Puppet Master", "Land Before Time", "TMNT", "Weird Science", "Goonies", "Total Recall", "Howard the duck", "Kindgergarden Cop", "Bloodsport", "Universal Soldier", "Ernest scared stupid", "Dumb and Dumber", "Breakfast Club" };
```

![](https://i.imgur.com/WeIEt08.png)

![](https://i.imgur.com/4hHmA9W.png)

<mark style="background: #AD21D9;">ListView recycles its items:</mark>
- To cut down on View Objects, a ``ListView`` will only allocate enough Item Views to “roughly” fill the size of a ``ListView``. 
- When an item gets scrolled off the ``ListView``, its view will be reused by a new Item that is scrolling on to the ``ListView``.
![](https://i.imgur.com/NaYjeZo.png)


<mark style="background: #AD21D9;">ListView Recylcing:</mark>
- Automatically taken care of by the ``ListView`` when using a standard ``ArrayAdapter``.  
- However, if you implement your own Adapter you’ll have to do a little work.

### <mark style="background: #AD21D9;">Adapters:</mark>

Lets look at how the ``ArrayAdapter`` class does the following:  
1. Creates list item Views  
2. Recycles list item Views

### <mark style="background: #AD21D9;">How an adapter works:</mark>

```Kotlin
Array<String> mMovies = { "Bill and Ted's Excellent Adventures", "Teen Wolf", "Honey I shrunk the kids", "Texas Chainsaw Massacre", "Puppet Master" }
```

![](https://i.imgur.com/jYnO4jA.png)

![](https://i.imgur.com/ixlx7cK.png)

![](https://i.imgur.com/pxr4yKu.png)

![](https://i.imgur.com/FtJFByg.png)

![](https://i.imgur.com/Gwr9PJT.png)

### <mark style="background: #AD21D9;">Implementing your own adapter:</mark>

The default look and feel of the Android ``ListView`` is not very attractive.  

Also, remember the default action of an ``ArrayAdapter`` is to call the ``toString()`` method on the data object it contains.  

This means your list will change the text on the list item and nothing else.

<mark style="background: #AD21D9;">Getting creative with Custom Adapters:</mark>  
- With Custom Adapters, you can use your own layout to make lists more interesting.  
- You can make the list items look any way you want.  
- You can make the list item have more data than just simple text.

<mark style="background: #AD21D9;">Steps for create a custom adapter:</mark>  
1. Extend an existing Adapter class  
2. Define a constructor  
3. @Override the Adapter’s ``getView()`` method.  
	- Use this to inflate custom list items  
	- Use this to populate the item with more data than just what comes from ``toString()``

<mark style="background: #AD21D9;">Extend an existing Adapter:</mark>
- Create a class that extends  
	1. BaseAdapter  
	2. ArrayAdapter  
	3. SimpleCursorAdapter  
- You’ll want to extend an existing adapter because they provide quite a bit of  functionality that we don’t want to rewrite ourselves.

### <mark style="background: #AD21D9;">Recycler view overview:</mark>

Recycler view is a robust list drawing library that provides a fixed size window we can use to load a large dataset into.  

It recycles the views it creates as we scroll (or the views go out of scope) and then if there is a need, it reuses them to make it seem as if the views were never offloaded.  

They appear to the user to be present outside the window.  

This makes Recycler view exceptional for displaying data collections whose elements change at runtime based on user action or network events.

``RecyclerView`` supports three types of lists using ``RecyclerView.LayoutManager``.  
- ``StaggeredGridLayoutManager``  
- ``GridLayoutManager``  
- ``LinearLayoutManager``

``RecyclerViews`` are generally used to show a scrolling list of items in either a list or grid format.  

As items in a list or grid can look different in different applications or even in different activities belonging to the same application.  

You’ll be required to not only add in a recycler view but also to tell the recycler view how to add in and display items.  

``RecyclerViews`` take a bit of work to get up and running because of this but they are highly flexible and adaptable as a result.