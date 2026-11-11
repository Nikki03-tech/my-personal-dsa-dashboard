# Day 10 — Sliding Window

**Date:** November 11, 2026 | **Language:** Python

## 1. What is a sliding window?
A window is a continuous range of elements in a string or array. Instead of recalculating everything, update the current window as it moves: add what enters on the right and remove what leaves on the left.

## 2. Fixed-size window
A fixed-size window always contains k elements. For `[1, 2, 3, 4, 5]` with k = 3, the windows are [1,2,3], [2,3,4], [3,4,5].

```python
window_sum = sum(nums[:k])
for right in range(k, len(nums)):
    window_sum += nums[right]
    window_sum -= nums[right - k]
```

Add the new value and subtract the outgoing value.

## 3. Maximum Average Subarray I
Find the maximum average of any consecutive group of k values.

```python
window_sum = sum(nums[:k])
max_sum = window_sum

for right in range(k, len(nums)):
    window_sum += nums[right]
    window_sum -= nums[right - k]
    max_sum = max(max_sum, window_sum)

return max_sum / k
```

All windows have the same size, so the maximum sum also gives the maximum average. Example: `[1,12,-5,-6,50,3]`, k = 4 → best window [12,-5,-6,50], average 12.75.

## 4. Subarray Division — The Birthday Bar
Count groups of exactly m consecutive values whose sum is d.

```python
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
```

## 5. Max Min — sort and scan windows
Choose k values with the smallest possible largest-minus-smallest difference. Sort, then check each group of k consecutive values:

```python
def maxMin(k, arr):
    arr.sort()
    answer = float('inf')
    for i in range(len(arr) - k + 1):
        difference = arr[i + k - 1] - arr[i]
        answer = min(answer, difference)
    return answer
```

After sorting, an optimal group can be found among consecutive values. This is a fixed-size scan after sorting, not a running-sum window.

## 6. Variable-size window
For Longest Substring Without Repeating Characters, grow right and shrink left while the new character is already in the current window:

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

Window length is `right - left + 1`. Use `while` because more than one removal may be needed.

## 7. Assigned questions
- [Longest Substring Without Repeating Characters — LeetCode](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- [Maximum Average Subarray I — LeetCode](https://leetcode.com/problems/maximum-average-subarray-i/)
- [Subarray Division — HackerRank](https://www.hackerrank.com/challenges/the-birthday-bar/problem)
- [Max Min — HackerRank](https://www.hackerrank.com/challenges/angry-children/problem)

## 8. Complexity
- Fixed-size sum window: O(n) time, O(1) extra space.
- Variable unique-character window: O(n) average time; O(k) space for distinct characters in the window.
- Max Min: O(n log n) sorting + O(n) scan.

## 9. Common mistakes
- Recalculating the entire window sum each time.
- Removing the wrong outgoing value; use `nums[right - k]`.
- Forgetting to check the first window.
- Using `if` instead of `while` to remove repeated characters.
- Forgetting the +1 in window length.

## 10. Interview revision
**Fixed vs variable window?** Fixed always has k elements; variable grows or shrinks to satisfy a condition.  
**Why can it be O(n)?** Each pointer moves forward at most n times.  
**How do you calculate window length?** right - left + 1.

**Key takeaway:** For consecutive ranges, reuse the previous window's information rather than starting the calculation again.
