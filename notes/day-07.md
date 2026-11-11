# Day 7 — Prefix Sums

**Date:** November 7, 2026  
**Language:** Python  
**Status:** Completed ✅

### 1. Concepts Learned

- Prefix sum means a running total of array elements.
- It helps answer range-sum questions without adding the same elements repeatedly.
- A prefix array stores the sum from the beginning up to each position.
- Starting the prefix array with zero makes range calculations easier.
- The sum from index left to right is prefix[right + 1] - prefix[left].
- A pivot index is where the sum on the left equals the sum on the right.
- Difference arrays help perform multiple range updates efficiently.

### 2. Important Logic

**Building a Prefix Sum**
~~~python
prefix = [0]

for number in nums:
    prefix.append(prefix[-1] + number)
~~~

**Range Sum**
~~~python
range_sum = prefix[right + 1] - prefix[left]
~~~

**Pivot Index**
~~~python
total = sum(nums)
left_sum = 0

for i in range(len(nums)):
    right_sum = total - left_sum - nums[i]
    if left_sum == right_sum:
        return i
    left_sum += nums[i]

return -1
~~~

**Difference Array Range Update**
~~~python
diff[left] += value
if right + 1 < len(diff):
    diff[right + 1] -= value
~~~
After all updates, calculate the running sum of diff to rebuild the final array.

### 3. Mistakes Corrected

- Learned why a prefix array often starts with zero.
- Understood why the right index becomes right + 1 in the prefix formula.
- Learned not to include the pivot element in either side's sum.
- Understood that left_sum must be updated after checking the current index.
- Learned that difference arrays avoid updating every element in a range separately.

### 4. Coding Problems Completed

| **Platform** | **Problem** | **Result** |
| --- | --- | --- |
| LeetCode | Find Pivot Index | Accepted ✅ |
| LeetCode | Range Sum Query - Immutable | Accepted ✅ |
| HackerRank | Array Manipulation | Accepted ✅ |
| HackerRank | Sherlock and Array | Accepted ✅ |

### 5. Time & Space Complexity

| **Problem / Technique** | **Time** | **Space** |
| --- | --- | --- |
| Building Prefix Sum | O(n) | O(n) |
| Range Sum Query after preprocessing | O(1) per query | O(n) for prefix array |
| Pivot Index | O(n) | O(1) auxiliary |
| Array Manipulation with Difference Array | O(n + m) | O(n) |

**Remember:**

- n = number of array elements.
- m = number of range update operations.
- Prefix sum stores previous totals.
- Difference array stores where range changes begin and end.

### 6. Mock Interview Questions & Answers

1. **What is a Prefix Sum?**  
   A running total of array elements stored so range sums can be calculated quickly.
2. **Why do we start the prefix array with zero?**  
   It makes the range-sum formula simpler and handles ranges beginning at index zero.
3. **How do we find a range sum?**  
   Use prefix[right + 1] - prefix[left].
4. **What is a Pivot Index?**  
   An index where the sum on the left equals the sum on the right, excluding the current element.
5. **Why is Pivot Index O(n)?**  
   We calculate the total once and traverse the array once.
6. **What is a Difference Array?**  
   A technique that records the start and end of range updates so we can apply them efficiently.
7. **When is Prefix Sum useful?**  
   When a problem asks for sums of continuous ranges or repeated cumulative totals.

### 7. Key Learning

Learned how to store running totals, calculate range sums quickly, find a pivot index, and use difference arrays for efficient range updates.

**Day 7 Completed! ✅**


---

## Previous complete version (preserved from GitHub history)

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
