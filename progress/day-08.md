# Day 08 — Strings and character frequencies

**Date:** November 10–11, 2026  
**Language:** Python  
**Status:** COMPLETED — all four LeetCode and HackerRank solutions confirmed Accepted by user.

## Updated dashboard assignments — four questions per day

### LeetCode
- [x] **Q1 — [Valid Anagram](https://leetcode.com/problems/valid-anagram/)** — Accepted
- [x] **Q2 — [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)** — Accepted

### HackerRank
- [x] **Q1 — [Making Anagrams](https://www.hackerrank.com/challenges/making-anagrams/problem)** — Accepted
- [x] **Q2 — [Anagram](https://www.hackerrank.com/challenges/anagram/problem)** — Accepted

## Today's learning goals
- [x] String traversal
- [x] Character frequency dictionaries
- [ ] Sorting strings as an alternative

## Core practice
- **LeetCode:** [Valid Anagram](https://leetcode.com/problems/valid-anagram/) — Accepted
- **LeetCode:** [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/) — Accepted
- **HackerRank:** [Making Anagrams](https://www.hackerrank.com/challenges/making-anagrams/problem) — Accepted
- **HackerRank:** [Anagram](https://www.hackerrank.com/challenges/anagram/problem) — Accepted

## How to approach it
Count how many times each character appears using dictionaries. Compare frequency information to check anagrams, find unique characters, or calculate the minimum number of deletions/changes.

## Key Python patterns
```python
count[char] = count.get(char, 0) + 1
```

- `enumerate(s)` gives both the index and character.
- `set(s1 + s2)` visits each distinct character across both strings.
- `abs(a - b)` gives the absolute frequency difference.
- For HackerRank Anagram, split an even-length string into two halves; an odd-length string returns `-1`.

## Complexity review
- Frequency counting and comparison are generally **O(n)** time for strings of length n, with **O(k)** auxiliary space for k distinct characters.
- The Anagram problem also uses linear time and frequency storage for the characters in the halves.

## Daily checklist
- [x] Read the concept and trace small examples by hand.
- [x] Complete both assigned LeetCode problems.
- [x] Complete both assigned HackerRank problems.
- [ ] Test all listed edge cases.
- [ ] Explain the approach aloud without reading the solution.
- [ ] Revisit this pattern after 2–3 days.

## My attempt notes
**First approach:** Use dictionaries to count character frequencies.

**Where I got stuck:** Understanding how to compare character frequencies and count the minimum changes/deletions.

**Hints used:** Step-by-step frequency-table tracing and checking whether a character is available in the first-half frequency dictionary.

**Key insight / final approach:** Anagrams have matching character frequencies. For Making Anagrams, add the absolute differences between the two strings' character counts. For HackerRank Anagram, match second-half characters against the first-half counts and count unmatched characters as required changes.

**Time complexity:** O(n) for the frequency-counting approaches.

**Auxiliary space complexity:** O(k), where k is the number of distinct characters.

**What I learned / what to revise:** Dictionary frequency counting, `get()`, `enumerate()`, `set()`, `abs()`, splitting strings into halves, and handling odd-length strings.
