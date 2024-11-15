### <mark style="background: #AD21D9;">Motivation:</mark>

At certain points during Android development, you will be required to develop a custom view
- Not everything you will require in terms of views will be provided by the SDK
- A lot of applications will have at least one custom view in their layouts and activities

Here we will discuss the various elements that will be required to make a fully working custom view

### <mark style="background: #AD21D9;">Why Custom Views?</mark>

The reason we require custom views is that the views provided by the SDK only cover the most common items that most if not all applications require.

Standard things like buttons, radio buttons, checkboxes, edit texts, etc

If the SDK was to provide for every single case, then it would be unfeasibly large

To combat this (like all other GUI toolkits) a base view is provided which you can extend and override to produce your own views.

### <mark style="background: #AD21D9;">Methods of making a custom view:</mark>

There are three methods of constructing a custom view in android listed here along with their probability of use
- <mark style="background: #AD21D9;">Method 1:</mark> subclass an already existing view (rare)
- <mark style="background: #AD21D9;">Method 2:</mark> Compose a view out of already existing views (rare)
- <mark style="background: #AD21D9;">Method 3:</mark> Do a full custom implementation (most likely)

### <mark style="background: #AD21D9;">Method 1 - Subclass an Existing View:</mark>

A good example of this is to extend the ``NumberPicker`` class to accept minimum and maximum values through XML

Depending on behaviour required you may need very little code

Rare chance that this can be done but very little effort when it can

If you only want to add a small piece of behaviour to an already existing view that can’t be set through attributes then this is the method to use.

### <mark style="background: #AD21D9;">Method 2: Compose out of existing views</mark>

Here you would combine multiple existing views to create a more complex view.

An example of this would be creating an edit text with a clear button (users find it frustrating to clear text by hand)

Here we compose a small custom layout that defines our view. Note that when using this approach the Layout must be subclassed not a view

Like method 1 this is rare but again very little code required if this can be used

### <mark style="background: #AD21D9;">Method 3 -Full Custom Implementation:</mark>

Most common form of writing custom views Requires a lot of mathematics and working with primitives

Mainly a trial-and-error process as the display can only be verified visually. Here you require a view that is not provided by the SDK, in this case you have to take a bare view class, subclass it, and do all the operations yourself.

### <mark style="background: #AD21D9;">Requirements for a custom view:</mark>

You must provide all the drawing operations (in the ``onDraw()`` method)

You must provide all interpretation of user touches on your view (if your view uses touch)

You must provide ways and means for your view to be customisable through attributes

There are a minimum set of requirements that must be satisfied if you want your custom view to work correctly.

### <mark style="background: #AD21D9;">Constructors:</mark>

When you subclass a view, you are required to implement three constructors each have a specific use case. Assuming our class is called ``CustomView`` we have the following
- ``CustomView(Context c)``
- ``CustomView(Context c, AttributeSet as)``
- ``CustomView(Context c, AttributeSet as, int def style)``

The first constructor is used when your custom view is directly initialised from java code
- Rarely used and not recommended
- The Context attribute is the context of the activity that will own this custom view
- Allows android to build an internal visual tree to manage event handling

The second constructor is used in the case where the custom view is added in XML and is constructed with the layout inflator:
- The AttributeSet holds the list of XML attributes that the caller wishes to set on this custom view
- You may accept as many attributes as you like
- Generally, a good idea to allow customisation through attributes as makes your view flexible

The third constructor is used when the caller applies a style to views within their XML layout
- Permits your view to apply that style to itself
- To enable better integration of your custom view into an application
- Requires the most work but great custom views are completely flexible if they are to be used elsewhere

### <mark style="background: #AD21D9;">Constructors: Recommended Practice:</mark>

It is recommended that when you go to implement these constructors that all common code between them is split into a shared method
- Basic bit of code refactoring. Write once, instead of three times
- Thus if you find a mistake in common behaviour you need only fix it once
- For our purposes we will call this method ``init()``

### <mark style="background: #AD21D9;">What should init() be used for?</mark>

Should be used for all items that are shared between all three constructors

Things like initialising colours, shapes, and any parameters or data structures that are relevant to your custom view

It is a good idea to initialise and construct all the objects required by your custom view here if you can

For performance reasons as will be discussed in the next slide

### <mark style="background: #AD21D9;">Why objects should be created in init() and not onDraw()</mark>

The reason why we create in ``init()`` is that ``init()`` will only be called once, ``onDraw()`` can potentially be called up to 60 times a second

This is because most displays use a refresh rate of 60Hz

If on each ``onDraw()`` call you allocate an object you potentially have a 120 allocate/deallocate events for that object in a second

Memory management operations are expensive particularly when a garbage collector is involved

### <mark style="background: #AD21D9;">onDraw():</mark>

Every custom view you create must implement the ``onDraw()`` method

Responsible for redrawing the entire view, whenever android or your code requests it.

All drawing must be described through primitives or bitmaps

Recommended that you use primitives as they are quick to render and will scale up and down easily

### <mark style="background: #AD21D9;">onDraw() - the importance of Algebra:</mark>

This is a situation where Algebra and Linear Algebra is particularly useful.

The reason for this is that the only method we have of describing drawing operations to a computer is through the use of mathematics

You will have to come up with all sorts of formulas to position, size, and angle your components, especially if you have primitives or sets of primitives that are required to move around the view.

