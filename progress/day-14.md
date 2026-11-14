# Day 14 — Binary Search Variations & Search on Answer

**Date:** November 14, 2026  
**Language:** Python  
**Status:** COMPLETED ✅

## 1. Concepts Learned

- A Rotated Sorted Array is an originally sorted array that has been rotated around a pivot.
- In a rotated sorted array, at least one half is always sorted.
- Binary Search can identify the sorted half and decide where to search next.
- We can find the minimum element in a rotated sorted array using Binary Search.
- `high = mid` keeps the middle element as a possible minimum.
- Climbing the Leaderboard uses Binary Search to find a player's rank.
- Removing duplicate leaderboard scores helps assign the correct dense ranking.
- Dictionaries store values as key-value pairs.
- Frequency Counting helps identify numbers that occur more times in one array than another.
- `sorted()` arranges the final results in ascending order.

## 2. Important Logic

### Search in Rotated Sorted Array — LeetCode

```python
class Solution:
    def search(self, nums, target):
        low = 0
        high = len(nums) - 1

        while low <= high:
            mid = (low + high) // 2

            if nums[mid] == target:
                return mid

            if nums[low] <= nums[mid]:
                if nums[low] <= target < nums[mid]:
                    high = mid - 1
                else:
                    low = mid + 1
            else:
                if nums[mid] < target <= nums[high]:
                    low = mid + 1
                else:
                    high = mid - 1

        return -1
```

### Find Minimum in Rotated Sorted Array — LeetCode

```python
class Solution:
    def findMin(self, nums):
        low = 0
        high = len(nums) - 1

        while low < high:
            mid = (low + high) // 2

            if nums[mid] > nums[high]:
                low = mid + 1
            else:
                high = mid

        return nums[low]
```

### Climbing the Leaderboard — HackerRank

```python
def climbingLeaderboard(ranked, player):
    unique = []

    for score in ranked:
        if not unique or score != unique[-1]:
            unique.append(score)

    result = []

    for score in player:
        low = 0
        high = len(unique)

        while low < high:
            mid = (low + high) // 2

            if unique[mid] > score:
                low = mid + 1
            else:
                high = mid

        result.append(low + 1)

    return result
```

### Missing Numbers — HackerRank

```python
def missingNumbers(arr, brr):
    frequency = {}

    for num in brr:
        frequency[num] = frequency.get(num, 0) + 1

    for num in arr:
        frequency[num] -= 1

    result = []

    for num, count in frequency.items():
        if count > 0:
            result.append(num)

    return sorted(result)
```

## 3. Mistakes Corrected

- Learned that a rotated sorted array is not completely sorted, but at least one half is always sorted.
- Understood how to identify the sorted half before deciding which direction to search.
- Learned why `high = mid` is used when finding the minimum because the middle element might itself be the minimum.
- Understood the difference between searching for a target and searching for the minimum value.
- Learned that duplicate leaderboard scores must be removed to calculate dense ranking correctly.
- Understood why the leaderboard rank is `low + 1`.
- Learned that Missing Numbers is about frequency differences, not just numbers that are completely absent.
- Understood how `dict.get(num, 0) + 1` counts occurrences.
- Learned why `sorted(result)` is used to return the missing numbers in ascending order.

## 4. Coding Problems Completed

| Platform | Problem | Result |
|---|---|---|
| LeetCode | [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) | Accepted ✅ |
| LeetCode | [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) | Accepted ✅ |
| HackerRank | [Climbing the Leaderboard](https://www.hackerrank.com/challenges/climbing-the-leaderboard/problem) | Accepted ✅ |
| HackerRank | [Missing Numbers](https://www.hackerrank.com/challenges/missing-numbers/problem) | Accepted ✅ |

## 5. Time & Space Complexity

| Problem | Time | Space |
|---|---|---|
| Search in Rotated Sorted Array | O(log n) | O(1) |
| Find Minimum in Rotated Sorted Array | O(log n) | O(1) |
| Climbing the Leaderboard | O(n + m log n) | O(n + m) including output |
| Missing Numbers | O(n + m + k log k) | O(k) |

### Complexity Notes

- `n` = number of elements in the first array or leaderboard.
- `m` = number of player scores or elements in the second array.
- `k` = number of distinct numbers in the frequency dictionary.
- Binary Search takes O(log n) time.
- `unique[-1]` accesses the last element of a list.
- `dict.get(key, 0)` returns the value if the key exists; otherwise, it returns 0.
- `count -= 1` decreases the frequency.
- `sorted(result)` sorts the result in ascending order.
- Auxiliary space and output space are different.

## 6. Mock Interview Questions & Answers

1. **What is a Rotated Sorted Array?**  
   An originally sorted array that has been shifted around a pivot position.

2. **How does Binary Search work in a Rotated Sorted Array?**  
   At least one half is sorted. We identify that half and check whether the target belongs to it.

3. **How do we find the minimum element in a Rotated Sorted Array?**  
   Compare the middle element with the rightmost element and adjust the search boundaries until the minimum is found.

4. **Why do we use `high = mid` while finding the minimum?**  
   Because the middle element could be the minimum, so we must not discard it.

5. **What is Dense Ranking?**  
   A ranking system in which equal scores share the same rank and the next distinct score gets the next consecutive rank.

6. **Why do we remove duplicate scores in Climbing the Leaderboard?**  
   To ensure equal scores share one rank and the ranking has no gaps.

7. **Why do we use Binary Search in Climbing the Leaderboard?**  
   To efficiently find the position where each player's score belongs in the sorted leaderboard.

8. **What is Frequency Counting?**  
   A technique used to count how many times each element appears in a collection.

9. **Why do we use a dictionary in Missing Numbers?**  
   To store and compare the frequencies of numbers in both arrays efficiently.

10. **What is the time complexity of Binary Search?**  
    O(log n), because the search range is divided into half at every step.

## 7. Key Learning

Learned how to apply Binary Search to rotated sorted arrays, find minimum elements efficiently, calculate leaderboard rankings using sorted unique scores, and identify missing occurrences using dictionary-based frequency counting. Improved understanding of search boundaries, dense ranking, dictionaries, sorting, and time and space complexity.

**Day 14 Completed! ✅**
