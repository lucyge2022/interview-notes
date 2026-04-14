# Trees

---

## 1. 236. Lowest Common Ancestor of a Binary Tree `[1/29][5/10]`

**Pattern:** DFS post-order — recurse left and right, bubble up results.

**Key Insight:** If both subtrees return non-null, current node is the LCA. If only one side returns non-null, propagate it up.

---

## 2. 938. Range Sum of BST `[2/15][3/2][3/26][5/10]`

**Pattern:** BST property pruning — only recurse into subtrees that overlap `[low, high]`.

**Key Insight:** Skip left subtree if `root.val <= low`, skip right subtree if `root.val >= high`.

---

## 3. 314. Binary Tree Vertical Order Traversal `[2/16][3/9][5/10][5/17][6/5]`

**Pattern:** BFS with column index tracking. Use a `deque` and a `dict[col -> list]`.

**Key Insight:** Pass `(node, col)` pairs in the BFS queue. Left child gets `col-1`, right child gets `col+1`. Sort keys at the end.

> BFS guarantees top-to-bottom order within each column without extra sorting on row.

---

## 4. 270. Closest Binary Search Tree Value `[2/22][5/17]`

**Pattern:** BST traversal — walk down the tree, track minimum absolute difference.

**Key Insight:** At each node, compare `abs(node.val - target)` and move left or right based on comparison with target. No need for full traversal.

---

## 5. 429. N-ary Tree Level Order Traversal `[2/27][5/10]`

**Pattern:** BFS with a queue. For each node dequeued, extend queue with all children.

---

## 6. 199. Binary Tree Right Side View `[2/27][3/27]`

**Pattern:** BFS level-order — take the last node of each level.

---

## 7. 958. Check Completeness of a Binary Tree `[6/1]`

**Pattern:** BFS level-order. Once a `null` node is seen, no non-null node should appear after it.

**Key Insight:** Use a flag `end = False`. When you see `None`, set `end = True`. If you see any non-None node after `end` is set, return False.

---

## 8. 1161. Maximum Level Sum of a Binary Tree `[3/2][3/27]`

**Pattern:** BFS level-order — accumulate sum per level, track max.

---

## 9. 235. Lowest Common Ancestor of a BST `[3/13][3/26]`

**Pattern:** Exploit BST ordering. If both `p` and `q` are less than root, go left. If both greater, go right. Otherwise, root is the LCA.

---

## 10. 1650. Lowest Common Ancestor of a Binary Tree III `[3/13]`

**Pattern:** Two-pointer on parent pointers (like linked list intersection). Walk both nodes up to root, then restart from the other's starting point.

**Key Insight:** Same trick as finding intersection of two linked lists — when one pointer hits `None`, redirect it to the other node's start.

---

## 11. 426. Convert Binary Search Tree to Sorted Doubly Linked List `[3/11]`

**Pattern:** In-order DFS (left → node → right). Thread nodes together as you visit them. Track `prev` and `head` as outer state.

**Key Insight:** After full traversal, connect `head.left = prev` and `prev.right = head` to make it circular.

---

## 12. 116. Populating Next Right Pointers in Each Node `[3/19]`

**Pattern:** BFS level-order, or use the already-populated `next` pointers from the previous level to traverse without extra space.

---

## 13. 129. Sum Root to Leaf Numbers `[3/19]`

**Pattern:** DFS preorder. Carry running number `curr = curr * 10 + node.val` down. Add to total at leaf.

---
