# Day 11 — Advanced Hashing and Grouping

**Date:** November 11, 2026 | **Language:** Python

## 1. Dictionary of lists
A dictionary can store a list as each value. This groups related items under one key.

```python
groups = {}
key = "aet"
if key not in groups:
    groups[key] = []
groups[key].append("eat")
groups[key].append("tea")
```

Now `groups["aet"]` is `["eat", "tea"]`.

## 2. Group Anagrams
Anagrams have the same letters. Sorting each word creates a common key:

- eat → aet
- tea → aet
- ate → aet

```python
groups = {}
for word in strs:
    key = ''.join(sorted(word))
    if key not in groups:
        groups[key] = []
    groups[key].append(word)
return list(groups.values())
```

An alternative is a tuple containing 26 letter counts for lowercase English letters.

## 3. Find All Anagrams in a String
Use a fixed-size window of length `len(p)`:
1. Count the characters in p.
2. Count the first window in s.
3. Compare the two dictionaries.
4. Slide one position: add the new character and remove the old one.
5. If counts match, record the window's start index.

```python
window_count[new_char] = window_count.get(new_char, 0) + 1
window_count[old_char] -= 1
if window_count[old_char] == 0:
    del window_count[old_char]
```

Deleting zero-count keys makes dictionary equality straightforward.

## 4. Sherlock and Anagrams
Count pairs of substrings that are anagrams. Sort each substring to make a common key. The dictionary stores how many earlier substrings have that key.

```python
from collections import defaultdict

def sherlockAndAnagrams(s):
    groups = defaultdict(int)
    count = 0
    for i in range(len(s)):
        for j in range(i, len(s)):
            substring = s[i:j + 1]
            key = ''.join(sorted(substring))
            count += groups[key]
            groups[key] += 1
    return count
```

Important: add `groups[key]` before incrementing it. It counts the earlier matching substrings, each of which forms a new pair with the current substring.

## 5. Game of Thrones - I
Can the characters be rearranged to form a palindrome? Every character must have an even frequency, except at most one character may have an odd frequency.

```python
frequency = {}
for char in s:
    frequency[char] = frequency.get(char, 0) + 1

odd_count = 0
for value in frequency.values():
    if value % 2 != 0:
        odd_count += 1

return "YES" if odd_count <= 1 else "NO"
```

Example: civic → c:2, i:2, v:1. One odd count, so YES.

## 6. Assigned questions
- [Group Anagrams — LeetCode](https://leetcode.com/problems/group-anagrams/)
- [Find All Anagrams in a String — LeetCode](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
- [Sherlock and Anagrams — HackerRank](https://www.hackerrank.com/challenges/sherlock-and-anagrams/problem)
- [Game of Thrones - I — HackerRank](https://www.hackerrank.com/challenges/game-of-thrones/problem)

## 7. Complexity
- Group Anagrams with sorted keys: O(n × k log k) time, where n is word count and k is max word length.
- Find All Anagrams: O(n) time for a fixed 26-letter alphabet; O(1) frequency space.
- Sherlock and Anagrams using sorted substrings: O(n³ log n) upper bound; O(n³) stored key characters in this straightforward approach.
- Game of Thrones - I: O(n) time and O(1) space for a fixed lowercase alphabet.

## 8. Common mistakes
- Using the original word as the key rather than a normalized key.
- Forgetting to join sorted letters into a string.
- Comparing lengths instead of character frequencies.
- Leaving zero-count keys in a window dictionary when using direct dictionary equality.
- Incrementing the Sherlock key count before adding the number of earlier matches.
- Assuming a palindrome can have two or more odd frequencies.

## 9. Interview revision
**Why sorted keys for Group Anagrams?** Anagrams produce the same sorted string.  
**Why add groups[key] in Sherlock?** It counts all previous matching substrings that pair with the current one.  
**How many odd frequencies can a rearrangeable palindrome have?** Zero or one.

**Key takeaway:** Hashing converts repeated comparisons into lookups. Build a consistent signature, then group or count items that share it.
