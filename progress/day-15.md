# Day 15 — Sorting & Partitioning

**Date:** November 15, 2026  
**Language:** Python  
**Status:** COMPLETED — solutions reviewed; submissions pending confirmation.

### Submission status

The four solutions have been reviewed. Individual platform submissions and acceptance results are still pending confirmation, so none of the problems below is marked Accepted.

## 1. Concepts Learned

- Sorting means arranging elements in ascending or descending order.
- Partitioning divides an array into sections based on a selected condition.
- The Three-Pointer Technique uses three pointers to arrange elements efficiently.
- The Two-Pointer Technique compares elements from different positions in an array.
- The Dutch National Flag Algorithm sorts an array containing only 0, 1, and 2 using three pointers.
- Merging Sorted Arrays combines two sorted arrays into one sorted array.
- Quicksort Partitioning separates elements around a pivot.
- Counting Sort uses frequency counting instead of comparing elements.
- Dictionaries and frequency arrays help count occurrences efficiently.

## 2. Important Logic

### Sort Colors — LeetCode

```python
class Solution:
    def sortColors(self, nums):
        low = 0
        mid = 0
        high = len(nums) - 1

        while mid <= high:
            if nums[mid] == 0:
                nums[low], nums[mid] = nums[mid], nums[low]
                low += 1
                mid += 1
            elif nums[mid] == 1:
                mid += 1
            else:
                nums[mid], nums[high] = nums[high], nums[mid]
                high -= 1
```

- `low` finds the correct position for 0.
- `mid` checks the current element.
- `high` finds the correct position for 2.
- If the element is 0, move it left.
- If it is 1, move forward.
- If it is 2, move it right. After swapping with `high`, check the new value at `mid` before advancing it.

### Merge Sorted Array — LeetCode

```python
class Solution:
    def merge(self, nums1, m, nums2, n):
        i = m - 1
        j = n - 1
        k = m + n - 1

        while j >= 0:
            if i >= 0 and nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1

            k -= 1
```

- `i` points to the last actual element of `nums1`.
- `j` points to the last element of `nums2`.
- `k` points to the last available position.
- Compare elements from the end and place the larger one first.

### Quicksort 1 — Partition — HackerRank

```python
def quickSort(arr):
    pivot = arr[0]
    left = []
    right = []

    for num in arr[1:]:
        if num < pivot:
            left.append(num)
        else:
            right.append(num)

    return left + [pivot] + right
```

- The first element is the pivot.
- Smaller elements go into the left list.
- Greater than or equal elements go into the right list.
- Combine left, pivot, and right. This performs one partition; it does not recursively sort the full array.

### Counting Sort 1 — HackerRank

```python
def countingSort(arr):
    result = [0] * 100

    for num in arr:
        result[num] += 1

    return result
```

- Create a list of 100 zeros.
- Count each number using its value as the index.
- Return the frequency list.

## 3. Mistakes to Avoid

- Do not use Python's built-in sorting function for Sort Colors.
- Do not increase `mid` after swapping a 2 with the element at `high`; the new element must still be checked.
- In Merge Sorted Array, begin from the end to avoid overwriting original values.
- In Merge Sorted Array, continue until all elements of `nums2` have been placed.
- In Quicksort Partition, do not sort the entire array; only partition around the pivot.
- In Counting Sort 1, remember that the output must contain exactly 100 frequency positions.
- Do not confuse counting frequencies with returning a sorted array.

## 4. Coding Problems

| Platform | Problem | Result |
|---|---|---|
| LeetCode | [Sort Colors](https://leetcode.com/problems/sort-colors/) | Pending submission confirmation |
| LeetCode | [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) | Pending submission confirmation |
| HackerRank | [Quicksort 1: Partition](https://www.hackerrank.com/challenges/quicksort1/problem) | Pending submission confirmation |
| HackerRank | [Counting Sort 1](https://www.hackerrank.com/challenges/countingsort1/problem) | Pending submission confirmation |

## 5. Time & Space Complexity

| Problem | Time | Auxiliary Space |
|---|---|---|
| Sort Colors | O(n) | O(1) |
| Merge Sorted Array | O(m + n) | O(1) |
| Quicksort 1 — Partition | O(n) | O(n) |
| Counting Sort 1 | O(n + 100) | O(100) |

### Complexity Notes

- `n` = number of elements.
- `m` = number of actual elements in `nums1`.
- In Merge Sorted Array, `n` is the number of elements in `nums2`.
- `low`, `mid`, and `high` are the three pointers in Sort Colors.
- `pivot` is the selected element used to partition an array.
- `append()` adds an element to a list.
- `result[num] += 1` increases the frequency of a number.
- Counting Sort 1 uses a fixed-size array of 100 counters.
- O(1) auxiliary space means constant extra working memory.

## 6. Mock Interview Questions & Answers

1. **What is Sorting?**  
   Sorting is arranging elements in a specific order, such as ascending or descending order.

2. **What is Partitioning?**  
   Partitioning divides an array into sections based on a selected condition or pivot.

3. **What is the Dutch National Flag Algorithm?**  
   It is a three-pointer technique used to sort an array containing 0, 1, and 2 in one traversal.

4. **Why do we use three pointers in Sort Colors?**  
   To keep track of the positions for 0, 1, and 2 while arranging the array.

5. **Why do we merge sorted arrays from the end?**  
   To avoid overwriting the original elements in `nums1`.

6. **What is a Pivot in Quicksort?**  
   A selected element used to divide the array into smaller and greater sections.

7. **What is Counting Sort?**  
   A sorting technique that uses the frequency of each value instead of comparing elements.

8. **What is the difference between Sorting and Counting Sort?**  
   Comparison sorting arranges elements by comparing them, whereas Counting Sort counts occurrences within a known value range.

## 7. Key Learning

Learned how to arrange elements using three pointers, merge two sorted arrays from the end, partition an array around a pivot, and count element frequencies using a fixed-size list. Improved understanding of sorting techniques, pointer movement, array manipulation, and time and space complexity.

**Day 15 — Solutions Reviewed! ✅**
