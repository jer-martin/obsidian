### Algorithm:
- A procedure that takes an input, transforms it, and then outputs the result
	- Input/Output could be empty
- Similar to a map between sets

### Algorithm Abstraction:
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
		- Want to bound ratio value

