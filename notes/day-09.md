# Day 9 — Two Pointers

**Date:** November 9, 2026  
**Language:** Python  
**Status:** Completed ✅

### 1. Concepts Learned

- Two Pointers means using two index variables to process an array or string.
- Common pointer names are left and right.
- Pointers can start at opposite ends or at different positions and move through the data.
- Two Pointers can reduce the need for nested loops.
- In a sorted array, moving a pointer can make a sum larger or smaller in a predictable way.
- Sorting first can make pair-difference problems easier.
- isalnum() checks whether a character is a letter or number.
- lower() converts a character to lowercase.
- Set intersection finds common elements.

### 2. Important Logic

**Valid Palindrome**
~~~python
left = 0
right = len(s) - 1

while left < right:
    if not s[left].isalnum():
        left += 1
    elif not s[right].isalnum():
        right -= 1
    elif s[left].lower() != s[right].lower():
        return False
    else:
        left += 1
        right -= 1

return True
~~~

**Two Sum II — Sorted Array**
~~~python
left = 0
right = len(numbers) - 1

while left < right:
    current_sum = numbers[left] + numbers[right]

    if current_sum == target:
        return [left + 1, right + 1]
    elif current_sum < target:
        left += 1
    else:
        right -= 1
~~~

**Two Strings — Common Character**
~~~python
if set(s1) & set(s2):
    return "YES"

return "NO"
~~~

**Pairs — Difference Equals k**
~~~python
def pairs(k, arr):
    arr.sort()
    left = 0
    right = 1
    count = 0

    while right < len(arr):
        if left == right:
            right += 1
            continue

        difference = arr[right] - arr[left]

        if difference == k:
            count += 1
            left += 1
            right += 1
        elif difference < k:
            right += 1
        else:
            left += 1

    return count
~~~

### 3. Mistakes Corrected

- Learned to move the left pointer when a sorted-array sum is too small.
- Learned to move the right pointer when the sum is too large.
- Understood why Two Sum II asks for 1-based indexes, so we return index + 1.
- Learned to skip spaces and punctuation in Valid Palindrome.
- Understood that set intersection checks for common characters.
- Learned that the Pairs problem needs sorting before using the two-pointer approach.
- Understood that at least one pointer must move in every loop iteration to avoid an infinite loop.

### 4. Coding Problems Completed

| **Platform** | **Problem** | **Result** |
| --- | --- | --- |
| LeetCode | Valid Palindrome | Accepted ✅ |
| LeetCode | Two Sum II - Input Array Is Sorted | Accepted ✅ |
| HackerRank | Two Strings | Accepted ✅ |
| HackerRank | Pairs | Accepted ✅ |

### 5. Time & Space Complexity

| **Problem** | **Time** | **Space** |
| --- | --- | --- |
| Valid Palindrome | O(n) | O(1) |
| Two Sum II | O(n) | O(1) |
| Two Strings | O(n + m) average | O(n + m) |
| Pairs | O(n log n) including sorting | Depends on sorting implementation; O(1) auxiliary for pointer scan |

**Remember:**

- n and m = lengths of the input strings or arrays.
- Sorted order helps us decide which pointer to move.
- Pairs takes O(n log n) because sorting is required.
- Each pointer moves forward or inward; do not leave both unchanged.

### 6. Mock Interview Questions & Answers

1. **What is the Two Pointers technique?**  
   It uses two indexes to process a sequence efficiently.
2. **Why is Two Sum II O(n)?**  
   Both pointers move through the sorted array at most once.
3. **What do we do if the sum is smaller than the target?**  
   Move the left pointer forward to try a larger value.
4. **What do we do if the sum is greater than the target?**  
   Move the right pointer backward to try a smaller value.
5. **Why do we sort the array in Pairs?**  
   Sorting makes the difference between the two pointer values predictable.
6. **What does set intersection do?**  
   It returns the elements that are present in both sets.
7. **Why does Two Sum II return index + 1?**  
   The problem requires 1-based indexes instead of Python's 0-based indexes.

### 7. Key Learning

Learned how to compare values from both ends, solve pair-sum and pair-difference problems, check common characters, and process palindromes efficiently.

**Day 9 Completed! ✅**
