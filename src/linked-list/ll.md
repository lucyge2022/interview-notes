# Linked List

---

## 1. 146. LRU Cache `[1/29]`

**Pattern:** `OrderedDict` (or doubly-linked list + hashmap). On `get`, move to end. On `put`, evict the front if over capacity.

**Key Insight:** Use `collections.OrderedDict`. `move_to_end(key)` on access. `popitem(last=False)` to evict LRU.

---

## 2. 138. Copy List with Random Pointer `[3/9]`

**Pattern:** Two passes with a `old → new` node map.

**Key Insight:**
- **Pass 1:** Create all new nodes and store in map `old → new`.
- **Pass 2:** Wire up `.next` and `.random` using the map.

> Save the new head from the map **before** wiring — don't re-derive it. Map is `old_node → new_node`.

---
