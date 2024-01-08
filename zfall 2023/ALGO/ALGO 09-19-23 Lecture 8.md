## Dijkstra's Algorithm
#### Caching
- Cache with capacity to store $k$ items.
- Sequence of $m$ item requests $d_{1}, d_{2}, ..., d_{m}$ 
- Cache hit: item already in cache when requested
- Cache miss: item not in cache when requested

#### Optimal Algorithm
- **Farthest In Future**:
	- Evict item in the cache that is not requested until farthest in the future

### Reduced Schedule
- A reduced schedule is a schedule that only inserts an item into the cache in a step in which that term is requested
#### Claim:
- Given any unreduced schedule $S$,, can transform it into a reduced schedule $S'$ with no more cache evictions
#### Proof:
- Suppose $S$ brings $d$ into the cache at time $t$, without a request
- Let $c$ be the item $S$ evicts when it brings $d$ into the cache
- Case 1: $d$ evicted at time $t'$, before next request to $d$.
- Case 2: $d$ requested at time $t'$ before $d$ is evicted


### Theorem:
- Prove the Farthest in the Future algorithm is optimal.
#### Proof:
##### Invariant:
- There exists an optimal reduced schedule $S$ that makes the same eviction schedule as $S_{FF}$ through the first $j+1$ requests

	Let $S$ be reduced schedule that satisfies invariant through $j$ requests. We produce $S'$ that satisfies invariant after $j+1$ requests.


