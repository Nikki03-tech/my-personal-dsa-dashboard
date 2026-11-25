# Day 27 — Greedy Algorithms

**Date:** November 27, 2026 | **Language:** Python  
**Status:** COMPLETED — 4/4 Accepted (user-confirmed November 25, 2026).

## 1. Concepts Learned
- A greedy algorithm makes a locally optimal choice at each step.
- Sorting can help select items in a useful order.
- A greedy choice needs justification.
- Running totals and maximum reach can maintain feasibility.

## 2. Questions, Python Solutions and Explanations

### Q1 — LeetCode: [Jump Game](https://leetcode.com/problems/jump-game/)

Each array element is the maximum jump length from that position. Return True if the last index is reachable.

```python
class Solution:
    def canJump(self, nums):
        farthest = 0
        for i in range(len(nums)):
            if i > farthest:
                return False
            farthest = max(farthest, i + nums[i])
            if farthest >= len(nums) - 1:
                return True
        return True
```

**Example:** `[2, 3, 1, 1, 4]` returns True.

**Explanation:** `farthest` stores the maximum index reachable. If the current index is beyond it, the end cannot be reached. Otherwise extend the reachable range.

**Complexity:** O(n) time, O(1) space.

### Q2 — LeetCode: [Gas Station](https://leetcode.com/problems/gas-station/)

Given fuel at each station and the cost of travelling to the next station, find a valid starting station or return -1.

```python
class Solution:
    def canCompleteCircuit(self, gas, cost):
        total = 0
        tank = 0
        start = 0

        for i in range(len(gas)):
            difference = gas[i] - cost[i]
            total += difference
            tank += difference

            if tank < 0:
                start = i + 1
                tank = 0

        if total < 0:
            return -1
        return start
```

**Example:** gas = [1,2,3,4,5], cost = [3,4,5,1,2] returns 3.

**Explanation:** `total` checks whether the whole circuit has enough fuel. `tank` checks the current candidate. If the tank becomes negative, discard that candidate and start after the failed station. If total is negative, no solution exists.

**Complexity:** O(n) time, O(1) space.

### Q3 — HackerRank: [Mark and Toys](https://www.hackerrank.com/challenges/mark-and-toys/problem)

Given toy prices and a budget, find the maximum number of toys purchasable.

```python
def maximumToys(prices, k):
    prices.sort()
    total = 0
    count = 0

    for price in prices:
        if total + price <= k:
            total += price
            count += 1
        else:
            break

    return count
```

**Example:** prices = [1,12,5,111,200,1000,10], k = 50 returns 4.

**Explanation:** Sort ascending and buy the cheapest toys while the total remains within budget. Stop when the next toy is too expensive.

**Complexity:** O(n log n) time due to sorting; sorting memory is implementation-dependent.

### Q4 — HackerRank: [Greedy Florist](https://www.hackerrank.com/challenges/greedy-florist/problem)

Given k friends and flower prices, minimize total cost. A friend's next flower has multiplier one plus the number of flowers already bought by that friend.

```python
def getMinimumCost(k, c):
    c.sort(reverse=True)
    total = 0

    for i, price in enumerate(c):
        multiplier = (i // k) + 1
        total += multiplier * price

    return total
```

**Example:** k = 3, c = [2,5,6] returns 13.

**Explanation:** Sort descending so expensive flowers get the smallest multipliers. The multiplier increases after every k purchases.

**Complexity:** O(n log n) time due to sorting; sorting memory is implementation-dependent.

## 3. Mistakes to Avoid
- Jump Game: track farthest reachable index, not only the next position.
- Gas Station: check total fuel and reset the candidate when tank becomes negative.
- Mark and Toys: sort ascending.
- Greedy Florist: sort descending.
- Justify why each greedy choice leads to the optimal result.

## 4. Coding Problems Completed — 4/4 Accepted
- [x] LeetCode — Jump Game
- [x] LeetCode — Gas Station
- [x] HackerRank — Mark and Toys
- [x] HackerRank — Greedy Florist

**Confirmation:** All four submissions were reported Accepted on November 25, 2026.

## 5. Complexity Summary
| Problem | Time | Auxiliary Space |
|---|---|---|
| Jump Game | O(n) | O(1) |
| Gas Station | O(n) | O(1) |
| Mark and Toys | O(n log n) | Sorting-dependent |
| Greedy Florist | O(n log n) | Sorting-dependent |

## 6. Mock Interview Questions
1. What is a Greedy Algorithm? A method that makes a locally optimal choice at each step.
2. What does farthest reach mean? The maximum index reachable so far.
3. Why reset the Gas Station candidate? A negative tank rules out that candidate segment.
4. Why sort Mark and Toys ascending? To maximize the number bought.
5. Why sort Greedy Florist descending? To assign smaller multipliers to expensive flowers.
6. Does greedy work for every optimization problem? No; the choice rule must be justified.

## 7. Key Learning
Jump Game tracks reachability, Gas Station tracks fuel feasibility, Mark and Toys buys the cheapest items first, and Greedy Florist assigns the lowest multipliers to the highest prices.

**Day 27 completed — 4/4 Accepted.**
