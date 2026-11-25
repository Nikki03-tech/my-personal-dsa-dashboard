# Day 30 — Final mixed mock and pattern review

**Date:** November 30, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4/4 online-judge submissions reported Accepted on November 25, 2026.

## Confirmed dashboard assignments — 4/4 Accepted

### LeetCode
- [x] **Q1 — [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)** — Accepted
- [x] **Q2 — [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)** — Accepted

### HackerRank
- [x] **Q1 — [New Year Chaos](https://www.hackerrank.com/challenges/new-year-chaos/problem)** — Accepted
- [x] **Q2 — [Minimum Swaps 2](https://www.hackerrank.com/challenges/minimum-swaps-2/problem)** — Accepted

**Submission confirmation:** The user reported that all four questions for Day 30 were run, submitted, and all test cases passed on November 25, 2026. This day was completed ahead of its scheduled calendar date.

**Digital study notes:** [Open Day 30 notes](../notes/day-30.md)

## 1. Concepts Learned

- [x] Choose a pattern from an unfamiliar statement
- [x] Prefix and suffix products
- [x] Two-pointer maximum boundaries
- [x] Bribe and inversion counting
- [x] Correct-position cyclic swapping

## 2. Important Logic

Use two passes for prefix/suffix products. Use two pointers and left/right maxima for trapped water. Count overtaking people within the allowed two-bribe range for New Year Chaos. Place each permutation value at index value - 1 for Minimum Swaps 2.

## 3. Edge Cases Reviewed

Test zero values in product arrays, monotonic and flat height arrays, a one-person queue, a queue with a person bribing more than twice, and already sorted or reverse permutations.

## 4. Coding Problems Completed

- [x] LeetCode Q1 — Product of Array Except Self
- [x] LeetCode Q2 — Trapping Rain Water
- [x] HackerRank Q1 — New Year Chaos
- [x] HackerRank Q2 — Minimum Swaps 2

## 5. Time and Space Complexity

All four solutions run in O(n) time and O(1) auxiliary space, excluding the Product of Array Except Self output.

## 6. Mock Interview Questions and Answers

1. **What is a prefix product?** The product of elements before the current index.
2. **What is a suffix product?** The product of elements after the current index.
3. **How is trapped water determined?** By the smaller of left and right maximum boundaries.
4. **What makes a queue Too chaotic?** A person moved forward by more than two positions.
5. **How does Minimum Swaps 2 find a target index?** Value x belongs at index x - 1.

## 7. Key Learning

The final mixed set combines prefix/suffix products, two pointers, inversion counting and correct-position swapping. Pattern recognition and explaining invariants are essential interview skills.

**Day 30 completed — 4/4 Accepted.**
