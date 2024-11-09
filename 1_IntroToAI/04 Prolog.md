<mark style="background: #69E7E4;">Theory:</mark>
- Unification
- Unification in Prolog
- Proof search

<mark style="background: #69E7E4;">Aim of this lecture:</mark>
- Discuss unification in Prolog: Show how Prolog unification differs from standard unification

- Explain Prolog’s search strategy: Prolog deduces new information from old, using modus ponens

### <mark style="background: #69E7E4;">Unification:</mark>

Recall the previous example, where we
said that Prolog unifies

``woman(X)``

with

``woman(mia)``

thereby instantiating the variable ``X`` with
the atom ``mia``.

<mark style="background: #69E7E4;">Recall Prolog terms:</mark>
![](https://i.imgur.com/vYm1Gml.png)

<mark style="background: #69E7E4;">Working definition – two terms unify:</mark>
- if they are the same term, or
- if they contain variables that can be uniformly
- instantiated with terms in such a way that the resulting terms are equal

<mark style="background: #69E7E4;">This means that:</mark>
- ``mia`` and ``mia`` unify
- ``42`` and ``42`` unify
- ``woman(mia)`` and ``woman(mia)`` unify

<mark style="background: #69E7E4;">This also means that:</mark>
- ``vincent`` and ``mia`` do not unify
- ``woman(mia)`` and ``woman(jody)`` do not unify

### <mark style="background: #69E7E4;">Instantiations:</mark>

When Prolog unifies two terms, it performs all the necessary instantiations, so that the terms are <mark style="background: #69E7E4;">equal</mark> afterwards

This makes unification a very powerful programming mechanism

### <mark style="background: #69E7E4;">Revised Definition:</mark>

If T<sub>1</sub> and T<sub>2</sub> are constants, then T<sub>1</sub> and T<sub>2</sub> unify if they are the same atom, or the same number

If T<sub>1</sub> is a variable and T<sub>2</sub> is any type of term, then T<sub>1</sub> and T<sub>2</sub> unify, and T<sub>1</sub> is instantiated to T<sub>2</sub>(and vice versa)

If T<sub>1</sub> and T<sub>2</sub> are complex terms then they unify if:
1. They have the same functor and arity, and
2. all their corresponding arguments unify, and
3. the variable instantiations are compatible.

```Prolog
?- mia = mia.
yes
?- mia = vincent.
no
?- mia = X.
X=mia
yes
?-
```

Why? After working through the first goal, Prolog has instantiated X with ``mia``, so that it cannot unify it with ``vincent`` anymore. Hence the second goal fails.

### <mark style="background: #69E7E4;">Prolog and unification:</mark>

Prolog does not use a standard unification algorithm

Consider the following query:

```Prolog
?- father(X) = X.
```

Do these terms unify or not?

<mark style="background: #69E7E4;">Infinite terms:</mark>
```Prolog
?- father(X) = X.
X=father(father(father(father(father(father
(father(father(father(father(father(father
(father(father(father(father(father(father
(father(father(father(father(father(father
(father(father(father(father(father(father
(father(father(father(father(father(father
(father(father(father(father(father(father
(father(father(father(father(father(father
(.............
```

```Prolog
?- father(X) = X.
X=father(father(father(…))))
yes
?-
```

### <mark style="background: #69E7E4;">Occurs Check:</mark>

A standard unification algorithm carries out an occurs check

If it is asked to unify a variable with another term it checks whether the variable occurs in this term

<mark style="background: #69E7E4;">In Prolog (ISO standard):</mark>
```Prolog
?- unify_with_occurs_check(father(X), X).
no
```

### <mark style="background: #69E7E4;">Programming with unification:</mark>

```Prolog
vertical( line(point(X,Y),
point(X,Z))).
horizontal( line(point(X,Y),
point(Z,Y))).
```

```Prolog
?- vertical(line(point(1,1),point(1,3))).
yes
?- vertical(line(point(1,1),point(3,2))).
no
?- horizontal(line(point(1,1),point(1,Y))).
Y = 1;
no
?- horizontal(line(point(2,3),Point)).
Point = point(_554,3);
no
?-
```

![](https://i.imgur.com/EcCtg1q.png)

### <mark style="background: #69E7E4;">Proof search:</mark>

Now that we know about unification, we are in a position to learn how Prolog searches a knowledge base to see if a
query is satisfied.

In other words: we are ready to learn about <mark style="background: #69E7E4;">proof search</mark> and <mark style="background: #69E7E4;">search trees</mark>

![](https://i.imgur.com/Hw5ZBeO.png)

![](https://i.imgur.com/k8MUv4g.png)

![](https://i.imgur.com/z8T1PEI.png)

![](https://i.imgur.com/2mZBOP0.png)

![](https://i.imgur.com/z5Wp7Kh.png)

![](https://i.imgur.com/73MkOwi.png)

![](https://i.imgur.com/ULB6FSc.png)

![](https://i.imgur.com/LJN9PtY.png)

![](https://i.imgur.com/3BSFsOO.png)

![](https://i.imgur.com/jibG7OT.png)
