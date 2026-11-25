# Day 29 — Bit Manipulation and Mathematical Algorithms

**Date:** November 29, 2026 | **Language:** Python  
**Status:** COMPLETED — 4/4 Accepted (user-confirmed November 25, 2026).

## 1. Concepts Learned
- Binary represents values using 0 and 1.
- AND (`&`), OR (`|`), XOR (`^`), NOT (`~`), left shift (`<<`) and right shift (`>>`) are bitwise operations.
- XOR cancels equal pairs.
- `n & (n - 1)` removes the rightmost set bit.
- A mask can limit operations to 32 bits.

## 2. Questions, Python Solutions and Explanations

### Q1 — LeetCode: [Single Number](https://leetcode.com/problems/single-number/)

Every number appears twice except one. Find the unique number in linear time and constant extra space.

```python
class Solution:
    def singleNumber(self, nums):
        result = 0
        for num in nums:
            result ^= num
        return result
```

**Example:** `[4,1,2,1,2]` returns 4.

**Explanation:** `a ^ a = 0`, and `a ^ 0 = a`. Duplicate pairs cancel, leaving the unique value.

**Complexity:** O(n) time, O(1) space.

### Q2 — LeetCode: [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)

Count the set bits in a 32-bit unsigned integer (Hamming Weight).

```python
class Solution:
    def hammingWeight(self, n):
        count = 0
        while n:
            n = n & (n - 1)
            count += 1
        return count
```

**Example:** 11 is binary 1011, so the answer is 3.

**Explanation:** Each `n & (n - 1)` removes the rightmost set bit. Count the iterations until n is zero.

**Complexity:** At most 32 iterations; O(1) space.

### Q3 — HackerRank: [Flipping Bits](https://www.hackerrank.com/challenges/flipping-bits/problem)

Flip all 32 bits of an unsigned 32-bit integer.

```python
def flippingBits(n):
    return n ^ 0xFFFFFFFF
```

Alternative:

```python
def flippingBits(n):
    return (~n) & 0xFFFFFFFF
```

**Example:** Input 1 returns 4294967294.

**Explanation:** `0xFFFFFFFF` contains 32 one bits. XOR flips every bit. The alternative masks the complement so the answer contains only 32 bits; Python integers do not have fixed 32-bit width.

**Complexity:** O(1) time and space for a fixed-width input.

### Q4 — HackerRank: [Sum vs XOR](https://www.hackerrank.com/challenges/sum-vs-xor/problem)

Count non-negative x such that `n + x == n ^ x`.

```python
def sumXor(n):
    zero_bits = 0

    while n > 0:
        if (n & 1) == 0:
            zero_bits += 1
        n >>= 1

    return 1 << zero_bits
```

**Examples:** sumXor(5) returns 2; sumXor(10) returns 4; sumXor(0) returns 1.

**Explanation:** Addition and XOR match when no carry is generated. At a 1 bit of n, x must have 0. At each zero bit below the highest set bit, x can have either value. Every such position doubles the number of choices.

**Complexity:** O(log n) time, O(1) space.

## 3. Mistakes to Avoid
- Do not confuse XOR with OR.
- Remember `a ^ a = 0`.
- Initialize the XOR accumulator to zero.
- `n & (n - 1)` clears one set bit.
- Use a 32-bit mask in Flipping Bits.
- In Sum vs XOR, do not count unlimited leading zeros.

## 4. Coding Problems Completed — 4/4 Accepted
- [x] LeetCode — Single Number
- [x] LeetCode — Number of 1 Bits
- [x] HackerRank — Flipping Bits
- [x] HackerRank — Sum vs XOR

**Confirmation:** All four submissions were reported Accepted on November 25, 2026.

## 5. Complexity Summary
| Problem | Time | Auxiliary Space |
|---|---|---|
| Single Number | O(n) | O(1) |
| Number of 1 Bits | At most O(32) | O(1) |
| Flipping Bits | O(1) | O(1) |
| Sum vs XOR | O(log n) | O(1) |

## 6. Mock Interview Questions
1. What is XOR? It returns 1 when two bits differ.
2. What happens when a value is XORed with itself? The result is zero.
3. Why does XOR solve Single Number? Duplicate pairs cancel.
4. What does `n & (n - 1)` do? Removes the rightmost set bit.
5. What is Hamming Weight? The number of one bits.
6. Why use a 32-bit mask? To restrict the result to 32 bits.
7. Why count zero bits in Sum vs XOR? Those positions allow choices without creating a carry.

## 7. Key Learning
XOR cancels duplicate values, bit clearing counts set bits, a mask flips a fixed-width number, and significant zero-bit counting solves Sum vs XOR.

**Day 29 completed — 4/4 Accepted.**
