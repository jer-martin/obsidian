## Dijkstra's Algorithm
#### Caching
- Cache with capacity to store $k$ items.
- Sequence of $m$ item requests $d_{1}, d_{2}, ..., d_{m}$ 
- Cache hit: item already in cache when requested
- Cache miss: item not in cache when requested

#### Optimal Algorithm
- **Farthest In Future**:
	- Evict item in the cache that is not requested until farthest in the future

#### Reduced Schedule
- A reduced schedule is a schedule that only inserts an item into the cache in a step in which that term is requested

