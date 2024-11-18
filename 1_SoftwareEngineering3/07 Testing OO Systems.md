### <mark style="background: #FFB8EBA6;">Introduction:</mark>

<mark style="background: #FFB8EBA6;">Testing conventional structured software use strategies:</mark>  
- Top down  
- Bottom up  
- White box  
- Black Box  

<mark style="background: #FFB8EBA6;">Top down and bottom up do not apply to the architecture of OO:</mark>  
- The architecture of OO software is a network of   collaborating classes.  
- Therefore it is necessary to test an OO system at a variety of different levels in an effort to uncover errors that may occur as classes collaborate with one another and the subsystems communicate across architectural layers.

### <mark style="background: #FFB8EBA6;">Approach to testing OO systems:</mark>

While black box and white box strategies are applied to OO systems as to conventional structured systems the <mark style="background: #FFB8EBA6;">tactics</mark> are different.  

As a class evolves through analysis and design to the coded stage, it becomes a target for <mark style="background: #FFB8EBA6;">test case design</mark>.  

Once classes are coded, a series of tests are designed that exercise class operations and examine whether errors exist as objects of one class collaborates with those of other classes.  

Attributes and operations are <mark style="background: #FFB8EBA6;">encapsulated</mark>  

Encapsulation produces test obstacles such as the reporting of the attribute values.  

<mark style="background: #FFB8EBA6;">Inheritance leads to additional challenges:</mark>  
- each level in the hierarchy produces a new context/environment of usage and requires retesting of the class at each level.  
- Each subclass in its own domain will require it’s own specific test cases.

White box testing can be applied to individual operations in isolation but the effort is sometimes better applied to these tests at the class level.  

Black box testing is also appropriate to OO and the Use Case is a natural source of the test case.

### <mark style="background: #FFB8EBA6;">Testing OO Analysis and Design Models:</mark>

Because OO analysis and design models align more closely in structure and content to the resultant OO software, testing can begin with a <mark style="background: #FFB8EBA6;">review of these models</mark>.  

<mark style="background: #FFB8EBA6;">These models iteratively evolve</mark> from informal representations of system requirements to detailed models of classes, attributes, operations, associations, messages and sequencing, events ..  

Therefore problems that are <mark style="background: #FFB8EBA6;">detected</mark> in these <mark style="background: #FFB8EBA6;">properties</mark> at the <mark style="background: #FFB8EBA6;">early iteration stages</mark> of <mark style="background: #FFB8EBA6;">analysis</mark> and <mark style="background: #FFB8EBA6;">design</mark> stage will circumvent problems at the later stages of development.  

Technical reviews of these models are considered as important as final testing

<mark style="background: #FFB8EBA6;">Correctness of OOA and OOD Models:</mark>  
- Syntactic Correctness: The notation and syntax should conform to the methodology  
- Semantic Correctness: The model is examined by expert users (domain experts) to check if it conforms to the real world problem as specified in use cases.

<mark style="background: #FFB8EBA6;">Consistency of OOA and OOD Models:</mark>  
- This involves cross-checking the class diagram with the detailed use-case descriptions, object collaboration diagram/interaction sequence diagrams and state transition diagrams to ensure that the associations and collaborations and responsibilities are consistent.

### <mark style="background: #FFB8EBA6;">Test Cases and the Class Hierarchy:</mark>

Inheritance does not remove the need to test all derived classes.  

Example:  
Class Derived redefines ``redefined()`` to serve in a local context.  

``Derived::redefined()`` must also be tested but does ``Derived::inherited()`` need to be tested?  

If ``Derived::inherited()`` calls ``Derived::redefined()`` then ``Derived::inherited()`` could misuse the new behaviour of ``Derived::redefined()`` and therefore must be tested as part of Derived.