If you manage to describe a view accurately through algebra you will gain the following benefits
- You will get a view that will display properly on any screen, regardless of pixel density of the device or the physical screen size
- If you previously used bitmaps to implement the view then you can remove them and save space
- The component can be reused elsewhere with little to no modification required

### <mark style="background: #AD21D9;">onDraw() - primitives:</mark>

As you will be doing all the drawing you have access to a set of primitives

Things like lines, arcs, circlues, rectangles, ovals, and text

These are easy to describe mathematically. More complex shapes can be described by composing out of these simpler shapes

Along with the use of transformation operations and a matrix stack

### <mark style="background: #AD21D9;">Matrix Stack:</mark>

Part of the reason for this is that hardware acceleration is provided by OpenGL ES thus makes sense to use the same OpenGL ES model

The main used for the matrix stack is to eliminate rendering glitches that are caused by rounding errors in floating point numbers

As floating point numbers are an approximation and not a precise value

This is a stack for storing 4x4 matrices which determine the position and orientation of the drawing origin in the current view

If you were to change the position and move back by using offsets you would eventually introduce rounding errors as the position is represented by floating point numbers

By maintaining a history of the drawing origin and using copy and paste we can prevent these errors from occurring

Initially when the view is first constructed and initialised the origin of drawing is at the top left corner of the view.

### <mark style="background: #AD21D9;">Matrix Stack: Save and Restore:</mark>

The canvas provides two methods to manipulate this stack, they are ``save()`` and ``restore()``
- With save() we take a copy of the current transformation matrix and store it on the stack
- With restore() we remove the matrix on top of the stack and set that as our current transformation matrix

Take great care however to make sure that for every ``save()`` you have a corresponding ``restore()`` and vice versa

Otherwise you will get graphical glitches and possibly exceptions

### <mark style="background: #AD21D9;">Matrix Stack: Translate, Scale, and Rotate</mark>

Translate, Scale, and Rotate are the three standard methods through which the transformation matrix can be modified.

It does this by multiplying in a matrix representing the operation to the current matrix, thus the current matrix collects all modifications
- ``translate()`` move the origin of drawing by an offset. As we are doing 2D we have an offset in X and Y
- ``scale()`` allows you to draw an object larger or smaller without having to change the coordinates of your object
- ``rotate()`` allows you to rotate the drawing origin by any angle without having to change its coordinates

### <mark style="background: #AD21D9;">Invalidation:</mark>

For this we use the ``invalidate()`` method, this asks the OS to schedule a redraw of the view

Never under any circumstances call the ``onDraw()`` method directly.

If you call ``onDraw()`` you may potentially cause an infinite loop and lock up your application.

There will be times where you will internally modify the state of your view and it will need to be redrawn.

### <mark style="background: #AD21D9;">onMeasure():</mark>

Sometimes you will want to restrict the size and shape of your view. ``onMeasure()`` can be used to do this.

For example with game boards you may want ot have a square shaped view.

``onMeasure()`` will be called when android changes the size of your view. It does this to give your view a chance to reduce its pixel size should you not need the amount of pixels it is offered

Any changes made here will be reflected in your final view size

Note that it is not possible to gain extra pixels in this method

For example if you wish to make a square view in android using this method:
- You will get a width and height provided to you
- Pick whatever is the smallest dimension
- Set your width and height to be that size

### <mark style="background: #AD21D9;">onTouchEvent():</mark>

Most custom views will require some form of interaction with the user. In this environment the main method of interaction is through touch
- Your interaction with all touch is handled through the ``onTouchEvent()`` method
- Either through the use of single touch (simple)
- Or combining multiple touches together (complex)

### <mark style="background: #AD21D9;">onTouchEvent() - Single Touch:</mark>

Single touch is the easiest case as interaction here is similar to that of a pointer in a GUI such as Java Swing or Java FX. There are three main actions
- ``ACTION DOWN:`` when the touch has started
- ``ACTION MOVE:`` when the touch is being dragged along the screen in any direction
- ``ACTION UP:`` when the touch has been finished

### <mark style="background: #AD21D9;">onTouchEvent() - Multi Touch:</mark>

Multi-touch is more complex however, because the android method of touch was originally designed only to accept single touches

However, it was modified to include multi-touch while still retaining support for applications using single touch, thus we have two new actions
- ``ACTION POINTER DOWN:`` for when an additional touch is added
- ``ACTION POINTER UP:`` for when an additional touch is removed

note that ``ACTION MOVE`` is still used to indicate movement

### <mark style="background: #AD21D9;">Integration - layouts:</mark>

It is possible to include your custom views in layouts by adding them into XML layout files

Because your view is not one provided by the SDK you must provide the fully qualified class name of the java file containing the view

`< package > . < class >`

### <mark style="background: #AD21D9;">Integration - Attributes:</mark>

The ``AttributeSet`` class is useful here as it divides attributes into namespaces

So, for example the attribute ``foo:bar`` would have a namespace of foo with an attribute name of bar. Attributes without namespaces have a null namespace

It is also possible to make your view understand attributes to make them more flexible.

### <mark style="background: #AD21D9;">Integration - Event Handlers:</mark>

Finally, if you are considering releasing your custom view for others to use you may wish to implement event handlers and event listeners
- Prevents the need for other developers to access your source code
- Gives them the minimum required effort to integrate your view into their own application
- Won’t cover here but easy enough to implement