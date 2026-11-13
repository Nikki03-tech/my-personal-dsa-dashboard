# Day 13 — Binary Search Fundamentals

**Date:** November 13, 2026  
**Language:** Python  
**Status:** COMPLETED ✅

## 1. Concepts Learned

- Binary Search is an efficient searching technique used on sorted arrays.
- It repeatedly divides the search range in half.
- `low` represents the starting index.
- `high` represents the ending index.
- `mid` represents the middle index.
- `mid = (low + high) // 2` calculates the middle index.
- If the middle element is smaller than the target, search the right half.
- If the middle element is greater than the target, search the left half.
- Binary Search takes O(log n) time.
- Binary Search can also find an insertion position.
- Binary Search on Answer is used to find the minimum or maximum feasible answer, such as minimum production time.

## 2. Important Logic

### Binary Search — LeetCode

```python
low = 0
high = len(nums) - 1

while low <= high:
    mid = (low + high) // 2

    if nums[mid] == target:
        return mid
    elif nums[mid] < target:
        low = mid + 1
    else:
        high = mid - 1

return -1
```

### Search Insert Position — LeetCode

```python
low = 0
high = len(nums) - 1

while low <= high:
    mid = (low + high) // 2

    if nums[mid] == target:
        return mid
    elif nums[mid] < target:
        low = mid + 1
    else:
        high = mid - 1

return low
```

### Intro to Tutorial Challenges — HackerRank

```python
def introTutorial(V, arr):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2

        if arr[mid] == V:
            return mid
        elif arr[mid] < V:
            low = mid + 1
        else:
            high = mid - 1

    return -1
```

### Minimum Time Required — HackerRank

```python
def minTime(machines, goal):
    low = 1
    high = min(machines) * goal

    while low < high:
        mid = (low + high) // 2
        total = 0

        for machine in machines:
            total += mid // machine

            if total >= goal:
                break

        if total >= goal:
            high = mid
        else:
            low = mid + 1

    return low
```

## 3. Mistakes Corrected

- Learned that Binary Search requires a sorted array.
- Corrected the middle-index calculation. For `low = 0` and `high = 5`, the correct `mid` is `2`.
- Understood why we use `mid + 1` when searching the right half.
- Understood why we use `mid - 1` when searching the left half.
- Learned the difference between returning `-1` and returning `low`.
- Understood that `return low` gives the correct insertion position when the target is not found.
- Learned that `while low <= high` is used for normal Binary Search, while `while low < high` is used in this minimum-time answer search.
- Understood that producing enough items means we should try a smaller time.

## 4. Coding Problems Completed

| Platform | Problem | Result |
|---|---|---|
| LeetCode | [Binary Search](https://leetcode.com/problems/binary-search/) | Accepted ✅ |
| LeetCode | [Search Insert Position](https://leetcode.com/problems/search-insert-position/) | Accepted ✅ |
| HackerRank | [Intro to Tutorial Challenges](https://www.hackerrank.com/challenges/tutorial-intro/problem) | Accepted ✅ |
| HackerRank | [Minimum Time Required](https://www.hackerrank.com/challenges/minimum-time-required/problem) | Accepted ✅ |

## 5. Time & Space Complexity

| Problem | Time | Auxiliary Space |
|---|---|---|
| Binary Search | O(log n) | O(1) |
| Search Insert Position | O(log n) | O(1) |
| Intro to Tutorial Challenges | O(log n) | O(1) |
| Minimum Time Required | O(n × log(min(machine) × goal)) | O(1) |

### Complexity Notes

- `n` = number of array elements or machines.
- `low` = starting search boundary.
- `high` = ending search boundary.
- `mid` = middle index or middle possible answer.
- `//` = integer division.
- O(log n) means the search space is reduced by half repeatedly.
- `mid // machine` calculates how many items one machine can produce in the given time.
- Binary Search on Answer searches for the minimum feasible result.

## 6. Mock Interview Questions & Answers

1. **What is Binary Search?**  
   Binary Search is an efficient searching technique that repeatedly divides a sorted search range in half.

2. **Why does Binary Search require a sorted array?**  
   Sorting helps us decide whether to search the left half or the right half.

3. **What is the time complexity of Binary Search?**  
   O(log n), because the search space is divided in half at every step.

4. **What is the purpose of `low`, `high`, and `mid`?**  
   `low` is the starting boundary, `high` is the ending boundary, and `mid` is the middle position.

5. **Why do we use `mid + 1` and `mid - 1`?**  
   To eliminate the already-checked middle element and continue searching in the correct half.

6. **What is the difference between Binary Search and Search Insert Position?**  
   Binary Search returns `-1` when the target is missing, whereas Search Insert Position returns the index where the target should be inserted.

7. **What is Binary Search on Answer?**  
   It searches for the minimum or maximum feasible answer instead of searching for an array element.

8. **How does Minimum Time Required work?**  
   It checks how many items all machines can produce in a given time and adjusts the search range until it finds the minimum sufficient time.

## 7. Key Learning

Learned how to implement Binary Search, find elements and insertion positions in sorted arrays, and apply Binary Search on Answer to solve minimum-time problems. Improved understanding of search boundaries, middle-index calculation, decision conditions, and time and space complexity.

**Day 13 Completed! ✅**
