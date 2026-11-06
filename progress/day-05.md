# Day 5 — Hash Maps (Python Dictionaries)

**Date:** November 5, 2026  
**Language:** Python  
**Status:** COMPLETED ✅


## Updated dashboard assignments — four questions per day

> The original two-problem work for this day is preserved below. Under the revised dashboard, Q1 on each platform was completed in the earlier session; the newly added Q2 tasks are still pending. The historical completion status below does not mean the new Q2 tasks have been attempted.

### LeetCode

- [x] **Q1 — [Two Sum](https://leetcode.com/problems/two-sum/)** — completed in the original plan
- [ ] **Q2 — [Majority Element](https://leetcode.com/problems/majority-element/)** — newly added in the four-question plan; not yet attempted

### HackerRank

- [x] **Q1 — [Ransom Note](https://www.hackerrank.com/challenges/ctci-ransom-note/problem)** — completed in the original plan
- [ ] **Q2 — [Frequency Queries](https://www.hackerrank.com/challenges/frequency-queries/problem)** — newly added in the four-question plan; not yet attempted

## 1. Concepts Learned

- Hash Maps using Python dictionaries (`dict`).
- Key-value pairs.
- Adding and updating dictionary values.
- Checking keys using `in`.
- Frequency counting using dictionaries.
- Complement technique in Two Sum.
- Using dictionaries for faster lookups.
- Decreasing word frequency when using a word.
- Difference between sequential loops and nested loops.

## 2. Important Logic

### Two Sum

```python
class Solution:
    def twoSum(self, nums, target):
        seen = {}

        for i, number in enumerate(nums):
            complement = target - number

            if complement in seen:
                return [seen[complement], i]

            seen[number] = i
```

### Ransom Note

```python
def checkMagazine(magazine, note):
    word_count = {}

    for word in magazine:
        if word in word_count:
            word_count[word] += 1
        else:
            word_count[word] = 1

    for word in note:
        if word not in word_count or word_count[word] == 0:
            print("No")
            return

        word_count[word] -= 1

    print("Yes")
```

## 3. Mistakes Corrected

- Learned that sets and dictionaries are mutable.
- Understood that dictionaries store key-value pairs.
- Learned that Two Sum stores the number as key and index as value.
- Understood why we use `target - number` to calculate the complement.
- Learned why Ransom Note decreases word frequency after using a word.
- Understood why `print("Yes")` belongs outside the checking loop.

## 4. Coding Problems Completed

| Platform | Problem | Result |
|---|---|---|
| LeetCode | Two Sum | Accepted ✅ |
| HackerRank | Ransom Note | Accepted ✅ |

## 5. Time & Space Complexity

| Problem | Time | Space |
|---|---|---|
| Two Sum | O(n) average | O(n) |
| Ransom Note | O(m + n) average | O(m) |

### Remember

- Dictionary lookup: O(1) average.
- Two Sum uses a Hash Map to avoid nested loops.
- Ransom Note uses frequency counting.
- Sequential loops: O(m + n).
- Nested loops: O(m × n).
- `m` = magazine length; `n` = note length.

## 6. Mock Interview Questions & Answers

1. **What is a Hash Map?** A data structure that stores information as key-value pairs.
2. **Difference between Hash Map and Set?** Hash Maps store key-value pairs; Sets store unique elements.
3. **What does `seen[2]` return?** It returns the value associated with key 2.
4. **Why calculate the complement in Two Sum?** To find the number needed to reach the target.
5. **Why decrease word frequency in Ransom Note?** To track how many copies of a word remain available.
6. **What is Ransom Note complexity?** O(m + n) average time because we process magazine and note separately.
7. **Difference between O(n) and O(n²)?** O(n) represents linear growth; O(n²) represents quadratic growth, commonly from nested loops.

## 7. Key Learning

Learned how to use Hash Maps for efficient searching, solve Two Sum using the complement technique, count word frequencies, and optimize solutions using dictionaries.

**Day 5 Completed! ✅**
