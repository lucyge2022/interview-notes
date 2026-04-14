# Dynamic Programming

---

## 1. 50. Pow(x, n) — Binary Exponentiation `[2/22][6/3]`

**Pattern:** Divide and conquer. `pow(x, n) = pow(x, n//2)^2`, with one extra `* x` if n is odd.

**Key Insight:** The final result should be one exponential term multiplied by any remainder factor — it's not a sum, it's a product chain.

```python
def myPow(x, n):
    if n < 0:
        x, n = 1/x, -n
    if n == 0:
        return 1
    half = myPow(x, n // 2)
    return half * half if n % 2 == 0 else half * half * x
```

> Think of it as: compute the "squarable half", then optionally multiply one more `x` for odd exponents.

---

## 2. 63. Unique Paths II `[2/27][6/3]`

**Pattern:** 2D DP. `dp[i][j] = dp[i-1][j] + dp[i][j-1]` if cell is not an obstacle, else 0.

**Key Insight:** Initialize `dp[0][0] = 1` if not blocked, then propagate. Obstacles block both the cell and all paths through it.

---

## 3. 714. Best Time to Buy and Sell Stock with Transaction Fee `[3/22][3/26]`

**Pattern:** State machine DP with two states: `hold` (holding stock) and `cash` (no stock).

```
hold = max(hold, cash - price)
cash = max(cash, hold + price - fee)
```

**Key Insight:** Transition happens simultaneously — use previous values of `hold` and `cash` each step.

---
