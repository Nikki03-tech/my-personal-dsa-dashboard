# Day 26 — Tries and prefix searching

**Date:** November 26, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4/4 online-judge submissions reported Accepted on November 25, 2026.

## Confirmed dashboard assignments — 4/4 Accepted

### LeetCode
- [x] **Q1 — [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)** — Accepted
- [x] **Q2 — [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)** — Accepted

### HackerRank
- [x] **Q1 — [Contacts](https://www.hackerrank.com/challenges/contacts/problem)** — Accepted
- [x] **Q2 — [No Prefix Set](https://www.hackerrank.com/challenges/three-month-preparation-kit-no-prefix-set/problem)** — Accepted

**Submission confirmation:** The user reported that all four questions for Day 26 were run, submitted, and all test cases passed on November 25, 2026. This day was completed ahead of its scheduled calendar date.

**Digital study notes:** [Open Day 26 notes](../notes/day-26.md)

## 1. Concepts Learned

- [x] Trie nodes and child maps
- [x] End-of-word markers
- [x] insert(), search() and startsWith()
- [x] Prefix counts, wildcard DFS and prefix conflict detection

## 2. Important Logic

Store words character by character in a Trie. Use terminal markers for complete words, per-prefix counts for Contacts, DFS for wildcard search, and terminal/child checks for No Prefix Set.

## 3. Edge Cases Reviewed

Test a word that is a prefix of another, duplicate words, missing prefixes, wildcard matches on multiple branches, and the first invalid word in No Prefix Set.

## 4. Coding Problems Completed

- [x] LeetCode Q1 — Implement Trie (Prefix Tree)
- [x] LeetCode Q2 — Design Add and Search Words Data Structure
- [x] HackerRank Q1 — Contacts
- [x] HackerRank Q2 — No Prefix Set

## 5. Time and Space Complexity

Trie operations O(L) per word or prefix. Wildcard search can branch. Contacts and No Prefix Set take O(total characters) in the usual alphabet model.

## 6. Mock Interview Questions and Answers

1. **What is a Trie?** A tree-like structure for storing and searching strings by prefix.
2. **What is a terminal marker?** A marker identifying the end of a complete word.
3. **How does wildcard search work?** DFS explores possible child branches.
4. **How do Contacts queries work efficiently?** Each prefix node stores the count of words passing through it.
5. **How can a Trie detect a prefix conflict?** Check for an earlier terminal node along the path or descendants below the new word's endpoint.

## 7. Key Learning

Tries support prefix operations, wildcard matching and prefix-conflict detection. The core concepts are child nodes, terminal markers, DFS branching and prefix counts.

**Day 26 completed — 4/4 Accepted.**
