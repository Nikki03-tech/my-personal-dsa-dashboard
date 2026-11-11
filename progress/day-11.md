# Day 11 — Advanced Hashing and Grouping

**Date studied:** November 11, 2026  
**Language:** Python  
**Status:** SOLUTIONS EXPLAINED — submission results not yet confirmed.

## 1. Assigned questions and submission status

### LeetCode
- [ ] **Q1 — [Group Anagrams](https://leetcode.com/problems/group-anagrams/)** — solution explained; submission unconfirmed
- [ ] **Q2 — [Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)** — solution explained; submission unconfirmed

### HackerRank
- [ ] **Q1 — [Sherlock and Anagrams](https://www.hackerrank.com/challenges/sherlock-and-anagrams/problem)** — solution explained; submission unconfirmed
- [ ] **Q2 — [Game of Thrones - I](https://www.hackerrank.com/challenges/game-of-thrones/problem)** — solution explained; submission unconfirmed

## 2. Concepts covered

- A dictionary can map one key to a list of grouped values.
- A sorted string can be used as an anagram signature.
- Character-frequency tuples are another possible anagram signature.
- Sliding windows can compare anagram frequencies efficiently.
- A dictionary can count how often a substring signature has appeared.
- A rearrangeable palindrome can have at most one odd character frequency.

## 3. Core patterns

### Group Anagrams

```python
groups = {}

for word in strs:
    key = ''.join(sorted(word))
    if key not in groups:
        groups[key] = []
    groups[key].append(word)

return list(groups.values())
```

### Find All Anagrams — window update

```python
window_count[new_char] = window_count.get(new_char, 0) + 1
window_count[old_char] -= 1

if window_count[old_char] == 0:
    del window_count[old_char]
```

Compare the window's frequency dictionary with the frequency dictionary of p. A match means the current window is an anagram.

### Sherlock and Anagrams

```python
from collections import defaultdict

def sherlockAndAnagrams(s):
    groups = defaultdict(int)
    count = 0

    for i in range(len(s)):
        for j in range(i, len(s)):
            key = ''.join(sorted(s[i:j + 1]))
            count += groups[key]
            groups[key] += 1

    return count
```

Add the number of earlier matching substrings before incrementing the key's frequency.

### Game of Thrones - I

```python
frequency = {}
for char in s:
    frequency[char] = frequency.get(char, 0) + 1

odd_count = sum(value % 2 != 0 for value in frequency.values())
return "YES" if odd_count <= 1 else "NO"
```

## 4. Complexity

- Group Anagrams with sorted keys: O(n × k log k), where n is the number of words and k is the maximum word length.
- Find All Anagrams: O(n) time for a fixed 26-letter alphabet, O(1) frequency space.
- Sherlock and Anagrams with sorted substrings: O(n³ log n) upper bound for this straightforward method.
- Game of Thrones - I: O(n) time and O(1) space for a fixed lowercase alphabet.

## 5. Common mistakes

- Using the original word as the key instead of a normalized key.
- Forgetting to join sorted letters into a string.
- Comparing only lengths instead of character frequencies.
- Keeping zero-count keys when comparing window dictionaries directly.
- Incrementing the Sherlock key before counting earlier matches.
- Allowing more than one odd frequency for a palindrome.

**Learning status:** All four solutions have been provided and explained. Do not mark a question Accepted until its platform submission confirms it.
