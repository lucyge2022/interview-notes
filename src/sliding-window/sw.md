# Sliding Window

---

## ⚠️ 1004. Max Consecutive Ones III `[2/27][3/6][5/10][5/18][6/3]`

> **This one bites every cycle. Review it first.**

**Pattern:** Sliding window with two pointers `st` and `ed`. Maintain a count of zeros used (`k` flips remaining).

**Key Insight:** Expand `ed` freely. When `k < 0`, shrink from `st`.

```
st = 0
for ed in range(len(nums)):
    if nums[ed] == 0:
        k -= 1
    while k < 0:
        if nums[st] == 0:
            k += 1
        st += 1
return ed - st + 1
```

**Critical trap:**
> When shrinking the `st` pointer, do NOT use `ed` to judge whether `nums[st]` was 0 — you must check `nums[st]` directly. The `ed` pointer position is irrelevant at shrink time.

> When retrieving `st` to restore k, increment k **only if `nums[st]` was originally 0** — then always advance `st`.

**Why it's tricky:** The instinct is to check the current `ed` value when deciding whether to increment `k` at shrink time. That's wrong — `ed` has already moved.

---
