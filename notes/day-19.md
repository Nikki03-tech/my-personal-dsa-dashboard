# Day 19 — Trees: DFS, Recursion and BSTs

**Date:** November 19, 2026  
**Language:** Python  
**Status:** COMPLETED — 4/4 accepted (confirmed November 19, 2026)

## 1. Concepts Learned

- A **tree** is a connected hierarchical structure of nodes.
- The **root** is the top node; a **leaf** has no children.
- A **binary tree** node has at most two children: left and right.
- **DFS (Depth-First Search)** explores down a branch before moving to another branch.
- **Preorder traversal** visits root → left → right.
- A **Binary Search Tree (BST)** follows this rule: values in the left subtree are smaller and values in the right subtree are larger (for the standard unique-value version).
- Recursive tree functions solve the left and right subtrees and combine their answers.

## 2. Important Logic

**Maximum Depth — one plus the deeper child**

An empty node has depth 0. A non-empty node has depth 1 plus the maximum depth of its left and right children.

~~~python
def maxDepth(root):
    if root is None:
        return 0
    left_depth = maxDepth(root.left)
    right_depth = maxDepth(root.right)
    return 1 + max(left_depth, right_depth)
~~~

**Validate BST — carry allowed bounds**

Checking only parent-child pairs is not enough. Every node must be inside the valid range inherited from all its ancestors.

~~~python
def isValidBST(root):
    def valid(node, low, high):
        if node is None:
            return True
        if not (low < node.val < high):
            return False
        return valid(node.left, low, node.val) and valid(node.right, node.val, high)

    return valid(root, float("-inf"), float("inf"))
~~~

**HackerRank Tree Height — count edges**

HackerRank defines height as the number of edges on the longest root-to-leaf path. Therefore an empty tree returns -1, a leaf returns 0, and a parent returns one plus the greater child height.

~~~python
def height(root):
    if root is None:
        return -1
    return 1 + max(height(root.left), height(root.right))
~~~

**Preorder Traversal — root, left, right**

Visit or print the current node first, then recursively visit the left subtree and right subtree.

~~~python
def preOrder(root):
    if root is None:
        return
    print(root.info, end=" ")
    preOrder(root.left)
    preOrder(root.right)
~~~

## 3. Mistakes Corrected

- Always handle an empty root before accessing its children.
- Do not check BST validity using only the immediate parent; enforce ancestor bounds.
- Remember the height convention: maximum depth often counts nodes, while HackerRank Tree Height counts edges.
- Do not mix traversal orders. Preorder is root → left → right.

## 4. Coding Problems Completed

### LeetCode
- [x] [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) — Accepted
- [x] [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/) — Accepted

### HackerRank
- [x] [Tree: Height of a Binary Tree](https://www.hackerrank.com/challenges/tree-height-of-a-binary-tree/problem) — Accepted
- [x] [Tree: Preorder Traversal](https://www.hackerrank.com/challenges/tree-preorder-traversal/problem) — Accepted

### Concept Review
- [x] Identify root, leaf, left child and right child.
- [x] Explain DFS and preorder.
- [x] Explain the BST lower/upper-bound method.
- [x] Distinguish node-count depth from edge-count height.

## 5. Time & Space Complexity

| Problem | Time complexity | Auxiliary space |
|---|---|---|
| Maximum Depth | O(n), visits each node once | O(h) recursion stack |
| Validate BST | O(n), visits each node once | O(h) recursion stack |
| Tree Height | O(n), visits each node once | O(h) recursion stack |
| Preorder Traversal | O(n), visits each node once | O(h) recursion stack |

Here, n is the number of nodes and h is the tree height. A balanced tree has h = O(log n); a fully skewed tree can have h = O(n).

## 6. Mock Interview Questions & Answers

1. **What is a leaf node?** A node with no children.
2. **What is DFS?** A traversal that explores one branch deeply before backtracking to another branch.
3. **What is preorder traversal?** Visit root, then left subtree, then right subtree.
4. **Why use lower and upper bounds to validate a BST?** A node must satisfy restrictions from every ancestor, not just its parent.
5. **What is the time complexity of traversing a tree?** O(n), because each node is visited once.
6. **Why can recursive tree code use O(n) stack space?** In the worst case a skewed tree has height n, creating n nested calls.

## 7. Key Learning

Tree recursion follows a repeatable pattern: handle an empty node, solve the left subtree, solve the right subtree, and combine or process the result. Learn the traversal order carefully, and validate BSTs using bounds that apply to the entire subtree.
