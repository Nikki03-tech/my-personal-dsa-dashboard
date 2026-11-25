# Day 26 — Tries and Prefix Searching

**Date:** November 26, 2026 | **Language:** Python  
**Status:** COMPLETED — 4/4 Accepted (user-confirmed November 25, 2026).

## 1. Concepts Learned
- A Trie (Prefix Tree) stores strings character by character.
- Each node stores child nodes; a terminal marker identifies a complete word.
- Prefix counts support fast contact searches.
- DFS explores possible branches for wildcard characters.
- A Trie can detect when one word is a prefix of another.

## 2. Questions, Python Solutions and Explanations

### Q1 — LeetCode: [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)

Implement `insert`, `search`, and `startsWith`.

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end = True

    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end

    def startsWith(self, prefix):
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True
```

**Example:** Insert `apple`; `search("apple")` is True, `search("app")` is False until app is inserted, and `startsWith("app")` is True.

**Explanation:** Insert creates missing child nodes and marks the last node as a complete word. Search checks the full path and terminal flag. Prefix search checks only whether the path exists.

**Complexity:** O(L) time per operation; O(total characters) storage.

### Q2 — LeetCode: [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)

A dot (`.`) matches any one character.

```python
class WordDictionary:
    def __init__(self):
        self.root = {}

    def addWord(self, word):
        node = self.root
        for char in word:
            if char not in node:
                node[char] = {}
            node = node[char]
        node["#"] = True

    def search(self, word):
        def dfs(node, index):
            if index == len(word):
                return "#" in node

            char = word[index]
            if char == ".":
                for key, child in node.items():
                    if key != "#" and dfs(child, index + 1):
                        return True
                return False

            if char not in node:
                return False
            return dfs(node[char], index + 1)

        return dfs(self.root, 0)
```

**Example:** After adding bad, dad, mad: search("pad") is False, search("bad") is True, search(".ad") is True, and search("b..") is True.

**Explanation:** Follow a normal character through one child. For a dot, use DFS to explore every child. A match requires reaching the terminal marker.

**Complexity:** Add O(L). Search O(L) without wildcards; wildcard branching can be exponential in the broad worst case (O(26^L)). Trie storage O(total characters).

### Q3 — HackerRank: [Contacts](https://www.hackerrank.com/challenges/contacts/problem)

Support `add name` and `find prefix`.

```python
def contacts(queries):
    root = {"children": {}, "count": 0}
    result = []

    for operation, value in queries:
        node = root

        if operation == "add":
            for char in value:
                if char not in node["children"]:
                    node["children"][char] = {
                        "children": {}, "count": 0
                    }
                node = node["children"][char]
                node["count"] += 1
        else:
            for char in value:
                if char not in node["children"]:
                    node = None
                    break
                node = node["children"][char]

            result.append(node["count"] if node else 0)

    return result
```

**Example:** Adding ed, eddie, edward; finding ed returns 3. Adding edwina and finding edw returns 2. Finding a returns 0.

**Explanation:** Each Trie node stores how many inserted names pass through it. A find operation follows the prefix and returns that node's count.

**Complexity:** O(total query characters) time; O(total inserted characters) storage.

### Q4 — HackerRank: [No Prefix Set](https://www.hackerrank.com/challenges/three-month-preparation-kit-no-prefix-set/problem)

Print GOOD SET if no word is a prefix of another; otherwise print BAD SET and the first invalid word.

```python
def noPrefix(words):
    root = {}

    for word in words:
        node = root

        for char in word:
            if "#" in node:
                print("BAD SET")
                print(word)
                return

            if char not in node:
                node[char] = {}
            node = node[char]

        if "#" in node or node:
            print("BAD SET")
            print(word)
            return

        node["#"] = True

    print("GOOD SET")
```

**Example:** `["aab", "defgab", "abcde", "aabcde"]` prints BAD SET, then aabcde.

**Explanation:** A terminal marker encountered before the new word ends means an earlier word is a prefix. Existing children after the new word ends mean the new word is a prefix of an earlier word. The terminal marker also detects duplicates.

**Complexity:** O(total characters) time and storage.

## 3. Mistakes to Avoid
- Distinguish complete-word search from prefix search.
- Mark the end of every complete word.
- Explore all branches for wildcard search.
- Update prefix counts for Contacts.
- Check both directions of prefix conflicts and duplicates in No Prefix Set.

## 4. Coding Problems Completed — 4/4 Accepted
- [x] LeetCode — Implement Trie (Prefix Tree)
- [x] LeetCode — Design Add and Search Words Data Structure
- [x] HackerRank — Contacts
- [x] HackerRank — No Prefix Set

**Confirmation:** All four submissions were reported Accepted on November 25, 2026.

## 5. Complexity Summary
| Problem | Time | Space |
|---|---|---|
| Implement Trie | O(L) per operation | O(total characters) |
| Word Dictionary | O(L) without wildcards; branching with dots | O(total characters) |
| Contacts | O(total query characters) | O(total inserted characters) |
| No Prefix Set | O(total characters) | O(total characters) |

## 6. Mock Interview Questions
1. What is a Trie? A tree-like structure for storing and searching strings by prefix.
2. Why use a terminal marker? To distinguish a complete word from a prefix.
3. Difference between search and startsWith? One checks a complete word; the other checks a prefix path.
4. How does wildcard search work? DFS explores possible child branches.
5. Why does Contacts use counts? Each prefix node records how many names pass through it.
6. How does No Prefix Set detect conflicts? It detects a terminal ancestor or existing descendants.

## 7. Key Learning
Tries support prefix search, autocomplete, wildcard search, contact counting and prefix-conflict detection. The key ideas are child nodes, terminal markers, DFS branching and prefix counts.

**Day 26 completed — 4/4 Accepted.**
