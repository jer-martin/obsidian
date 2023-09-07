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

- ### Connected Component
    - Find all nodes reachable from $s$

- ### Bipartite Graphs
    - An undirected graph $G = (V, E)$ is bipartite if the nodes can be colored blue or white such that every edge has one white and one blue end
    - *applications:*
        - stable matching: med-school residents = blue, hospitals = white
        - scheduling: machines = blue, jobs = white
    - #### Many graph problems become:
        - Easier if the underlying graph is bipartite
        - Tractable if the underlying graph is bipartite

    *Before attempting to design an algorithm, we need to understand structure of bipartite graphs.*
    
    - *lemma*:
        - if a graph $G$ is bipartite, it cannot contain an odd-length cycle
    - *proof:*
        - not possible to 2-color the odd length cycle, let alone $G$

    - *lemma:*
        - Let $G$ be a connected graph, and let $L_0$, …, $L_k$ be the layers produced by BFS starting at node $s$. Exactly one of the following holds:
            - No edge of $G$ joins two nodes of the same layer, and $G$ is bipartite
            - An edge of $G$ joins two nodes of the same layer, and $G$ contains an odd-length cycle (and hence is not bipartite)
    - *proof:*
        - Suppose no edge joins two nodes in the same layer
        - By BFS property, each edge joins two nodes in adjacent levels. 
        - Bipartition: 
            - white = nodes on odd levels, blue = nodes on even levels.
        - Suppose $(x,y)$ is an edge with $x, y$ in same level $L_j$
        - Let $z=lca(x,y) =$ lowest common ancestor
        - Let $L_i$ be level containing $z$
        - Consider cycle that takes edge from $x$ to $y$, then path from $y$ to $z$, then path from $z$ to $x$. 
        - Its length is $1 + (j – i) + (j – i)$, which is odd.

- ### Directed Graphs
    - #### Notation:
        - $G = (V, E)$
        - Edge $(u, v)$ leaves vertex $u$ and goes to vertex $v$
    - #### Strong Connectivity
        - Nodes $u$ and $v$ are mutually reachable if there is both a path from $u$ to $v$ and also a path from $v$ to $u$.
        - Nodes $u$ and $v$ are mutually reachable if there is both a path from $u$ to $v$ and also a path from $v$ to $u$.
    - *lemma:*
        - Let $s$ be any node. $G$ is strongly connected if every node is reachable from $s$, and $s$ is reachable from every node.
    - *proof:*
        - ⇒ Follows from definition. 
        - ⇐ Path from $u$ to $v$: concatenate $u↝s$ path with $s↝v$ path. Path from $v$ to $u$: concatenate $v↝s$ path with $s↝u$ path.
    - Can determine if $G$ is strongly connected in $O(m + n)$ time
    - *proof:*
        - Pick any node $s$
        - Run BFS from $s$ in $G$
        - Run BFS from $s$ in $G^{reverse}$
        - Return true if all nodes reached in both BFS executions
        - Correctness follows from previous *lemma*
    -
    
**Strong Component**
-  maximal subset of mutually reachable nodes