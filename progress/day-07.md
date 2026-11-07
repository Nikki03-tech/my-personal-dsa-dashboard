# Day 07 — Prefix Sums and Subarray Sums

**Date:** November 7, 2026  
**Language:** Python  
**Status:** COMPLETED — confirmed by user ✅

## 1. Concepts covered

- Prefix sums (cumulative sums) and running totals.
- Building a prefix-sum array.
- Comparing left sum and right sum to find a pivot index.
- Deriving the right sum from the total sum, left sum, and current element.
- Using prefix sums to support range-sum queries.
- Difference arrays as an extension for efficient range updates.

## 2. Core problem-solving pattern

For a pivot-index style scan:

1. Calculate the total sum of the array.
2. Initialize the running left sum to zero.
3. At each index, calculate the right sum as:

   `right_sum = total_sum - left_sum - nums[i]`

4. Compare the left and right sums.
5. If they are equal, the current index is a pivot.
6. Add the current element to the left sum before moving to the next index.

The key idea is to reuse a total calculated earlier instead of summing the left and right portions repeatedly.

## 3. Prefix-sum pattern

```python
prefix = [0]

for number in nums:
    prefix.append(prefix[-1] + number)
```

A range sum from index `left` through `right` (inclusive) can be calculated using:

```python
range_sum = prefix[right + 1] - prefix[left]
```

## 4. Assigned coding practice

### LeetCode
- [Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)
- [Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/)

### HackerRank
- [Array Manipulation](https://www.hackerrank.com/challenges/crush/problem)
- [Sherlock and Array](https://www.hackerrank.com/challenges/sherlock-and-array/problem)

**Completion note:** The user confirmed Day 7 is completed. Individual acceptance results and personal attempt details were not present in the previous dashboard entry, so they are not reported here as verified.

## 5. Edge cases to remember

- A pivot may occur at the first or last index.
- An array may have no pivot index.
- Test arrays containing negative values.
- Test repeated values and arrays with a single element.
- For range sums, check that the prefix indexes use `right + 1` and `left` correctly.

## 6. Complexity review

- Building a prefix-sum array: **O(n) time** and **O(n) additional space**.
- A pivot-index scan after calculating the total: **O(n) time** and **O(1) auxiliary space**.
- Prefix-sum range query: **O(1) time** after preprocessing.
- Difference arrays can make repeated range updates more efficient, with a later prefix pass to reconstruct values.

## 7. Key learning

Prefix sums preserve information from earlier elements so later calculations can be answered without repeatedly traversing the same range. The technique is useful for pivot indexes, range-sum queries, and more advanced subarray problems.

**Day 7 Completed! ✅**
