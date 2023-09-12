
**Statement**: There exists a unique stable matching of students and hospitals if and only if $M_{h}= M_{s}$

### Proof:

**Part 1**: If there exists a unique stable matching, then $M_{h}= M_{s}$​.

Assume that there exists a unique stable matching $M$, but $M \ne M_{h}$​, where $M_{h}$​ is the hospital-optimal stable matching. Then there must be some student $s$ and hospital $h$ such that $s$ is matched to $h$ in $M_{h}$​ but not in $M$. Let $h'$ be the hospital to which $s$ is matched in $M$.

Because $M_{h}$​ is hospital-optimal, $s$ prefers $h'$ over $s$ (since $h$ would have proposed to all of its higher preferences before $s$). But this means $s$ and $h'$ form a blocking pair to $M_{h}$​, which contradicts the assumption that $M_{h}$​ is stable. Hence, $M=M_{h}$

Similarly, if $M \ne M_{s}$, we can derive a contradiction, so $M = M_{s}$.

Thus, $M = M_{h}= M_{s}$.

**Part 2**: If $M_{h}= M_{s}$, then the stable matching is unique.

Assume $M_{h}= M_{s}$​ but there exists another stable matching $M'$ such that $M' \ne M_{h}$

For the sake of contradiction, let's consider a student $s$ and hospitals $h$ and $h'$ such that $s$ is matched to $h$ in $M_{h}$ and to $h'$ in $M'$.

Since $M_{h}$​ is hospital-optimal, it means $s$ prefers $h'$ over $h$ (using the same logic as before).

However, since $M_{s}$ is student-optimal and $M_{h}= M_{s}$​, it means that $s$ prefers $h$ over $h'$. This is a contradiction.

Thus, there can be no such stable matching $M$ different from $M_{h}$​. Hence, the stable matching is unique.

From Part 1 and Part 2, we can conclude that there exists a unique stable matching of students and hospitals if and only if $M_{h}=M_{s}$

The beauty of this result is in showing the dual nature of the Gale-Shapley algorithm. When one side (hospitals or students) proposes, they get their optimal match, while the other side gets their pessimal (or worst stable) match. When there's only one stable matching, it's optimal for both.