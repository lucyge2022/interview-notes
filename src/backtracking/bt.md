# Backtracking

---

## ⚠️ 1. 39. Combination Sum `[2/27][3/25][6/3]`

> **Train this one. The template here applies broadly.**

**Pattern:** Backtracking with a running `start` index to avoid re-using earlier elements.

**Key Insight:** Each recursive call passes `start=i` (not `i+1`) to allow the same element to be reused.

```python
def backtrack(start, curr, remaining):
    if remaining == 0:
        result.append(curr[:])
        return
    for i in range(start, len(candidates)):
        if candidates[i] > remaining:
            break   # pruning (sort first)
        curr.append(candidates[i])
        backtrack(i, curr, remaining - candidates[i])
        curr.pop()
```

**Template to remember:**
```
sort candidates
backtrack(start=0, path=[], remaining=target)
  loop i from start to end:
    prune if too large
    choose candidates[i]
    recurse with start=i (allow reuse) or i+1 (no reuse)
    unchoose
```

---

## ⚠️ 2. 78. Subsets `[3/13][3/26][3/27][5/10]`

> **Train this one.**

**Pattern:** Backtracking. At each index, decide include or skip.

```python
def backtrack(start, curr):
    result.append(curr[:])
    for i in range(start, len(nums)):
        curr.append(nums[i])
        backtrack(i + 1, curr)
        curr.pop()
```

**Key difference from 39:** Pass `i+1` — each element used at most once, no repetition.

---
