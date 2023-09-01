## Review: 
#### Interval Scheduling: 
- $O(n\log n)$ greedy algorithm
#### Weighted IS: 
- $O(n\log n)$ dynamic programming algorithm
#### Bipartite matching: 
- $O(n^k)$ max-flow based algorithm
#### Independent set: 
- NP-Complete
#### Competitive facility location: 
- PSPACE-Complete

## Algorithm Analysis
#### Deterministic Turing Machine:
- Simple and idealistic model
##### -  Running Time
- Number of Steps
##### - Memory
- Number of tape cells utilized
##### - Caveat
- No random access of memory

**Single-tape TM requires $\ge n^2$ steps to detect n-bit palindrome 

**Word Ram**
- Each memory location and input/output cell stores a $w$-bit integer
- Primitive operation:
	- arithmetic/logic

#### Brute Force:
- For many nontrivial problems, there is a natural brute force search algorithm that checks every possible solution
	- Typically takes $2^n$ steps (or worse)

### Polynomial Running Time:
##### Desirable scaling property:
- When the input size doubles, the algorithm should slow down by at most some multiplicative constant factor $C$
- An algorithm is **POLY-TIME** if the above scaling property holds

**We say that an algorithm is *efficient* if it has a polynomial running time**

Definition is (relatively) insensitive to model of computation.

Poly time algorithms that people develop have both small exponents and constants.

Breaking through the exponential barrier of brute force typically exposes some crucial structure of the problem.

**Exceptions**
- Some poly-time algorithms in the wild have galactic constants and/or huge exponents (map graphs in poly time is $n^{120}$)


### Worst Case Analysis:
- Running time guarantee for **any input** of size $n$
- Generally captures efficiency in practice
- Draconian view, but hard to find effective alternative
- Some exponential time algorithms are used widely in practice because the worst-case instances don't arise

### Other Types of Analysis:
- ##### Probabilistic:
	- Expected running time of a *randomized* algorithm
	- Ex: the expected number of compares to quick-sort $n$ elements is ~$2n \ln n$ 
- ##### Amortized
	- Worse case running time for *any sequence* of $n$ operations
	- Starting from an empty stack, any sequence of $n$ push and pop operations takes $O(n)$ steps using a resizing array

*We will generally focus on big O (worst-case analysis)*

### Big O Notation:
- ##### Upper Bounds:
	- $f(n)$ is $O(g(n))$ if there exists constants $c > 0$ and $n_{0}\ge 0$ such that $0 \le f(n) \le c * g(n)$ for all $n \ge n_0$ 
- ##### One way "equality":
	- $O(g(n))$ is a set of functions but computer scientists often write $f(n) = O(g(n))$ instead of $f(n) \in O(g(n))$ 
- ##### Reflexivity:
	- $f$ is $O(f)$
- ##### Constants:
	- If $f$ is $O(g)$ and $c > 0$ then $cf$ is $O(g)$ 
- ##### Products:
	- If $f_1$ is $O(g_1)$ and $f_2$ is $O(g_2)$ then $f_{1}f_{2}$ is $O(g_{1}g_{2})$ 
- ##### Sums:
	- If $f_{1}$ is $O(g_{1})$ and $f_2$ is $O(g_{2})$ then $f_{1}+ f_{2}$ is $O(\max(g_{1},g_{2}))$ 
- ##### Transitivity:
	- If $f$ is $O(g)$ and $g$ is $O(k)$ then $f$ is $O(k)$ 
- ##### Lower Bounds:
	- $f(n)$ is $\Omega(g(n))$ if there exist constants $c > 0$ and $n_{0}\ge 0$ such that $f(n) \ge c * g(n) \ge 0$  for all $n \ge n_0$ 
	- **Typical usage**
		- Any compare based sorting algorithm requires $\Omega(n \log n)$ compares in the worst case
	- **Vacuous statement**
		- Any compare based sorting algorithm requires $O(n \log n)$ compares in the worst case
- ### Big Theta Notation
	- ##### Tight Bounds:
		- $f(n)$ is $\Theta(g(n))$ if there exist constants $c_{1}>0, c_{2}>0$, and $n_{0}\ge 0$ such that $0 \le c_{1} * g(n) \le f(n) \le c_{2} * g(n)$ for all $n \ge n_0$ 
			- $f(n)$ is *IN BETWEEN* $c_{1} * g(n)$ and $c_{2} * g(n)$ 
	- *BIG THETA MEANS THAT $f(n)$ IS BOTH $O(g(n))$ AND $\Omega(g(n))$ 

- ### Big O with Multiple Variables
	- ##### Upper Bounds:
		- $f(m,n)$ is $O(g(m,n))$ if there exists constants $c > 0$, $m_{0}\ge 0$, and $n_{0}\ge 0$ such that $0 \le f(m,n) \le c * g(m,n)$ for all $n \ge n_0$ or $m \ge m_0$
		- If $n < m$ *always,* the multi-variable problem can be reduced to one variable
		- **Typical usage
			- In the worst case, breadth-first search takes $O(m + n)$ time to find a shortest path from $s$ to $t$ in a digraph with $n$ nodes and $m$ edges
