# Day 10 — Sliding Window

**Date studied:** November 11, 2026  
**Language:** Python  
**Status:** COMPLETED — all four LeetCode and HackerRank solutions confirmed Accepted by user.

## 1. Assigned questions and submission status

### LeetCode
- [x] **Q1 — [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)** — Accepted
- [x] **Q2 — [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)** — Accepted

### HackerRank
- [x] **Q1 — [Subarray Division](https://www.hackerrank.com/challenges/the-birthday-bar/problem)** — Accepted
- [x] **Q2 — [Max Min](https://www.hackerrank.com/challenges/angry-children/problem)** — Accepted

## 2. Concepts covered

- A sliding window is a continuous range of an array or string.
- Fixed-size windows always contain exactly k elements.
- Variable-size windows grow or shrink based on a condition.
- Reuse the previous window's information instead of recalculating it.
- Window length = `right - left + 1`.

## 3. Core patterns

### Fixed-size sum window

```python
window_sum = sum(nums[:k])
max_sum = window_sum

for right in range(k, len(nums)):
    window_sum += nums[right]
    window_sum -= nums[right - k]
    max_sum = max(max_sum, window_sum)
```

Add the entering value and subtract the value that leaves.

### Variable-size unique-character window

```python
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
```

Use `while` because several characters may need to be removed before the window becomes valid again.

### Max Min after sorting

```python
def maxMin(k, arr):
    arr.sort()
    answer = float('inf')

    for i in range(len(arr) - k + 1):
        answer = min(answer, arr[i + k - 1] - arr[i])

    return answer
```

## 4. Key examples

For `nums = [1, 12, -5, -6, 50, 3]`, k = 4, the best window is `[12, -5, -6, 50]`; its average is 12.75.

For `s = "abca"`, the longest substring without repeating characters is `"abc"` or `"bca"`, length 3.

## 5. Complexity

- Fixed-size window sum: O(n) time, O(1) extra space.
- Variable-size unique-character window: O(n) average time; O(k) space for distinct characters.
- Max Min: O(n log n) sorting plus O(n) scan.

## 6. Common mistakes

- Recalculating the full sum for every window.
- Removing the wrong outgoing item; use `nums[right - k]`.
- Forgetting to check the first window.
- Using `if` instead of `while` to shrink a variable window.
- Forgetting +1 in `right - left + 1`.

**Completion note:** The user confirmed all four LeetCode and HackerRank solutions were Accepted.
