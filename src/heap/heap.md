# Heap / Priority Queue

---

## 1. 378. Kth Smallest Element in a Sorted Matrix `[5/21]`

**Pattern:** Min-heap initialized with the first element of each row. Pop k times.

**Key Insight:** Each pop gives the current minimum; push the next element from that row. Exploits the row-sorted and column-sorted property.

```
heap = [(matrix[r][0], r, 0) for r in range(min(k, n))]
heapify(heap)
for _ in range(k):
    val, r, c = heappop(heap)
    if c + 1 < n:
        heappush(heap, (matrix[r][c+1], r, c+1))
return val
```

**Alternative:** Binary search on value range — `lo=matrix[0][0]`, `hi=matrix[n-1][n-1]`, count elements ≤ mid.

---

## 2. 215. Kth Largest Element in an Array `[2/27]`

**Pattern:** Min-heap of size k. The root is always the kth largest.

---

## 3. 296. Find Median from Data Stream `[3/1]`

**Pattern:** Two heaps — a max-heap for the lower half, a min-heap for the upper half. Keep them balanced (size diff ≤ 1).

**Key Insight:** Median is either the top of one heap (odd total) or average of both tops (even total).

---

## 4. 23. Merge K Sorted Lists `[3/11][4/5]`

**Pattern:** Min-heap of `(val, node)`. Pop minimum, push its next node.

**Key Insight:** Need a tiebreaker in the heap tuple if `ListNode` isn't comparable — add an integer counter as second element.

---

## 5. 347. Top K Frequent Elements `[3/9]`

**Pattern:** `Counter` + min-heap of size k, or bucket sort by frequency.

---

## 6. 973. K Closest Points to Origin `[3/11][4/2]`

**Pattern:** Max-heap of size k (negate distance). Or `heapq.nsmallest(k, points, key=lambda p: p[0]**2 + p[1]**2)`.

---
