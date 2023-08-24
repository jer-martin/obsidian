### #Algorithm:
- A procedure that takes an input, transforms it, and then outputs the result
	- Input/Output could be empty
- Similar to a map between sets

### #Algorithm Abstraction:
- What do these scenarios have in common?
	- Pair up students to be roommates based on how they ranked each other. There should not be a pair of students who both prefer each other over their assigned roommates.
	- Medical students and hospitals have ranked each other. Assign students to hospitals (not necessarily one-to-one) so that there is no student-hospital pair where both members prefer someone else to their assigned.
- Abstract problem: Stable matching (or variations)
	- given sets A and B and functions $F_a$: A x B -> R and $F_b$: B x A -> R
	- find a bijective function M: A -> B s.t. there do not exist pairs (a,b) and (a',b') satisfying
		- a,a' ∈ A; b, b' ∈ B; a $\ne$ a'; b $\ne$ b'
		- M(a) = b
		- $F_a$(a, b) < $F_a$(a, b') and $F_b$(b,a) < $F_b$(b, a')

*Abstract algorithm can solve abstract problem*s

Most course content is under these categories:
- #Graphs
- #Greedies
- #DivideNConquer
- #DP
- #NetworkFlow

### P vs NP
- P = polynomial time
- NP = non-deterministic polynomial time
	- i.e. if given a possible solution to a problem, can check if solution is correct in polynomial time

- How to cope with NP-complete problems?
	- Approximation algorithms: finds a solution (called SOL) that is close enough to the best solution (called OPT)
		- Want to bound ratio value(SOL)/value(OPT)

*Approximation does not solve every problem!*
- Traveling salesman problem (TSP): given a set of cities and costs of paths between them, find a minimum cost path that visits all cities exactly once then returns to the starting city
- Cannot achieve certain approximation bounds for TSP unless P = NP
- Can get good approximation bounds for  **special cases**  of TSP


## Stable Matching #
### Goal:
- Given a set of preferences among hospitals and med-school students, design a self-reinforcing admissions process
### Unstable Pair:
- Hospital $h$  and student $S$ prefer other matches to current partner
- *BOTH MUST BE TRUE:*
	- $h$ prefers $s$ to matched student
	- $s$ prefers $h$ to matched hospital
- Unstable pair can be fixed by **joint action**



### Gale-Shapley #Greedies 
Initialize $M$ to empty matching
- While some hospital $h$ is unmatched and hasn't proposed to every student
	 $s$ <- first student on $h$'s list to whom $h$ has not yet proposed
- If $s$ is unmatched
	Add $h-s$ to matching $M$
- Else if $s$ prefers $h$ to current partner $h'$
	Replace $h'-s$ with $h-s$ in matching $M$
- Else
	$s$ rejects $h$
Return stable matching $M$ 

### Observation 1 
	Hospitals propose to students in decreasing order of preference
### Observation 2 
	Once a student is matched, the student never becomes unmatched; only "trades up"

