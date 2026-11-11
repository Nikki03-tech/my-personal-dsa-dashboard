# Day 8 — Strings and Character Frequencies

**Date:** November 10–11, 2026 | **Language:** Python

## 1. Character frequency
Frequency means how many times a character appears.

For `"banana"`: b = 1, a = 3, n = 2.

```python
frequency = {}
for char in word:
    frequency[char] = frequency.get(char, 0) + 1
```

`get(char, 0)` returns the existing count, or zero if the character is new. Then we add one.

## 2. Anagrams
Two strings are anagrams when they contain exactly the same characters with the same frequencies, in any order. For example, `listen` and `silent`.

Simple check: `sorted(s) == sorted(t)`. A frequency dictionary is another approach.

## 3. First Unique Character
A unique character appears once. Use `enumerate` to get both its index and value:

```python
for index, char in enumerate(s):
    if frequency[char] == 1:
        return index
return -1
```

## 4. Making Anagrams
To make two strings anagrams by deleting characters, add the absolute differences between their character counts:

```python
deletions = 0
for char in set(a + b):
    deletions += abs(count_a.get(char, 0) - count_b.get(char, 0))
```

`abs(x)` returns the non-negative value of x.

## 5. HackerRank Anagram
Split the string into two equal halves. If the length is odd, return `-1`. Otherwise compare the character counts in both halves and count the changes needed to match them.

## 6. Assigned questions
- [Valid Anagram — LeetCode](https://leetcode.com/problems/valid-anagram/)
- [First Unique Character — LeetCode](https://leetcode.com/problems/first-unique-character-in-a-string/)
- [Making Anagrams — HackerRank](https://www.hackerrank.com/challenges/making-anagrams/problem)
- [Anagram — HackerRank](https://www.hackerrank.com/challenges/anagram/problem)

## 7. Complexity
- Frequency counting: O(n) time and O(k) extra space, where k is distinct characters.
- Comparing frequency maps: O(k).
- Sorting-based anagram check: O(n log n).

## 8. Common mistakes
- Confusing a character with its index.
- Forgetting to start a missing count at zero.
- Comparing only string lengths; anagrams need matching frequencies.
- Forgetting the odd-length case in HackerRank Anagram.
- Returning the character when the problem asks for its index.

## 9. Interview revision
**What does a frequency dictionary store?** Each character and its count.  
**What does enumerate return?** An index and the corresponding item.  
**What makes two strings anagrams?** Identical character frequencies.

**Key takeaway:** When a string question asks about repeated, unique, missing or matching characters, think about frequency counting.
