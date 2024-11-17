### <mark style="background: #69E7E4;">Introduction:</mark>

One of the most powerful approaches to problem solving in AI

Represent problem as
- a set of states
- a start state
- a set of legal moves between states
- a set of goal states or a goal condition

Convenient to represent as a directed graph

![](https://i.imgur.com/QG1xRru.png)

### <mark style="background: #69E7E4;">Block Stacking:</mark>

![](https://i.imgur.com/ijcWaLu.png)

### <mark style="background: #69E7E4;">State Space:</mark>

![](https://i.imgur.com/gqWBfjL.png)

### <mark style="background: #69E7E4;">Sliding Tiles Problem:</mark>

![](https://i.imgur.com/6t72uJ1.png)

### <mark style="background: #69E7E4;">A fragment of State Space:</mark>

![](https://i.imgur.com/ubXJDqx.png)

### <mark style="background: #69E7E4;">Route Finding:</mark> 

![](https://i.imgur.com/8aG9rUa.png)

### <mark style="background: #69E7E4;">Other Examples:</mark>

![](https://i.imgur.com/AnYbVy3.png)

### <mark style="background: #69E7E4;">State space search using Prolog:</mark>

Represent each arc by a relation:

``s(X,Y)`` or ``move(X,Y)``

meaning there is a legal move from node X to node Y or state X to state Y. Can say Y is a successor state to X.

Remember to include moves in both directions.

Assume a predicate ``goal(X)`` that is true if X is a goal node.

### <mark style="background: #69E7E4;">The solve predicate:</mark>

Want predicate solve(Node, List) that takes a start node Node and returns a list of nodes List on the route to a goal node, if such a route exists.

<mark style="background: #69E7E4;">Two cases:</mark>
- Node is already a goal node
- if a route exists to a goal node from a successor of Node, then tacking Node onto this route gives a solution.

![](https://i.imgur.com/J3dWeRZ.png)

### <mark style="background: #69E7E4;">Writing this in Prolog:</mark>

```Prolog
solve(Node,[Node]) :-
	goal(Node).

solve(Node,[Node|Sol]) :-
	s(Node,Successor),
	solve(Successor,Sol).
```

<mark style="background: #69E7E4;">Note:</mark> instead ``s(Node, Successor)`` we usually write something like: ``move(State, NextState)``

### <mark style="background: #69E7E4;">An example:</mark>

![](https://i.imgur.com/L1UQEpS.png)

### <mark style="background: #69E7E4;">Execution Trace 1:</mark>

![](https://i.imgur.com/DSmeDVW.png)

### <mark style="background: #69E7E4;">Execution Trace - 2:</mark>

![](https://i.imgur.com/hLlCmfp.png)

### <mark style="background: #69E7E4;">Search path:</mark>

![](https://i.imgur.com/3h12vMG.png)

### <mark style="background: #69E7E4;">First Attempt in Prolog:</mark>

![](https://i.imgur.com/raQpsQb.png)

### <mark style="background: #69E7E4;">Circular paths:</mark>

![](https://i.imgur.com/wsvOfMr.png)

### <mark style="background: #69E7E4;">Our Prolog code goes into infinite loop with circular path</mark>

![](https://i.imgur.com/rQZbGhz.png)

### <mark style="background: #69E7E4;">Prolog code to prevent looping:</mark>

![](https://i.imgur.com/lQd7609.png)

### <mark style="background: #69E7E4;">Prolog code to prevent looping:</mark>

```Prolog
solve(N,Sol):- solve(N,[],Sol).

solve(N, Path,[N|Path]):- goal(N).

solve(N,Path,Sol):-
	s(N,N1),
	not (member(N1,Path)),
	solve(N1,[N|Path],Sol).
```

### <mark style="background: #69E7E4;">Execution Trace 1:</mark>

![](https://i.imgur.com/udzJOPh.png)

### <mark style="background: #69E7E4;">Execution Trace 2:</mark>

![](https://i.imgur.com/JMBDETz.png)
