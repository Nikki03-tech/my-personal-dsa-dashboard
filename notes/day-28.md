# Day 28 — Dynamic Programming: 1D and 2D Foundations

**Date:** November 28, 2026 | **Language:** Python  
**Status:** COMPLETED — 4/4 Accepted (user-confirmed November 25, 2026).

## 1. Concepts Learned
- DP stores answers to smaller, overlapping subproblems.
- A state represents a smaller problem.
- A recurrence relates current states to previous states.
- Base cases provide starting values.
- Memoization is top-down caching; tabulation is bottom-up iteration.
- Space optimization keeps only the previous values when possible.
- The two Coin Change problems have different goals.
- The dashboard's Max Array Sum link is HackerRank's `maxsubarray` challenge, which returns contiguous and non-contiguous maximum sums.

## 2. Questions, Python Solutions and Explanations

### Q1 — LeetCode: [House Robber](https://leetcode.com/problems/house-robber/)

Each house contains money; adjacent houses cannot both be robbed. Find the maximum amount.

```python
class Solution:
    def rob(self, nums):
        prev_two = 0
        prev_one = 0

        for money in nums:
            current = max(prev_one, prev_two + money)
            prev_two = prev_one
            prev_one = current

        return prev_one
```

**Example:** `[2,7,9,3,1]` returns 12.

**Explanation:** Either skip the current house and keep the previous best, or rob it and add its money to the best from two houses earlier.

**Complexity:** O(n) time, O(1) space.

### Q2 — LeetCode: [Coin Change](https://leetcode.com/problems/coin-change/)

Find the minimum number of coins needed to make an amount. Each coin denomination can be used unlimited times. Return -1 if impossible.

```python
class Solution:
    def coinChange(self, coins, amount):
        dp = [amount + 1] * (amount + 1)
        dp[0] = 0

        for coin in coins:
            for value in range(coin, amount + 1):
                dp[value] = min(
                    dp[value],
                    dp[value - coin] + 1
                )

        if dp[amount] == amount + 1:
            return -1
        return dp[amount]
```

**Example:** coins = [1,2,5], amount = 11 returns 3 (5 + 5 + 1).

**Explanation:** `dp[value]` stores the minimum coins for that amount. Start with `dp[0] = 0); for each coin, test whether using it improves the answer.

**Complexity:** O(A × C) time and O(A) space, where A is amount and C is number of denominations.

### Q3 — HackerRank: [Max Array Sum / The Maximum Subarray](https://www.hackerrank.com/challenges/maxsubarray/problem)

**Important:** The dashboard label “Max Array Sum” links to HackerRank's `maxsubarray` challenge, titled The Maximum Subarray. It asks for both maximum contiguous and maximum non-contiguous sums.

```python
def maxSubarray(arr):
    # Maximum contiguous subarray sum (Kadane)
    current = arr[0]
    best = arr[0]

    for num in arr[1:]:
        current = max(num, current + num)
        best = max(best, current)

    # Maximum non-contiguous subsequence sum
    positive_sum = sum(num for num in arr if num > 0)

    if positive_sum == 0:
        positive_sum = max(arr)

    return [best, positive_sum]
```

**Example:** `[2,-1,2,3,4,-5]` returns `[10,11]`.

**Explanation:** Kadane's algorithm either starts a new contiguous subarray at the current value or extends the previous one. For the non-contiguous result, add all positive values; if none are positive, choose the largest value.

**Complexity:** O(n) time and O(1) auxiliary space.

### Q4 — HackerRank: [The Coin Change Problem](https://www.hackerrank.com/challenges/coin-change/problem)

Count the number of different combinations that make a target amount, with unlimited use of each coin type.

```python
def getWays(n, c):
    ways = [0] * (n + 1)
    ways[0] = 1

    for coin in c:
        for amount in range(coin, n + 1):
            ways[amount] += ways[amount - coin]

    return ways[n]
```

**Example:** n = 4, c = [1,2,3] returns 4 combinations: 1+1+1+1, 1+1+2, 2+2 and 1+3.

**Explanation:** `ways[amount]` stores the number of combinations. Set `ways[0] = 1). Process each coin and update amounts from that coin to the target. Keeping the coin loop outside avoids counting different orders separately.

**Complexity:** O(A × C) time and O(A) space.

## 3. Mistakes to Avoid
- House Robber: never select two adjacent houses.
- Keep the two previous DP values in the right order.
- LeetCode Coin Change minimizes coin count; HackerRank Coin Change counts combinations.
- Use `dp[0] = 0` for minimum coins and `ways[0] = 1` for counting combinations.
- In combination counting, keep the coin loop outside.
- The HackerRank `maxsubarray` task returns two values, not only a non-adjacent sum.
- For all-negative values in the non-contiguous result, use the largest element, not zero.

## 4. Coding Problems Completed — 4/4 Accepted
- [x] LeetCode — House Robber
- [x] LeetCode — Coin Change
- [x] HackerRank — Max Array Sum / The Maximum Subarray
- [x] HackerRank — The Coin Change Problem

**Confirmation:** All four submissions were reported Accepted on November 25, 2026.

## 5. Complexity Summary
| Problem | Time | Auxiliary Space |
|---|---|---|
| House Robber | O(n) | O(1) |
| LeetCode Coin Change | O(A × C) | O(A) |
| HackerRank Maximum Subarray | O(n) | O(1) |
| HackerRank Coin Change | O(A × C) | O(A) |

## 6. Mock Interview Questions
1. What is Dynamic Programming? Storing solutions to smaller subproblems.
2. What is a DP state? The stored answer to a smaller problem.
3. What is a recurrence? The relationship between current and previous states.
4. Memoization versus tabulation? Top-down cached recursion versus bottom-up table filling.
5. Difference between the Coin Change tasks? Minimum coin count versus number of combinations.
6. What is Kadane's algorithm? A linear method for maximum contiguous subarray sum.
7. What does HackerRank maxsubarray return? Contiguous and non-contiguous maximum sums.

## 7. Key Learning
DP defines states, base cases and recurrences to avoid repeated work. These tasks illustrate take-or-skip choices, minimum-count optimization, combination counting and Kadane's algorithm.

**Day 28 completed — 4/4 Accepted.**
