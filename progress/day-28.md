# Day 28 — Dynamic programming: 1D and 2D foundations

**Date:** November 28, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4/4 online-judge submissions reported Accepted on November 25, 2026.

## Confirmed dashboard assignments — 4/4 Accepted

### LeetCode
- [x] **Q1 — [House Robber](https://leetcode.com/problems/house-robber/)** — Accepted
- [x] **Q2 — [Coin Change](https://leetcode.com/problems/coin-change/)** — Accepted

### HackerRank
- [x] **Q1 — [Max Array Sum / The Maximum Subarray](https://www.hackerrank.com/challenges/maxsubarray/problem)** — Accepted
- [x] **Q2 — [The Coin Change Problem](https://www.hackerrank.com/challenges/coin-change/problem)** — Accepted

**Submission confirmation:** The user reported that all four questions for Day 28 were run, submitted, and all test cases passed on November 25, 2026. This day was completed ahead of its scheduled calendar date.

**Digital study notes:** [Open Day 28 notes](../notes/day-28.md)

## 1. Concepts Learned

- [x] DP states and recurrence
- [x] Base cases
- [x] Memoization and tabulation
- [x] Minimum-coin DP versus combination-counting DP
- [x] Kadane's algorithm and non-contiguous maximum sum

## 2. Important Logic

House Robber uses a take-or-skip recurrence. LeetCode Coin Change minimizes coin count. The HackerRank maxsubarray challenge returns both contiguous and non-contiguous maximum sums. HackerRank Coin Change counts combinations with the coin loop outside.

## 3. Edge Cases Reviewed

Test all-negative arrays, unreachable coin amounts, amount zero, small arrays, and target amounts below the smallest coin.

## 4. Coding Problems Completed

- [x] LeetCode Q1 — House Robber
- [x] LeetCode Q2 — Coin Change
- [x] HackerRank Q1 — Max Array Sum / The Maximum Subarray
- [x] HackerRank Q2 — The Coin Change Problem

## 5. Time and Space Complexity

House Robber O(n)/O(1). Both coin-change tasks O(A × C) time and O(A) space. HackerRank Maximum Subarray O(n) time and O(1) auxiliary space.

## 6. Mock Interview Questions and Answers

1. **What is a DP state?** The stored answer to a smaller subproblem.
2. **What is a recurrence?** A relationship between the current state and earlier states.
3. **Memoization versus tabulation?** Top-down cached recursion versus bottom-up table filling.
4. **How do the Coin Change tasks differ?** LeetCode minimizes coin count; HackerRank counts combinations.
5. **What is Kadane's algorithm?** A linear method for finding the maximum contiguous subarray sum.
6. **What does HackerRank maxsubarray return?** Both contiguous and non-contiguous maximum sums.

## 7. Key Learning

Dynamic Programming defines states and recurrences to reuse smaller answers. Similar-looking tasks may have different goals: minimize a coin count, count combinations, or maximize contiguous and non-contiguous sums.

**Day 28 completed — 4/4 Accepted.**
