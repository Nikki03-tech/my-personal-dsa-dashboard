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
