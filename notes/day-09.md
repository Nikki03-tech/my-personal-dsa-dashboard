# Day 9 — Two Pointers

**Date:** November 11, 2026 | **Language:** Python

## 1. What are two pointers?
Two pointers are index variables that track two positions in an array or string. They can move toward each other or move forward through a sorted array.

```python
left = 0
right = len(arr) - 1
```

## 2. Valid Palindrome
Compare characters at both ends. Skip non-alphanumeric characters, compare lowercase characters, then move both pointers inward. If a pair differs, it is not a palindrome.

Useful methods: `isalnum()` checks for a letter or digit; `lower()` converts to lowercase.

## 3. Two Sum II — sorted array
Start at both ends:

```python
left, right = 0, len(numbers) - 1
while left < right:
    current_sum = numbers[left] + numbers[right]
    if current_sum == target:
        return [left + 1, right + 1]
    elif current_sum < target:
        left += 1
    else:
        right -= 1
```

- Sum too small: move left forward to get a larger value.
- Sum too large: move right backward to get a smaller value.
- Correct sum: return the indexes. This problem asks for 1-based indexes, so add one.

## 4. HackerRank Two Strings
Check whether two strings share a character. Sets keep unique characters; `set(s1) & set(s2)` finds their intersection.

## 5. HackerRank Pairs
Count pairs with difference exactly k. Sort first, then use two pointers:

```python
def pairs(k, arr):
    arr.sort()
    left, right = 0, 1
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
```

Difference too small → move right. Difference too large → move left. Equal → count and move both.

## 6. Assigned questions
- [Valid Palindrome — LeetCode](https://leetcode.com/problems/valid-palindrome/)
- [Two Sum II — LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
- [Two Strings — HackerRank](https://www.hackerrank.com/challenges/two-strings/problem)
- [Pairs — HackerRank](https://www.hackerrank.com/challenges/pairs/problem)

## 7. Complexity
- Palindrome scan: O(n) time, O(1) extra space.
- Two Sum II: O(n) time, O(1) extra space.
- Set intersection: O(n + m) average time and O(n + m) space.
- Pairs: O(n log n) including sorting, then O(n) pointer scan.

## 8. Common mistakes
- Moving the wrong pointer for a small or large sum.
- Forgetting Two Sum II uses 1-based indexes.
- Forgetting to sort before the Pairs algorithm.
- Failing to move a pointer, which can cause an infinite loop.

## 9. Interview revision
**When is two pointers useful?** For sorted data, comparing both ends, or finding pairs efficiently.  
**Why move left when the sum is too small?** A larger left value increases the sum.  
**Why sort for Pairs?** Sorting makes pointer movement predictable.

**Key takeaway:** Use the order in the data to avoid checking every possible pair with nested loops.
