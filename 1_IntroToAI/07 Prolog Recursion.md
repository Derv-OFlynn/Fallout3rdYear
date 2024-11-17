<mark style="background: #69E7E4;">Theory:</mark>
- Introduce recursive definitions in Prolog
- Go through four examples
- Show that there can be mismatches between the declarative and procedural meaning of a Prolog program

<mark style="background: #69E7E4;">Exercises:</mark>
- Exercises of LPN chapter 3
- Practical work

![](https://i.imgur.com/u9XXk5N.png)

### <mark style="background: #69E7E4;">Recursive definitions:</mark>

Prolog predicates can be defined recursively

A predicate is recursively defined if one or more rules in its definition refers to itself

### <mark style="background: #69E7E4;">Example 1 - Eating:</mark>

![](https://i.imgur.com/0QJQiRR.png)

```Prolog
isDigesting(X,Y):- justAte(X,Y).
isDigesting(X,Y):- justAte(X,Z), isDigesting(Z,Y).

justAte(mosquito,blood(john)).
justAte(frog,mosquito).
justAte(stork,frog).
```

![](https://i.imgur.com/Wt5jgFc.png)

```Prolog
?- isDigesting(stork,mosquito).
yes
```

### <mark style="background: #69E7E4;">Example 2 - Descendant:</mark>

![](https://i.imgur.com/S8rw2aw.png)

```Prolog
child(bridget,caroline).
child(caroline,donna).

descend(X,Y):- child(X,Y).
descend(X,Y):- child(X,Z), child(Z,Y).
```

```Prolog
child(anna,bridget).
child(bridget,caroline).
child(caroline,donna).
child(donna,emily).

descend(X,Y):- child(X,Y).
descend(X,Y):- child(X,Z), child(Z,Y).
```

```Prolog
?- descend(anna,donna).
no
?-
```

### <mark style="background: #69E7E4;">Search tree:</mark>

Draw search tree for

```Prolog
?- descend(anna,donna).
```

### <mark style="background: #69E7E4;">Example 3 - Successor:</mark>

![](https://i.imgur.com/mQYqDta.png)

Suppose we use the following way to write numerals:
1. 0 is a numeral.
2. If X is a numeral, then so is ``succ(X)``.

```Prolog
numeral(0).
numeral(succ(X)):- numeral(X).

?- numeral(succ(succ(succ(0)))).
yes
?- numeral(X).

X=0;
X=succ(0);
X=succ(succ(0));
X=succ(succ(succ(0)));
X=succ(succ(succ(succ(0))))
```

### <mark style="background: #69E7E4;">Prolog and Logic:</mark>

Prolog was the first reasonable attempt to create a logic programming language
- Programmer gives a declarative specification of the problem, using the language of logic
- The programmer should not have to tell the computer what to do
- To get information, the programmer simply asks a query

Prolog does some important steps in this direction

Nevertheless, Prolog is not a full logic programming language!

Prolog has a specific way of answering queries:
- Search knowledge base from top to bottom
- Processes clauses from left to right
- Backtracking to recover from bad choices

### <mark style="background: #69E7E4;">Four different descend/2:</mark>

![](https://i.imgur.com/pTlyjaI.png)

### <mark style="background: #69E7E4;">descend1.pl</mark>

```Prolog
child(anna,bridget).
child(bridget,caroline).
child(caroline,donna).
child(donna,emily).

descend(X,Y):- child(X,Y).
descend(X,Y):- child(X,Z), descend(Z,Y).

?- descend(A,B).
```

### <mark style="background: #69E7E4;">Summary of this lecture:</mark>

In this lecture we introduced recursive predicates

We also looked at the differences between the declarative and the procedural meaning of Prolog programs

We have identified some of the shortcomings of Prolog seen as a logical programming language

### <mark style="background: #69E7E4;">Matryoshka dolls:</mark>

![](https://i.imgur.com/7sH2sk4.png)

First, write a knowledge base using the predicate directlyIn/2 which encodes which doll is directly contained in which other doll.

Then, define a recursive predicate in/2, that tells us which doll is (directly or indirectly) contained in which other dolls.

![](https://i.imgur.com/N8EQoMP.png)
