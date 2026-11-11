# Day 10 — Sliding Window

**Date:** November 10, 2026  
**Language:** Python  
**Status:** Completed ✅

### 1. Concepts Learned

- A window is a continuous part of an array or string.
- Sliding Window reuses information from the previous window instead of recalculating everything.
- A fixed-size window always contains exactly k elements.
- A variable-size window can grow or shrink depending on a condition.
- The right pointer adds new elements to the window.
- The left pointer removes elements from the beginning of the window.
- Window length is calculated using right - left + 1.
- A set can track characters currently inside a window.
- Sorting followed by checking consecutive groups is useful for the Max Min problem.

### 2. Important Logic

**Fixed-Size Window — Maximum Sum**
~~~python
window_sum = sum(nums[:k])
max_sum = window_sum

for right in range(k, len(nums)):
    window_sum += nums[right]
    window_sum -= nums[right - k]
    max_sum = max(max_sum, window_sum)

return max_sum
~~~

**Longest Substring Without Repeating Characters**
~~~python
left = 0
seen = set()
max_length = 0

for right in range(len(s)):
    while s[right] in seen:
        seen.remove(s[left])
        left += 1

    seen.add(s[right])
    max_length = max(max_length, right - left + 1)

return max_length
~~~

**Subarray Division — The Birthday Bar**
~~~python
def birthday(s, d, m):
    if m > len(s):
        return 0

    window_sum = sum(s[:m])
    count = 1 if window_sum == d else 0

    for right in range(m, len(s)):
        window_sum += s[right]
        window_sum -= s[right - m]

        if window_sum == d:
            count += 1

    return count
~~~

**Max Min**
~~~python
def maxMin(k, arr):
    arr.sort()
    answer = float('inf')

    for i in range(len(arr) - k + 1):
        difference = arr[i + k - 1] - arr[i]
        answer = min(answer, difference)

    return answer
~~~

### 3. Mistakes Corrected

- Learned to add the new element and remove the element leaving the window.
- Understood why the outgoing element is at index right - k.
- Learned to check the first window before sliding.
- Understood why variable-size windows may need a while loop instead of an if.
- Learned that window length is right - left + 1, not just right - left.
- Understood that Max Min uses sorting and consecutive groups of size k.

### 4. Coding Problems Completed

| **Platform** | **Problem** | **Result** |
| --- | --- | --- |
| LeetCode | Longest Substring Without Repeating Characters | Accepted ✅ |
| LeetCode | Maximum Average Subarray I | Accepted ✅ |
| HackerRank | Subarray Division | Accepted ✅ |
| HackerRank | Max Min | Accepted ✅ |

### 5. Time & Space Complexity

| **Problem** | **Time** | **Space** |
| --- | --- | --- |
| Longest Substring Without Repeating Characters | O(n) average | O(k) |
| Maximum Average Subarray I | O(n) | O(1) |
| Subarray Division | O(n) | O(1) |
| Max Min | O(n log n) including sorting | Depends on sorting implementation |

**Remember:**

- n = number of elements or characters.
- k = window size or number of distinct characters, depending on the problem.
- Fixed-size window: add one element and remove one element.
- Variable-size window: expand and shrink until the condition is satisfied.

### 6. Mock Interview Questions & Answers

1. **What is Sliding Window?**  
   It is a technique for processing continuous parts of an array or string efficiently.
2. **What is a Fixed-Size Window?**  
   A window that always contains exactly k elements.
3. **What is a Variable-Size Window?**  
   A window that grows or shrinks depending on a condition.
4. **Why is Maximum Average Subarray O(n)?**  
   We calculate the first window and then update the sum in constant time for each next position.
5. **Why do we use a while loop for Longest Substring?**  
   We may need to remove more than one character before the repeated character is no longer in the window.
6. **How do we calculate window length?**  
   Use right - left + 1.
7. **Why do we sort in Max Min?**  
   After sorting, checking consecutive groups lets us find the smallest possible difference between the largest and smallest values.

### 7. Key Learning

Learned fixed-size and variable-size sliding windows, how to update a window efficiently, and how to track the longest valid substring without repeating characters.

**Day 10 Completed! ✅**
