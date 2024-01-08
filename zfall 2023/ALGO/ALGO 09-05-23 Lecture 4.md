## Implementation of Gale-Shapley
#### Goal:
- Implement Gale-Shapley to run in $O(n^2)$ time
#### Representing Hospitals and Students:
- Index hospitals and students $1,...,n$
#### Representing the matching:
- Maintain two arrays $student[h]$ and $hospital[s]$
    - If $h$ matched to $s$, then $student[h] = s$ and $hospital[s] = h$
    - use value $0$ to designate that hospital or student is unmatched
- Can add/remove a pair from matching in $O(1)$ time
- Maintain set of unmatched hospitals in a queue (or stack)
- Can find an unmatched hospital in $O(1)$ time

### Hospital makes a proposal:
- #### Key Operation:
    - Find hospitals next favorite student
- #### For Each Hospital:
    - maintain a list of students, ordered by preference
    - maintain a pointer to student for next proposal

### Student accepts/rejects a proposal
- Does student $s$ prefer hospital $h$ to hospital $h'$?
- For each student, create *inverse* of preference list of hospitals

### Bottom Line:
- After $O(n^2)$ preprocessing time (to create the $n$ ranking arrays), it takes $O(1)$ time to rank

## Common Running Times
### Constant Time:
- Running time is $O(1)$
- Ex:
    - Conditional branch
    - Arithmetic/logic operation
    - Accessing next node in linked list
### Linear Time:
- Running time is $O(n)$
- Ex:
    - Merge two sorted lists
    - Mergesort
### Logarithmic Time:
- Running time is $O(\log n)$
- Ex:
    - Binary Search
### Linearithmic Time:
- Running time is $O(n \log n)$
- Ex:
    - Largest-Empty-Interval
### Cubic Time:
- Running time is $O(n^3)$
- Ex:
    - 3-Sum
### Polynomial Time:
- Running time is $O(n^k)$ for any constant $k > 0$
- Ex:
    - Independent set of size $k$
### Exponential Time:
- Running time is $O(2^{n^{k}})$
- Ex:
    - Euclidean Travelling Salesman

## Graphs
### Notation:
- $V$ = nodes (vertices)
- $E$ = edges (arcs)
- Captures pairwise relationships
- Graph size parameters: $n = |V|, m = |E|$ 

#### Adjacency Matrix:
- n-by-n matrix with $A_{uv}= 1$ if $(u,v)$ is an edge
- Two representations of each edge
- Space proportional to $n^2$
- Checking if $(u, v)$ is an edge takes $\Theta(1)$ time
- Identifying all edges takes $\Theta(n^2)$ time

#### Adjacency List:
- Node-indexed array of lists
- Two representations of each edge
- Space is $\Theta(m + n)$
- Checking if an edge exists takes $o(degree(u))$ time
    - degree of a vertex is number of edges connected to it
- Identifying all edges takes $\Theta(m + n)$ time

#### Path:
- A sequence of nodes with the property that each consecutive pair is joined by a different edge
- A path is *simple* if all nodes are distinct
- An undirected graph is *connected* if for every pair of nodes $u$ and $v$, there is a path between $u$ and $v$


