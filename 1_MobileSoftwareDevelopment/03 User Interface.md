### <mark style="background: #AD21D9;">View System:</mark>

The Java API Framework comes with a <mark style="background: #AD21D9;">built-in</mark> View System

![](https://i.imgur.com/xi2GllC.png)

<mark style="background: #AD21D9;">Examples:</mark>
If you look at your mobile device, every <mark style="background: #AD21D9;">User Interface</mark> element that you see is a <mark style="background: #AD21D9;">View</mark>.

![](https://i.imgur.com/TUpgiRR.png)

![](https://i.imgur.com/VXUO3bi.png)

### <mark style="background: #AD21D9;">What is a View?</mark>

<mark style="background: #AD21D9;">View subclasses are basic User-Interface building blocks</mark>  
- Display text (``TextView`` class), Edit text (``EditText`` class)  
- Buttons (``Button`` class), ``menus``, other controls  
- Scrollable (``ScrollView``, ``RecyclerView``)  
- Show images (``ImageView``)  
- Group views (``ConstraintLayout`` and ``LinearLayout``)

<mark style="background: #AD21D9;">Button:</mark>
- <mark style="background: #AD21D9;">View</mark> that responds to <mark style="background: #AD21D9;">tapping</mark> (clicking) or pressing  
- Usually text or visuals indicate what will happen when tapped

![](https://i.imgur.com/QSUhO4v.png)

<mark style="background: #AD21D9;">EditText:</mark>
- ``EditText`` default lines of text  
- Alphanumeric Keyboard  
- Suggestions appear  
- Tapping <mark style="background: #AD21D9;">Return</mark> key starts new line  
- Set in Attributes pane of Layout Editor

![](https://i.imgur.com/CyfczOL.png)

<mark style="background: #AD21D9;">Messages:</mark>
- Single line of text  
- ``android:inputType =  “textShortMessage”``  
- Tapping Emoticons key changes keyboard to emoticons 
- Tapping ``Done`` key advances focus to next View

![](https://i.imgur.com/B48TPeh.png)

<mark style="background: #AD21D9;">Phone Numbers:</mark>
- For phone number entry  
- ``android:inputType = “phone”``  
- Numeric keypad (numbers only)  
- Tapping Done key advances focus to next View

![](https://i.imgur.com/iC4RJ0X.png)

<mark style="background: #AD21D9;">Dates:</mark>
- For date entry  
- ``android:inputType = “date”``  
- Numeric keypad (numbers only)  
- Tapping ``Done`` key advances focus to next View  
- Note prominence of <mark style="background: #AD21D9;">backslash</mark> /
![](https://i.imgur.com/Hlmxvo2.png)

### <mark style="background: #AD21D9;">Input types:</mark>

``textCapCharacters:`` Set to ALL CAPITAL LETTERS  

``textPassword:`` Conceal an entered p******d  

``number:`` <mark style="background: #AD21D9;">Restrict</mark> text entry to numbers  

``textEmailAddress:`` Show keyboard with @ conveniently located  

``datetime:`` Show a numeric keypad with a slash and colon for entering the date and time.

<mark style="background: #AD21D9;">CheckBox:</mark>
- User can select <mark style="background: #AD21D9;">any</mark> number of choices  
- Checking one box does <mark style="background: #AD21D9;">not</mark> uncheck another  
- Users expect checkboxes in a <mark style="background: #AD21D9;">vertical</mark> list  
- Commonly used with a <mark style="background: #AD21D9;">Submit</mark> button

![](https://i.imgur.com/M3zvWej.png)

<mark style="background: #AD21D9;">RadioButton:</mark>
- Put ``RadioButton`` elements in a ``RadioGroup`` in a vertical list (horizontally if labels are short)  
- User can select <mark style="background: #AD21D9;">only one</mark> of the choices  
- Checking one <mark style="background: #AD21D9;">unchecks</mark> all others  
- Commonly used with a Submit button for the ``RadioGroup``

<mark style="background: #AD21D9;">Toggle Buttons / Switches:</mark>
- User can switch between On and Off

![](https://i.imgur.com/R068m5Q.png)

### <mark style="background: #AD21D9;">Custom Views:</mark>

Over 100 different types of Views available from the Android system, all <mark style="background: #AD21D9;">children</mark> of the ``View`` class  

If necessary, ``create custom views`` by <mark style="background: #AD21D9;">subclassing</mark> existing views or the ``View`` class itself

<mark style="background: #AD21D9;">View Attributes:</mark>
- Every ``View`` and ``ViewGroup`` object supports their own set of attributes.  
- Some attributes are specific to a ``View`` object e.g. ``TextView`` supports the ``textSize`` attribute.  
- Some are common to all ``View`` objects, because they are inherited from the root View class e.g. the ``id`` attribute.

<mark style="background: #AD21D9;">Create Views and Layouts:</mark>
1. Android Studio Layout Editor: visual representation of XML  
2. XML Editor  
3. Kotlin/Java code

![](https://i.imgur.com/V92JEiB.png)

<mark style="background: #AD21D9;">ViewGroup and View hierarchy:</mark>

![](https://i.imgur.com/v3FjmKp.png)

<mark style="background: #AD21D9;">Scroll View:</mark>
- Allows ``View`` placed within it be scrolled.  
- Only 1 direct child placed within it.  
- To add multiple views make the direct child a view group e.g. ``LinearLayout``.  
- Supports <mark style="background: #AD21D9;">vertical</mark> scrolling only.

![](https://i.imgur.com/XX8AfBV.png)

<mark style="background: #AD21D9;">Recycler View:</mark>
- If your app needs to display a scrolling list of elements based on large data sets (or data that frequently changes).  
- Replacement for older ListView.

![](https://i.imgur.com/p5pJVkc.png)

- Cards provide an easy way to contain a group of views while providing a consistent style for the container.  
- Lists of these cards can then be displayed in a Recycler View.

![](https://i.imgur.com/TInnBh3.png)

### <mark style="background: #AD21D9;">ViewGroups for Layouts:</mark>

<mark style="background: #AD21D9;">Layouts:</mark>  
- Are specific types of ViewGroups (subclasses of ViewGroup)  
- Contain child views  
- Can be in a row, column, grid, table, absolute

### <mark style="background: #AD21D9;">Common Layout Classes:</mark>

![](https://i.imgur.com/98yK5Ta.png)

<mark style="background: #AD21D9;">Linear Layout:</mark>
- Aligns all children in a <mark style="background: #AD21D9;">single</mark> direction, vertically or horizontally.  
- Specify layout direction with <mark style="background: #AD21D9;">orientation</mark> attribute.  
- Vertical list will only have 1 child per row.  
- Respects margins between children and <mark style="background: #AD21D9;">gravity</mark> (alignment) of each child.

![](https://i.imgur.com/GnKAsKf.png)

<mark style="background: #AD21D9;">Relative Layout:</mark>

Displays child view in a relative position  

The position of each view can be relative to the sibling, (like on the left or below another view)  

Or relative to the position of the main area of the relative layout, like bottom, left, or centre.

![](https://i.imgur.com/DrRVufz.png)

<mark style="background: #AD21D9;">Constraint Layout:</mark>
- Create large and complex layouts with a flat view hierarchy (no nested view groups).  
- Laid out according to relationships between sibling views and the parent layout.  
- Layout Editor specially built for it.  
- Drag and drop v's XML editing

![](https://i.imgur.com/QXjZwMd.png)

![](https://i.imgur.com/Ypb9BLD.png)

[Constraint video](https://www.youtube.com/watch?v=XamMbnzI5vE)

<mark style="background: #AD21D9;">Grid Layout:</mark>
- A layout that places its children in a rectangular grid.  
- The grid separates the viewing area into cells.  
- Children occupy one or more contiguous cells

![](https://i.imgur.com/5GczcU9.png)

<mark style="background: #AD21D9;">Table Layout:</mark>
- Arranges children into rows and columns.  
- Consists of ``TableRow`` objects, each defining a <mark style="background: #AD21D9;">row</mark> of 0 or more cells.  
- A cell can hold one View object.  
- Has as many <mark style="background: #AD21D9;">columns</mark> as row with most cells.

![](https://i.imgur.com/AjerqEu.png)

### <mark style="background: #AD21D9;">Class and Layout Hierarchies:</mark>

View class-hierarchy is standard <mark style="background: #AD21D9;">object-oriented</mark> class Inheritance  
- For example, ``Button`` is-a ``TextView`` is-a ``View`` is-an ``Object``  
- Superclass-subclass relationship  

Layout hierarchy is how Views are visually arranged  
- ``LinearLayout`` can <mark style="background: #AD21D9;">contain</mark> Buttons arranged in a row  
- Parent-child relationship

<mark style="background: #AD21D9;">Hierarchy of Viewgroups/Views:</mark>
- Root View is always a <mark style="background: #AD21D9;">ViewGroup</mark>

![](https://i.imgur.com/x1dlF9G.png)

<mark style="background: #AD21D9;">View hierarchy and screen layout:</mark>

![](https://i.imgur.com/79aedpq.png)

### <mark style="background: #AD21D9;">In the Layout editor:</mark>

![](https://i.imgur.com/XOttGVA.png)

![](https://i.imgur.com/cA9yCDi.png)

### <mark style="background: #AD21D9;">Layout created in XML</mark>

```XML
<LinearLayout  
	android:orientation="vertical"  
	android:layout_width="match_parent"  
	android:layout_height="match_parent">  
	
	<Button  
	... />  
	<TextView  
	... />  
	<Button  
	... />  
</LinearLayout>
```

### <mark style="background: #AD21D9;">Note:</mark>

Context is an interface to global information about an application environment  

Get the context:  
``Context context = getApplicationContext();``  

An Activity is its own context:  
``TextView myText = new TextView(this);``

<mark style="background: #AD21D9;">Best Practices:</mark>
- Arrangement of View hierarchy affects app performance  
- Use smallest number of simplest views possible  
- Keep the hierarchy flat i.e. limit nesting of views and view groups

### <mark style="background: #AD21D9;">Resources:</mark>
- Separate static data from code in your layouts.  
- Strings, dimensions, images, menu text, colours, styles  
- Useful for localisation

The API Framework allows us easily use app Resources.

![](https://i.imgur.com/cagJMFL.png)

![](https://i.imgur.com/ehEHj5o.png)

### <mark style="background: #AD21D9;">Drawables:</mark> 

Drawable—generic Android class used to represent any kind of graphic.  

Bitmaps e.g. PNG (.png), JPG (.jpg), or GIF (.gif) format.  

Vector Graphics, scale smoothly for all screen sizes e.g. defined in XML.

![](https://i.imgur.com/B3ZiCZj.png)

### <mark style="background: #AD21D9;">What is a Style?</mark>

Collection of <mark style="background: #AD21D9;">attributes</mark> that define the <mark style="background: #AD21D9;">visual appearance of a View</mark>  

Reduce <mark style="background: #AD21D9;">duplication</mark>  

Make code more <mark style="background: #AD21D9;">compact</mark>  

Manage visual appearance of many components with one style

### <mark style="background: #AD21D9;">Styles Reduce Clutter:</mark>

```XML
<TextView  
	android:layout_width="match_parent"  
	android:layout_height="wrap_content  
	android:textColor="#00FF00"  
	android:typeface="monospace"  
	android:text="@string/hello" 
/>  
<TextView  
	style="@style/CodeFont"  
	android:text="@string/hello"  
/>
```

### <mark style="background: #AD21D9;">Defined in styles.xml</mark>

``styles.xml`` is in ``res/values``

```SQL
<resources>  
	<style name="CodeFont">  
		<item name="android:textColor">#00FF00</item>  
		<item name="android:typeface">monospace</item>  
	</style>  
</resources>
```

### <mark style="background: #AD21D9;">Inheritance: Parent</mark>

Define a parent style...

```XML
<resources>  
	<style name="CodeFont">  
		<item name="android:layout_width">match_parent</item>  
		<item name="android:layout_height">wrap_content</item>  
		<item name="android:textColor">#00FF00</item>  
		<item name="android:typeface">monospace</item>  
	</style>  
</resources>
```

### <mark style="background: #AD21D9;">Inheritance: Define Child:</mark>

Define child with Codefont as parent

```XML
<resources>  
	<style name="RedCode" parent="@style/Codefont">  
		<item name="android:textColor"> #FF0000 </item>  
	</style>  
</resources>
```

### <mark style="background: #AD21D9;">Themes:</mark>

A Theme is a style applied to an entire activity or even the entire app  

Themes are defined in styles.xml and may be customised  

```XML
<style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">  
<!-- Customise your theme here. -->  
	<item name="colorPrimary">@color/colorPrimary</item>  
	<item name="colorPrimaryDark">@color/colorPrimaryDark</item>  
	<item name="colorAccent">@color/colorAccent</item>  

</style>
```

### <mark style="background: #AD21D9;">Colours:</mark>

A colour value can be defined in XML.  

The colour is specified with an RGB value and alpha channel.  

You can use a colour resource any place that accepts a hexadecimal colour value.  

Value always begins with # character and then the Alpha-Red-Green-Blue info e.g. ``#RGB``

<mark style="background: #AD21D9;">Colour Example:</mark>
```XML
<resources>  
	<color name="colorPrimary">#008577</color>  
	<color name="colorPrimaryDark">#00574B</color>  
	<color name="colorAccent">#D81B60</color>  
</resources>
```

### <mark style="background: #AD21D9;">Strings:</mark>

<mark style="background: #AD21D9;">Strings.xml:</mark>

```XML
<resources>  
	<string name="hello">Hello!</string>  
</resources> 
```

<mark style="background: #AD21D9;">Layout:</mark>
```XML  
<TextView  
	android:layout_width="fill_parent"  
	android:layout_height="wrap_content"  
	android:text="@string/hello"  
/>
```

### <mark style="background: #AD21D9;">Refer to resources in code:</mark>

```XML  
XML: @drawable/filename  
<ImageView  
	android:layout_height="wrap_content"  
	android:layout_width="wrap_content"  
	android:src="@drawable/myimage"/>  
```

```Java
Java: R.drawable.filename  

Resources res = getResources();  
Drawable drawable = res.getDrawable(R.drawable.myimage);
```

<mark style="background: #AD21D9;">Layout:</mark>
```Kotlin
setContentView(R.layout.activity_main);
```

<mark style="background: #AD21D9;">View:</mark>
```Kotlin
rv = (RecyclerView) findViewById(R.id.recyclerview);
```

<mark style="background: #AD21D9;">String:</mark>
```Java
//Java
R.string.title
```

```XML
android:text="@string/title"
```

1. Get a EditText object for the EditText View  
```Kotlin
EditText simpleEditText = findViewById(R.id.edit_simple);
```  
2. Retrieve the CharSequence and convert it to a string  
```Kotlin
String strValue =  simpleEditText.getText().toString();
```

### <mark style="background: #AD21D9;">Measurements:</mark>

Devices have different screen sizes (handsets, tablets, TVs...)  

Different pixel sizes e.g. 160 or 480 per square inch.  

If you don't consider this, system might:  
- Scale your images (resulting in blurry images).  
- Images might appear at the completely wrong size.

A View defined as  "100px" wide will appear much larger on the left device.

![](https://i.imgur.com/8a4caoN.png)

For good graphics quality across devices, provide multiple versions of each bitmap in your app.

![](https://i.imgur.com/L9uaxre.png)

<mark style="background: #AD21D9;">dp:</mark>
- 1 dp is a virtual pixel unit, roughly equal to 1 pixel on a medium-density screen (160dpi; the "baseline" density).  
- Android translates dps to the number of real pixels for each other density using this formula:  
- ``px = dp * (dpi / 160)``

<mark style="background: #AD21D9;">sp:</mark>
- When defining text sizes you should instead use scalable pixels (sp) as your units (but never use sp for layout sizes).  
- The sp unit is the same size as dp, by default, but it resizes based on the user's preferred text size.

<mark style="background: #AD21D9;">Guidelines:</mark>
- Density-independent Pixels (dp): for Views  
- Scalable Pixels (sp): for text  

<mark style="background: #AD21D9;">Don't use device-dependent or density-dependent units:</mark>  
- Actual Pixels (px)  
- Actual Measurement (in, mm)  
- Points - typography 1/72 inch (pt