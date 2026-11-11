# Day 09 — Two pointers and pointer invariants

**Date completed:** November 11, 2026  
**Language:** Python  
**Status:** COMPLETED — 3 accepted; Q4 solution reviewed (submission not confirmed)

## Completed questions

### LeetCode
- [x] **Q1 — [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)** — Accepted
- [x] **Q2 — [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)** — Accepted

### HackerRank
- [x] **Q1 — [Two Strings](https://www.hackerrank.com/challenges/two-strings/problem)** — Accepted
- [x] **Q2 — [Pairs](https://www.hackerrank.com/challenges/pairs/problem)** — Solution reviewed; HackerRank submission not confirmed

## Learning goals
- [x] Left and right pointers
- [x] Move one or both pointers based on a condition
- [x] Use two pointers on a sorted array
- [x] Count pairs with a target difference

## Key notes

### Two pointers
- A pointer is an index used to track a position in an array or string.
- For a palindrome, compare the characters at the left and right ends, then move both inward.
- For Two Sum II, move left rightward when the sum is too small; move right leftward when the sum is too large.
- For Pairs, sort the array, start `left = 0` and `right = 1`, then compare `arr[right] - arr[left]` with `k`.
  - Difference < k: move right forward to increase the difference.
  - Difference > k: move left forward to decrease the difference.
  - Difference == k: count the pair and move both forward.
- HackerRank Pairs guarantees distinct integers.

## HackerRank Pairs — Python solution

```python
def pairs(k, arr):
    arr.sort()
    left = 0
    right = 1
    count = 0

    while right < len(arr):
        if left == right:
            right += 1
            continue

        difference = arr[right] - arr[left]

        if difference == k:
            count += 1
            left += 1
            right += 1
        elif difference < k:
            right += 1
        else:
            left += 1

    return count
```

**Example:** `arr = [1, 5, 3, 4, 2]`, `k = 2` → sorted array `[1, 2, 3, 4, 5]` → 3 pairs.

**Time complexity:** O(n log n) because of sorting, followed by O(n) pointer traversal.  
**Auxiliary space:** O(1) for the pointer logic (Python sorting may use additional implementation space).

## What I learned
- Sorting helps make pointer movement predictable.
- If the difference is too small, move the right pointer.
- If the difference is too large, move the left pointer.
- Compare time complexity and auxiliary space separately.

## Daily status
All four assigned Day 9 problems are marked complete.