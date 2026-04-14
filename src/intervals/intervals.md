# Intervals & Rectangles

---

## 1. 986. Interval List Intersections `[5/25]`

**Pattern:** Two pointers, one per list. Compute overlap, advance the pointer with the earlier end.

**Key Insight:** Intersection of `[a, b]` and `[c, d]` is `[max(a,c), min(b,d)]` — valid only if `max(a,c) <= min(b,d)`. Advance the pointer whose interval ends first.

```python
i = j = 0
while i < len(A) and j < len(B):
    lo = max(A[i][0], B[j][0])
    hi = min(A[i][1], B[j][1])
    if lo <= hi:
        result.append([lo, hi])
    if A[i][1] < B[j][1]:
        i += 1
    else:
        j += 1
```

---

## 2. 56. Merge Intervals `[2/27][4/2]`

**Pattern:** Sort by start. Iterate and merge if current interval overlaps the last merged one.

**Key Insight:** Overlap condition: `curr.start <= last.end`. If overlap, extend `last.end = max(last.end, curr.end)`.

---

## 3. 939. Minimum Area Rectangle `[5/31]`

**Pattern:** Fix two points as the diagonal of a rectangle. Check if the other two corners exist in a set.

**Key Insight:** For each pair of points `(x1,y1)` and `(x2,y2)` with `x1 != x2` and `y1 != y2`, check if `(x1,y2)` and `(x2,y1)` are in the point set. Area = `abs(x2-x1) * abs(y2-y1)`.

Use a `set` of tuples for O(1) lookup.

---
