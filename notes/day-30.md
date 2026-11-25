# Day 30 — Final Mixed Mock and Pattern Review

**Date:** November 30, 2026 | **Language:** Python  
**Status:** COMPLETED — 4/4 Accepted (user-confirmed November 25, 2026).

## 1. Concepts Learned
- Prefix products summarize all values before an index.
- Suffix products summarize all values after an index.
- Two pointers can process opposite ends of an array.
- Trapped water depends on the smaller boundary maximum.
- New Year Chaos counts overtaking inversions and checks the two-bribe limit.
- Minimum Swaps 2 places each value at its target index.

## 2. Questions, Python Solutions and Explanations

### Q1 — LeetCode: [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

Return the product of every array element except the element at each index. Do not use division; solve in O(n) time.

```python
class Solution:
    def productExceptSelf(self, nums):
        n = len(nums)
        result = [1] * n

        prefix = 1
        for i in range(n):
            result[i] = prefix
            prefix *= nums[i]

        suffix = 1
        for i in range(n - 1, -1, -1):
            result[i] *= suffix
            suffix *= nums[i]

        return result
```

**Example:** `[1,2,3,4]` returns `[24,12,8,6]`.

**Explanation:** The first pass stores products to the left. The second pass multiplies products to the right. This also handles zero values without division.

**Complexity:** O(n) time; O(1) auxiliary space excluding output.

### Q2 — LeetCode: [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

Given bar heights, calculate the amount of rainwater trapped.

```python
class Solution:
    def trap(self, height):
        left = 0
        right = len(height) - 1
        left_max = 0
        right_max = 0
        water = 0

        while left < right:
            if height[left] <= height[right]:
                if height[left] >= left_max:
                    left_max = height[left]
                else:
                    water += left_max - height[left]
                left += 1
            else:
                if height[right] >= right_max:
                    right_max = height[right]
                else:
                    water += right_max - height[right]
                right -= 1

        return water
```

**Example:** `[0,1,0,2,1,0,1,3,2,1,2,1]` returns 6.

**Explanation:** Water at an index is limited by the smaller of its left and right maximum heights, minus the current height. Process the side with the smaller current boundary and move inward.

**Complexity:** O(n) time and O(1) space.

### Q3 — HackerRank: [New Year Chaos](https://www.hackerrank.com/challenges/new-year-chaos/problem)

Each person can bribe the person immediately ahead and move forward one position. Count minimum bribes, or print Too chaotic if anyone moved forward more than two places.

```python
def minimumBribes(q):
    bribes = 0

    for i in range(len(q) - 1, -1, -1):
        if q[i] - (i + 1) > 2:
            print("Too chaotic")
            return

        for j in range(max(0, q[i] - 2), i):
            if q[j] > q[i]:
                bribes += 1

    print(bribes)
```

**Examples:** `[2,1,5,3,4]` prints 3. `[2,5,1,3,4]` prints Too chaotic.

**Explanation:** Traverse backward. `q[i] - (i + 1)` measures how far the person moved forward. If it exceeds two, stop. Otherwise count overtaking people in the only possible range: from `max(0, q[i] - 2)` to `i - 1`.

**Complexity:** O(n) time because the inner loop checks at most three positions per person; O(1) auxiliary space. The function prints the answer.

### Q4 — HackerRank: [Minimum Swaps 2](https://www.hackerrank.com/challenges/minimum-swaps-2/problem)

Given a permutation of 1 through n, find the minimum swaps needed to sort it.

```python
def minimumSwaps(arr):
    swaps = 0
    i = 0

    while i < len(arr):
        if arr[i] != i + 1:
            correct_index = arr[i] - 1
            arr[i], arr[correct_index] = (
                arr[correct_index],
                arr[i]
            )
            swaps += 1
        else:
            i += 1

    return swaps
```

**Example:** `[4,3,1,2]` returns 3.

**Explanation:** Value x belongs at index x - 1. If the current value is wrong, swap it directly into its target index. Check the same index again after a swap; advance only when it is correct.

**Complexity:** O(n) time and O(1) auxiliary space.

## 3. Mistakes to Avoid
- Product Except Self: do not use division; use prefix and suffix passes.
- Trapping Rain Water: process the side with the smaller current boundary.
- New Year Chaos: verify the two-bribe limit before counting overtakes.
- New Year Chaos: print Too chaotic and stop for an invalid queue.
- Minimum Swaps 2: target index is value minus one; do not advance immediately after swapping.

## 4. Coding Problems Completed — 4/4 Accepted
- [x] LeetCode — Product of Array Except Self
- [x] LeetCode — Trapping Rain Water
- [x] HackerRank — New Year Chaos
- [x] HackerRank — Minimum Swaps 2

**Confirmation:** All four submissions were reported Accepted on November 25, 2026.

## 5. Complexity Summary
| Problem | Time | Auxiliary Space |
|---|---|---|
| Product of Array Except Self | O(n) | O(1), excluding output |
| Trapping Rain Water | O(n) | O(1) |
| New Year Chaos | O(n) | O(1) |
| Minimum Swaps 2 | O(n) | O(1) |

## 6. Mock Interview Questions
1. What is a prefix product? Product of elements before an index.
2. What is a suffix product? Product of elements after an index.
3. Why use two passes for Product Except Self? One builds left products; the other adds right products.
4. How is trapped water determined? By the smaller of left and right maximum boundaries.
5. What makes a queue Too chaotic? A person moved forward more than two positions.
6. Why check `q[i] - (i + 1)`? It measures forward displacement.
7. Where does value x belong in Minimum Swaps 2? At index x - 1.

## 7. Key Learning
The final mixed set combines prefix/suffix products, two pointers, inversion counting and correct-position swapping. Recognize the pattern, explain the invariant, test edge cases and state complexity.

**Day 30 completed — 4/4 Accepted.**
