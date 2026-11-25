# Day 29 — Bit manipulation and mathematical algorithms

**Date:** November 29, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4/4 online-judge submissions reported Accepted on November 25, 2026.

## Confirmed dashboard assignments — 4/4 Accepted

### LeetCode
- [x] **Q1 — [Single Number](https://leetcode.com/problems/single-number/)** — Accepted
- [x] **Q2 — [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)** — Accepted

### HackerRank
- [x] **Q1 — [Flipping Bits](https://www.hackerrank.com/challenges/flipping-bits/problem)** — Accepted
- [x] **Q2 — [Sum vs XOR](https://www.hackerrank.com/challenges/sum-vs-xor/problem)** — Accepted

**Submission confirmation:** The user reported that all four questions for Day 29 were run, submitted, and all test cases passed on November 25, 2026. This day was completed ahead of its scheduled calendar date.

**Digital study notes:** [Open Day 29 notes](../notes/day-29.md)

## 1. Concepts Learned

- [x] Binary representation and AND/OR/XOR
- [x] XOR cancellation
- [x] n & (n - 1) set-bit removal
- [x] 32-bit masks
- [x] Significant zero bits and Sum vs XOR

## 2. Important Logic

XOR all values to find the unpaired number. Repeatedly clear the rightmost set bit to count ones. Use a 32-bit all-ones mask to flip bits. Count significant zero bits to solve Sum vs XOR.

## 3. Edge Cases Reviewed

Test one number, duplicate pairs, zero, 32-bit boundary values, and numbers whose binary representations contain several zero bits.

## 4. Coding Problems Completed

- [x] LeetCode Q1 — Single Number
- [x] LeetCode Q2 — Number of 1 Bits
- [x] HackerRank Q1 — Flipping Bits
- [x] HackerRank Q2 — Sum vs XOR

## 5. Time and Space Complexity

Single Number O(n)/O(1). Number of 1 Bits at most 32 iterations. Flipping Bits O(1). Sum vs XOR O(log n) time and O(1) space.

## 6. Mock Interview Questions and Answers

1. **What is XOR?** It returns 1 when two bits differ and 0 when they are equal.
2. **Why does XOR solve Single Number?** Duplicate pairs cancel.
3. **What does n & (n - 1) do?** Removes the rightmost set bit.
4. **What is Hamming Weight?** The number of one bits.
5. **Why use a 32-bit mask?** To keep Flipping Bits within exactly 32 bits.
6. **Why count zero bits in Sum vs XOR?** Those positions allow choices without causing a carry.

## 7. Key Learning

Bit manipulation works directly with binary values. XOR cancels duplicates, n & (n - 1) clears a set bit, masks control bit width, and zero-bit counting solves Sum vs XOR.

**Day 29 completed — 4/4 Accepted.**
