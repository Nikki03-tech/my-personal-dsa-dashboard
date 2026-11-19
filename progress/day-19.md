# Day 19 — Trees: DFS, recursion and BSTs

**Date:** November 19, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4/4 online judge submissions accepted (confirmed November 19, 2026).


## Updated dashboard assignments — four questions per day

> These are the four assigned problems shown on the current dashboard. All four submissions are now confirmed accepted; the checkboxes below record that status.

### LeetCode
- [x] **Q1 — [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)**
- [x] **Q2 — [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)**

### HackerRank
- [x] **Q1 — [Tree: Height of a Binary Tree](https://www.hackerrank.com/challenges/tree-height-of-a-binary-tree/problem)**
- [x] **Q2 — [Tree: Preorder Traversal](https://www.hackerrank.com/challenges/tree-preorder-traversal/problem)**

## Today's learning goals
- [x] Tree nodes, root, leaves and height
- [x] DFS: preorder, inorder and postorder
- [x] BST ordering property
- [x] Recursive base cases

## Core practice
- **LeetCode:** [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) — Easy
- **HackerRank / practice:** [Tree: Height of a Binary Tree](https://www.hackerrank.com/challenges/tree-height-of-a-binary-tree/problem)

## How to approach it
For maximum depth, return zero for an empty node and one plus the larger depth of the children. A BST validation must respect allowed value ranges throughout each subtree.

## Edge cases to test
Test an empty tree, a single node, a skewed tree and a balanced tree.

## Optional stretch
[Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)
Optional Medium: use lower and upper bounds rather than checking only parent-child pairs.

## Complexity review
- [x] State the time complexity and explain which input size it depends on.
- [x] State auxiliary space separately from output space.
- [x] Explain whether sorting, hashing, or an extra data structure changes the trade-off.

## Daily checklist
- [x] Read the concept and trace a small example by hand.
- [x] Attempt the core LeetCode problem independently.
- [x] Attempt the HackerRank exercise or custom Python drill.
- [x] Test the edge cases above.
- [x] Explain the approach aloud without reading the solution.
- [x] Revisit this pattern after 2–3 days.

## Confirmed submission results

**Submission confirmation (November 19, 2026):** All four problems were reported Accepted.
- [x] LeetCode — Maximum Depth of Binary Tree
- [x] LeetCode — Validate Binary Search Tree
- [x] HackerRank — Tree Height
- [x] HackerRank — Preorder Traversal

**Key revision:** DFS explores a branch recursively. Maximum depth counts nodes; HackerRank tree height counts edges. BST validation carries lower and upper bounds through the whole subtree. Preorder is root → left → right.

## My attempt notes
**First approach:**  

**Where I got stuck:**  

**Hints used:**  

**Key insight / final approach:**  

**Time complexity:**  

**Auxiliary space complexity:**  

**What I learned / what to revise:**  
