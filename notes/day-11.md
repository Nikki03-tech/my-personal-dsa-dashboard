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


---

## Previous complete version (preserved from GitHub history)

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
