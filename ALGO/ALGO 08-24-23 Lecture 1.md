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
		- a,a' ∈ A; b, b' ∈ B; a =/= a'; b =/= b'
		- M(a) = b
		- $F_a$(a,b) < $F_a$(a,b') and $F_b$(b,a) < $F_b$(b, a')

*Abstract algorithm can solve abstract problem*s

Most of course content is under:
- Graphs
- Greedies
- Divide and conquer
- Dynamic Programming