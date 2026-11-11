# Day 7 — Prefix Sums and Subarray Sums

**Date:** November 7, 2026 | **Language:** Python

## 1. Prefix sum in simple words
A prefix sum is a running total. It stores the sum from the start of the array through each position.

Example: `nums = [2, 4, 1, 3]` gives prefix sums `[2, 6, 7, 10]`.

```python
prefix = [0]
for number in nums:
    prefix.append(prefix[-1] + number)
```

Starting with zero makes range calculations easier. The sum from index `left` to `right` (inclusive) is:

```python
prefix[right + 1] - prefix[left]
```

Example: for `[2, 4, 1, 3]`, the sum at indexes 1 through 2 is `prefix[3] - prefix[1] = 7 - 2 = 5`.

## 2. Pivot Index
A pivot is an index where the sum on the left equals the sum on the right. The pivot value itself is not included.

```python
total = sum(nums)
left_sum = 0

for i in range(len(nums)):
    right_sum = total - left_sum - nums[i]
    if left_sum == right_sum:
        return i
    left_sum += nums[i]

return -1
```

Why? Total = left + current + right. So right = total - left - current.

## 3. Difference array
Useful when many operations add a value to a whole range. Instead of updating every element in the range:

```python
diff[left] += value
if right + 1 < n:
    diff[right + 1] -= value
```

After all updates, take a running sum of the difference array to rebuild the final values.

## 4. Assigned questions
- [Find Pivot Index — LeetCode](https://leetcode.com/problems/find-pivot-index/)
- [Range Sum Query - Immutable — LeetCode](https://leetcode.com/problems/range-sum-query-immutable/)
- [Array Manipulation — HackerRank](https://www.hackerrank.com/challenges/crush/problem)
- [Sherlock and Array — HackerRank](https://www.hackerrank.com/challenges/sherlock-and-array/problem)

## 5. Complexity
- Build prefix sums: O(n) time, O(n) extra space.
- Pivot scan after total is known: O(n) time, O(1) extra space.
- One range-sum query after preprocessing: O(1) time.
- Difference-array reconstruction: O(n) time.

## 6. Common mistakes
- Forgetting Python uses zero-based indexes.
- With a leading zero, use `prefix[right + 1] - prefix[left]`.
- Do not include the pivot element in either side.
- Check the pivot before adding the current value to `left_sum`.

## 7. Interview revision
**What is a prefix sum?** A running total that helps answer range-sum questions quickly.  
**Why calculate total once for Pivot Index?** To derive the right sum without another loop.  
**What does a difference array improve?** Repeated range updates.

**Key takeaway:** Reuse information from earlier elements instead of summing the same ranges again and again.
