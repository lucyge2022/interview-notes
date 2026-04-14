# Stack

---

## 1. 227. Basic Calculator II `[3/9][3/26][5/17]`

**Pattern:** Stack-based. Process number tokens with their preceding operator sign.

**Key Insight:** Track `sign` (`+`, `-`, `*`, `/`). On `+`/`-`, push signed number. On `*`/`/`, pop top and push result.

```
num = 0, sign = '+'
for ch in s + '+':   # trailing '+' flushes last number
    if ch.isdigit():
        num = num * 10 + int(ch)
    elif ch in '+-*/':
        if sign == '+': stack.append(num)
        elif sign == '-': stack.append(-num)
        elif sign == '*': stack.append(stack.pop() * num)
        elif sign == '/': stack.append(int(stack.pop() / num))
        sign = ch
        num = 0
return sum(stack)
```

---

## 2. 31. Next Permutation `[3/6][3/16][6/5]`

**Pattern:** Three-step in-place algorithm.

**Key Insight:**
1. Find rightmost index `i` where `nums[i] < nums[i+1]` (the "dip").
2. Find rightmost index `j` where `nums[j] > nums[i]`. Swap `nums[i]` and `nums[j]`.
3. Reverse from `i+1` to end.

> If no such `i` exists (fully descending), reverse the entire array.

---

## 3. 1047. Remove All Adjacent Duplicates in String `[3/13]`

**Pattern:** Stack — push char, pop if top equals current char.

---

## 4. 1209. Remove All Adjacent Duplicates in String II `[3/13]`

**Pattern:** Stack of `(char, count)` pairs. If count reaches k, pop.

---
