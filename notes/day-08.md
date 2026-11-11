# Day 8 — Strings and Character Frequencies

**Date:** November 8, 2026  
**Language:** Python  
**Status:** Completed ✅

### 1. Concepts Learned

- A string is a sequence of characters.
- A dictionary stores key-value pairs.
- Character frequency means counting how many times each character appears.
- dict.get(key, 0) returns the current count or zero if the key does not exist.
- Two strings are anagrams when they contain the same characters with the same frequencies.
- enumerate() gives both the index and the character while looping.
- set() stores unique characters.
- abs() returns the positive difference between two numbers.

### 2. Important Logic

**Character Frequency**
~~~python
frequency = {}

for char in word:
    frequency[char] = frequency.get(char, 0) + 1
~~~

**Valid Anagram**
~~~python
return sorted(s) == sorted(t)
~~~

**First Unique Character**
~~~python
for index, char in enumerate(s):
    if frequency[char] == 1:
        return index

return -1
~~~

**Making Anagrams**
~~~python
deletions = 0

for char in set(a + b):
    deletions += abs(
        count_a.get(char, 0) - count_b.get(char, 0)
    )

return deletions
~~~

**HackerRank Anagram**
- If the string length is odd, return -1.
- Otherwise count characters in both halves.
- Count how many characters must be changed so both halves have matching frequencies.

### 3. Mistakes Corrected

- Learned the difference between a character and its index.
- Understood why enumerate() is useful when an index is required.
- Learned that matching string lengths does not prove two strings are anagrams.
- Understood why every character's frequency must match.
- Learned to use dict.get(char, 0) for characters that may not exist in a dictionary.
- Understood why an odd-length string cannot be split into two equal halves.

### 4. Coding Problems Completed

| **Platform** | **Problem** | **Result** |
| --- | --- | --- |
| LeetCode | Valid Anagram | Accepted ✅ |
| LeetCode | First Unique Character in a String | Accepted ✅ |
| HackerRank | Making Anagrams | Accepted ✅ |
| HackerRank | Anagram | Accepted ✅ |

### 5. Time & Space Complexity

| **Problem / Technique** | **Time** | **Space** |
| --- | --- | --- |
| Frequency Counting | O(n) | O(k) |
| Valid Anagram using sorting | O(n log n) | O(n) depending on sorting |
| First Unique Character | O(n) | O(k) |
| Making Anagrams | O(n + m) | O(k) |

**Remember:**

- n and m = lengths of the input strings.
- k = number of distinct characters.
- Dictionary lookup is O(1) average time.
- Sorting a string takes O(n log n) time.

### 6. Mock Interview Questions & Answers

1. **What is Character Frequency?**  
   It is the number of times a character appears in a string.
2. **What is an Anagram?**  
   Two strings that contain the same characters with the same frequencies, possibly in a different order.
3. **Why use a Dictionary for frequency counting?**  
   It stores each character and its count, making updates and lookups efficient.
4. **What does dict.get(char, 0) do?**  
   It returns the character's current count, or zero if the character is not present.
5. **What does enumerate() return?**  
   It gives the index and the corresponding item during a loop.
6. **Why do we use abs() in Making Anagrams?**  
   To calculate the positive difference between the two character counts.
7. **What should we return for an odd-length string in HackerRank Anagram?**  
   Return -1 because it cannot be divided into two equal halves.

### 7. Key Learning

Learned how to count characters using dictionaries, identify anagrams, find the first unique character, and calculate the minimum deletions needed to make strings anagrams.

**Day 8 Completed! ✅**
