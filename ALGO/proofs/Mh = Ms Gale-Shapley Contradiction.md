Certainly! The statement you've put forth is a result from the classic Gale-Shapley algorithm and its properties. Let's go through the proof.

**Statement**: There exists a unique stable matching of students and hospitals if and only if $M_{h}= M_{s}$

### Proof:

**Part 1**: If there exists a unique stable matching, then $M_{h}= M_{s}$​.

Assume that there exists a unique stable matching $M$, but $M \ne M_{h}$​, where $M_{h}$​ is the hospital-optimal stable matching. Then there must be some student $s$ and hospital $h$ such that $s$ is matched to $h$ in $M_{h}$​ but not in $M$. Let $h$ be the hospital to which $s$ is matched in $M$.

Because �ℎMh​ is hospital-optimal, �s prefers ℎ′h′ over ℎh (since ℎh would have proposed to all of its higher preferences before �s). But this means �s and ℎ′h′ form a blocking pair to �ℎMh​, which contradicts the assumption that �ℎMh​ is stable. Hence, �=�ℎM=Mh​.

Similarly, if �≠��M=Ms​, we can derive a contradiction, so �=��M=Ms​.

Thus, �ℎ=��Mh​=Ms​.

**Part 2**: If �ℎ=��Mh​=Ms​, then the stable matching is unique.

Assume �ℎ=��Mh​=Ms​ but there exists another stable matching �′M′ such that �′≠�ℎM′=Mh​.

For the sake of contradiction, let's consider a student �s and hospitals ℎh and ℎ′h′ such that �s is matched to ℎh in �ℎMh​ and to ℎ′h′ in �′M′.

Since �ℎMh​ is hospital-optimal, it means �s prefers ℎ′h′ over ℎh (using the same logic as before).

However, since ��Ms​ is student-optimal and �ℎ=��Mh​=Ms​, it means that �s prefers ℎh over ℎ′h′. This is a contradiction.

Thus, there can be no such stable matching �′M′ different from �ℎMh​. Hence, the stable matching is unique.

From Part 1 and Part 2, we can conclude that there exists a unique stable matching of students and hospitals if and only if �ℎ=��Mh​=Ms​.

The beauty of this result is in showing the dual nature of the Gale-Shapley algorithm. When one side (hospitals or students) proposes, they get their optimal match, while the other side gets their pessimal (or worst stable) match. When there's only one stable matching, it's optimal for both.