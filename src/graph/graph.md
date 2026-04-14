# Graph

---

## 1. 743. Network Delay Time — Dijkstra `[5/21]`

**Pattern:** Dijkstra with a min-heap. `(dist, node)` pairs in heap.

**Key Insight:** Relax neighbors only when popped from heap (greedy). Use `dist[]` array initialized to infinity.

```
heap = [(0, src)]
while heap:
    d, u = heappop(heap)
    if d > dist[u]: continue   # stale entry
    for v, w in graph[u]:
        if dist[u] + w < dist[v]:
            dist[v] = dist[u] + w
            heappush(heap, (dist[v], v))
```

---

## 2. 1514. Path with Maximum Probability — Dijkstra `[5/21]`

**Pattern:** Max-probability Dijkstra. Use a max-heap (negate probabilities). Multiply edge weights instead of adding.

**Key Insight:** Same structure as 743, but maximize product of probabilities instead of minimizing sum of weights.

---

## 3. 207. Course Schedule — Topological Sort `[2/27]`

**Pattern:** Build indegree array + adjacency list. BFS (Kahn's algorithm).

**Key Insight:**
- If a cycle exists, involved nodes will **never** reach indegree = 0.
- Only enqueue a node when its indegree drops to 0 — that's the "ready to take" signal.

```
If count of processed nodes == numCourses → no cycle → return True
```

---

## 4. 934. Shortest Bridge `[3/6]`

**Pattern:** Two-phase BFS.
1. DFS to find all cells of island 1, add them to a BFS queue.
2. Multi-source BFS expanding outward — first time you reach island 2 is the answer.

---

## 5. 133. Clone Graph `[3/9]`

**Pattern:** BFS with a `old → new` node map.

**Key Insight:**
1. A node is considered **visited** when its children are being processed (not when it's first seen).
2. Even if a child has already been cloned, you still **must connect** the edge from the current clone to it.

> Don't skip the edge connection just because the neighbor is already in the map!

---
