# Day 11 — Advanced Hashing and Grouping

**Date:** November 11, 2026  
**Language:** Python  
**Status:** Completed ✅

### 1. Concepts Learned

- A dictionary can store lists as values.
- A common key can group related words or substrings.
- An anagram contains the same characters with the same frequencies.
- Sorting the letters of a word creates a common signature for anagrams.
- A tuple of character counts can also be used as an anagram signature.
- A fixed-size sliding window can find anagrams inside another string.
- A dictionary can count how many times a substring signature has appeared.
- A palindrome can have at most one character with an odd frequency.

### 2. Important Logic

**Group Anagrams**
~~~python
groups = {}

for word in strs:
    key = ''.join(sorted(word))

    if key not in groups:
        groups[key] = []

    groups[key].append(word)

return list(groups.values())
~~~

**Find All Anagrams in a String — Window Update**
~~~python
window_count[new_char] = window_count.get(new_char, 0) + 1

window_count[old_char] -= 1

if window_count[old_char] == 0:
    del window_count[old_char]
~~~
Compare the window frequency with the frequency of the pattern. If they match, record the window's starting index.

**Sherlock and Anagrams**
~~~python
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
~~~

**Game of Thrones - I**
~~~python
frequency = {}

for char in s:
    frequency[char] = frequency.get(char, 0) + 1

odd_count = 0

for value in frequency.values():
    if value % 2 != 0:
        odd_count += 1

return "YES" if odd_count <= 1 else "NO"
~~~

### 3. Mistakes Corrected

- Learned to use a sorted word as a common key for anagram groups.
- Understood why we join sorted letters into a string key.
- Learned to store multiple words in a list under one dictionary key.
- Understood that anagram checking needs matching character frequencies, not just matching lengths.
- Learned to remove zero-frequency keys when directly comparing frequency dictionaries.
- Understood why Sherlock and Anagrams adds the previous frequency before increasing the current key count.
- Learned that a rearrangeable palindrome can have only zero or one odd character frequency.

### 4. Coding Problems Completed

| **Platform** | **Problem** | **Result** |
| --- | --- | --- |
| LeetCode | Group Anagrams | Accepted ✅ |
| LeetCode | Find All Anagrams in a String | Accepted ✅ |
| HackerRank | Sherlock and Anagrams | Accepted ✅ |
| HackerRank | Game of Thrones - I | Accepted ✅ |

### 5. Time & Space Complexity

| **Problem** | **Time** | **Space** |
| --- | --- | --- |
| Group Anagrams using sorted keys | O(n × k log k) | O(n × k) for grouped words and keys |
| Find All Anagrams in a String | O(n) for a fixed alphabet | O(1) frequency space for a fixed alphabet |
| Sherlock and Anagrams using sorted substrings | O(n³ log n) upper bound | O(n³) total stored key characters in this approach |
| Game of Thrones - I | O(n) | O(1) for a fixed lowercase alphabet |

**Remember:**

- n = input string length or number of words, depending on the problem.
- k = maximum word length or alphabet size, depending on the problem.
- A signature is a normalized representation used as a dictionary key.
- Matching signatures mean the words or substrings are anagrams.

### 6. Mock Interview Questions & Answers

1. **What is Group Anagrams?**  
   It groups words that contain the same characters with the same frequencies.
2. **Why do we sort each word?**  
   Anagrams produce the same sorted string, which we can use as a common dictionary key.
3. **Why store a list inside a dictionary?**  
   So multiple words with the same signature can be grouped under one key.
4. **How does Find All Anagrams use Sliding Window?**  
   It checks a window the same size as the pattern and updates character frequencies as the window moves.
5. **Why do we use a dictionary in Sherlock and Anagrams?**  
   To count earlier substrings with the same sorted signature and count matching pairs efficiently.
6. **Why do we add groups[key] before incrementing it?**  
   It counts the earlier matching substrings that can form a pair with the current substring.
7. **How many odd character frequencies can a palindrome have?**  
   At most one, because one character can occupy the middle position.

### 7. Key Learning

Learned how to group anagrams using dictionary keys, find anagram windows using character frequencies, count anagram substring pairs, and check whether a string can be rearranged into a palindrome.

**Day 11 Completed! ✅**