![](https://i.imgur.com/z287VBd.png)

``Base::redefined()`` and ``Derived::redefined()`` are different as each implements different requirements and therefore require a separate set of test cases.  

The similarities in the operation will lead to similarities in the test cases.  

The better the OO design, the better the overlap in the inherited features.  

New test will be required only for the <mark style="background: #FFB8EBA6;">additional</mark> ``Derived::redefined()`` requirements.

### <mark style="background: #FFB8EBA6;">Test Cases for a Class:</mark>

The test should drive a selection of objects from the class through its states and for each test, the following characteristics should be tested for
- List of states for the class
- List of messages / operations invoked
- List of exceptions occurring

### <mark style="background: #FFB8EBA6;">Class/Unit Testing:</mark>

The classical strategy for testing structured software is <mark style="background: #FFB8EBA6;">unit testing</mark> (smallest indivisible module, subroutine etc.) leading progressively up to integration testing

These tests require regression testing to check for the effects of adding new components, major bug fixes, finishing with system testing and validation.  

In an OO context, <mark style="background: #FFB8EBA6;">encapsulation</mark> of <mark style="background: #FFB8EBA6;">attributes</mark> and <mark style="background: #FFB8EBA6;">operations</mark> into a class dictates that a class should be tested as an indivisible unit in conjunction with other collaborating classes.

Testing the operationX() in isolation may not uncover the subtle differences that it encounters with the environment of each subclass and the private attributes of its  
environment.  

Class testing is driven by the operations and attributes encapsulated within the class along with the state behaviour.

![](https://i.imgur.com/nqsY8gC.png)

### <mark style="background: #FFB8EBA6;">Scenario-Based Test Design:</mark>

Scenario-based testing concentrates on what the user does (rather than what the built product does).  

This means capturing the tasks (<mark style="background: #FFB8EBA6;">via use-cases</mark>) that the user has to perform, then applying them and their variants as tests. (essentially <mark style="background: #FFB8EBA6;">black box</mark>)

### <mark style="background: #FFB8EBA6;">Integration Testing:</mark>

Because OO software does not consist of a hierarchy of program modules as in classical structured design, top down and bottom up testing is not applicable.  

Further, adding operations one at a time and testing the class after each addition (incremental testing) can sometimes be ruled out due to the complexity of the collaborations required.

### <mark style="background: #FFB8EBA6;">Thread Based integration Testing:</mark>

The classes involved in one incoming event or input message (taken from the Interaction Sequence Diagram) for the thread and are assembled and tested.  

As threads are integrated, regression tests are done to check for any side effects of the integration.

![](https://i.imgur.com/fu4sQYR.png)

### <mark style="background: #FFB8EBA6;">Cluster Testing:</mark>

Grouping together cooperating classes that have similar functions or work together to accomplish a particular goal.  
- Typically the functionality of these classes would have already been tested using dummy drivers or test harness software.  
- This cluster may be modelled as a referenced sequence diagram.

![](https://i.imgur.com/ivLsCTX.png)

![](https://i.imgur.com/48Mxzog.png)

### <mark style="background: #FFB8EBA6;">Final steps of OO Testing:</mark>

As classes are integrated to form subsystems, thread-based, use-based and cluster-based testing along with fault-based approaches are applied to fully exercise collaborating classes.  

Collaboration or Interaction errors are targeted by exercising multiple subsystems in a single test case.

### <mark style="background: #FFB8EBA6;">Unit Testing:</mark>

<mark style="background: #FFB8EBA6;">Goal:</mark> Isolate individual parts of the program and show that they behave correctly  

<mark style="background: #FFB8EBA6;">Benefits:</mark> 
- A unit test explicitly specifies conditions that the individual program parts must satisfy.  
- This facilitates uncovering issues at an early stage and also ease in testing future modifications to ensure existing tests are still successful.  

<mark style="background: #FFB8EBA6;">Limitations:</mark> Testing cannot be expected to catch every error in the program

### <mark style="background: #FFB8EBA6;">Traditional Approach to Unit Testing:</mark>

<mark style="background: #FFB8EBA6;">Write the code:</mark>  
- Write your implementation
- e.g. java methods  

<mark style="background: #FFB8EBA6;">Test the code:</mark>  
- Write a class that instantiates an object of the class and tests the methods by executing them and checking results etc.  
- Fix any problems encountered...

### <mark style="background: #FFB8EBA6;">Test Driven Development (TDD):</mark>

Test Driven Development (TDD) is a design technique that drives the development process through testing. In essence you follow three simple steps repeatedly:  
1. Write a test for the next bit of functionality you want to add.  
2. Write the functional code until the test passes.  
3. Refactor both new and old code to make it well structured.

![](https://i.imgur.com/Vr1jE0g.png)

### <mark style="background: #FFB8EBA6;">Why TDD:</mark>
- Code Modularisation, Flexibility, Extensibility  
- Clean code  
- Leads to better design  
- Better code documentation 
- Well tested codebase

### <mark style="background: #FFB8EBA6;">What to do:</mark>

A design model will have defined our classes (attributes and <mark style="background: #FFB8EBA6;">operations</mark>).  

Tools can generally automatically create the skeleton code from the class diagram (e.g MyClass.java) – where methods have return values, one line of code is inserted which returns a null.  

Next we can write a test class (e.g. ``MyClassTest.java``) within which we write methods that test instances of our actual class.  

Remember, none of our methods actually have any code – so the tests should all fail.  

Take one test at a time and go back to our actual class and write just enough code to pass that test.

### <mark style="background: #FFB8EBA6;">Using Mock Objects in Testing:</mark>

When writing Unit tests, there can be a number of collaborating objects that are required to be available in order to test a given class.  
- Objects can be passed as parameters to the method under test.  
- The method under test may use objects which are attributes of its class.  

The test class needs to create the necessary instances of these objects so that the method under test can be called in an appropriate context  

This can be a challenging obstacle when testing non-trivial classes (object creation, attribute setting etc.).

Remember – when we are writing unit tests, we are only interested in testing the unit and not any other units that it requires to perform its function.  

What if we could ‘mock up’ any other objects that our object under test requires.  

This would free us up from being dependent on those other objects.

![](https://i.imgur.com/td4KrQy.png)

### <mark style="background: #FFB8EBA6;">Test Code - creating a mock object:</mark>

![](https://i.imgur.com/5mPYPHm.png)

![](https://i.imgur.com/lJhj2oR.png)

### <mark style="background: #FFB8EBA6;">Development Methodology:</mark>

<mark style="background: #FFB8EBA6;">TDD</mark> and <mark style="background: #FFB8EBA6;">Mock Objects</mark> can help in a number of ways when it comes to design and development.  

Once the domain model has been defined and behavioural models developed:  
- A set of interfaces can be defined and created  
- Different development teams can work on different aspects concurrently through the use of those interfaces  
- Unit tests can be written independent of required objects  

Think of a Service class that uses a <mark style="background: #FFB8EBA6;">Dao</mark> class...