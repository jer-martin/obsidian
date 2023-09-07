## Graphs
    continuation of last lecture
- ### [Notation](ALGO%2009-05-23%20Lecture%204.md)
- ### [Path](ALGO%2009-05-23%20Lecture%204.md)

- ### Cycle
    - A cycle is a path $v_{1},v_{2}...$ in which $v_{1}= v_{k}$ and $k \ge 2$ 
    - A cycle is simple if all nodes are distinct (except for $v_{1}$ and $v_{k}$ )

- ### Trees
    - An undirected graph is a tree if it is connected and doesn't contain a cycle
    - Let $G$ be an undirected graph on $n$ nodes. Any two of the following statements *imply the third:*
        - G is connected
        - G does not contain a cycle
        - G has $n-1$ edges

- ### Rooted Trees
    - Given a tree $T$, choose a root node $r$ and orient each edge away from $r$
    - Models hierarchical structure

- ### Connectivity
    - *s-t connectivity problem*
        - given two nodes $s$ and $t$, is there a path between them?
    - *s-t shortest path problem.*
        -  Given two nodes $s$ and $t$, what is the length of a shortest path between the two?

- ### Breadth-first Search
    - Explore outward from $s$ in all possible directions, adding nodes one "layer" at a time
    - *algorithm*:
        - $L_{0} = \{s\}$ 
        - $L_{1}$ all neighbors of $L_{0}$
        - $L_{2}$ = all nodes that do not belong to $L_{0}$ or $L_{1}$, and that have an edge to a node in $L_1$  
        - $L_{i+1}$ = all nodes that do not belong to an earlier layer, and that have an  edge to a node in $L_{i}$
    - *theorem:*
        - For each $i,$ $L_i$ consists of all nodes at distance exactly $i$ from $s$. There is a path from $s$ to $t$ if $t$ appears in some layer
    - *proof:*
        - easy to prove $O(n^{2})$ running time:
            - at most $n$ lists $L[i]$
            - each node occurs on at most one list; for loop runs $\le n$ times
            - when we consider node $u$, there are $\le n$ incident edges $(u, v)$, and we spend $O(1)$ processing each edge
        - actually runs in $O(m+n)$ time:
            - when we consider node $u,$ there are $degree(u)$ incident edges $(u,v)$
            - total time processing edges is $\Sigma_{u\in V} degree(u) = 2m$
            - each edge $(u,v)$ is counted exactly twice in sum; once in $degree(u)$ and once in $degree(v)$
        - 