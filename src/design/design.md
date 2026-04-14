# Design & Misc

---

## 1. 1570. Dot Product of Two Sparse Vectors `[1/29][3/31]`

**Pattern:** Store non-zero elements as `{index: value}` dict. Iterate over the smaller dict, look up in the larger.

---

## 2. 348. Design Tic-Tac-Toe `[3/12][4/5]`

**Pattern:** Track row sums, col sums, and two diagonal sums per player. A win is when any sum reaches `n`.

**Key Insight:** No need to store the board. Use arrays `rows[n]`, `cols[n]`, and two integers `diag`, `anti_diag`. Increment for player 1, decrement for player 2 (or use separate arrays). Win when `abs(count) == n`.

---

## 3. 346. Moving Average from Data Stream `[3/9][3/28]`

**Pattern:** Fixed-size `deque`. Maintain running sum — subtract outgoing value, add incoming value.

---

## 4. 528. Random Pick with Weight `[3/3]`

**Pattern:** Prefix sum array + binary search. `random.random() * total_weight` gives a target; binary search for first prefix sum ≥ target.

---

## 5. 560. Subarray Sum Equals K `[3/2][6/3]`

**Pattern:** Prefix sum + hashmap. For each index, check if `prefix_sum - k` exists in the map.

**Key Insight:** `count[0] = 1` initialized — handles subarrays starting from index 0.

```python
count = {0: 1}
prefix = 0
result = 0
for num in nums:
    prefix += num
    result += count.get(prefix - k, 0)
    count[prefix] = count.get(prefix, 0) + 1
return result
```

---

## 6. 246. Strobogrammatic Number `[3/19]`

**Pattern:** Two pointers from both ends. Valid strobogrammatic pairs: `(0,0)`, `(1,1)`, `(6,9)`, `(8,8)`, `(9,6)`.

---

## 7. 339. Nested List Weight Sum `[3/16]`

**Pattern:** DFS with depth parameter. For each `NestedInteger`, if integer add `val * depth`, else recurse into its list with `depth+1`.

---
