# Day 18 — Recursion and advanced backtracking

**Date:** November 18, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4/4 online judge submissions accepted (confirmed November 19, 2026).


## Updated dashboard assignments — four questions per day

> These are the four assigned problems shown on the current dashboard. All four submissions are now confirmed accepted; the checkboxes below record that status.

### LeetCode
- [x] **Q1 — [Subsets](https://leetcode.com/problems/subsets/)**
- [x] **Q2 — [Permutations](https://leetcode.com/problems/permutations/)**

### HackerRank
- [x] **Q1 — [Recursive Digit Sum](https://www.hackerrank.com/challenges/recursive-digit-sum/problem)**
- [x] **Q2 — [Crossword Puzzle](https://www.hackerrank.com/challenges/crossword-puzzle/problem)**

## Today's learning goals
- [x] Base case and recursive case
- [x] Call stack and recursion tree
- [x] Choose, explore, undo
- [x] Subsets, permutations and combinations

## Core practice
- **LeetCode:** [Subsets](https://leetcode.com/problems/subsets/) — Medium
- **HackerRank / practice:** [Recursive Digit Sum](https://www.hackerrank.com/challenges/recursive-digit-sum/problem)

## How to approach it
At each position, decide whether to include or exclude the current value. Add a copy of the current path when a valid leaf is reached.

## Edge cases to test
Test empty input and one item. Ensure a copy of the current path is stored rather than a reference to a list that will keep changing.

## Optional stretch
[Permutations](https://leetcode.com/problems/permutations/)
Optional Medium: compare permutations (order matters) with combinations (selection matters). Combination Sum is a further stretch.

## Complexity review
- [x] State the time complexity and explain which input size it depends on.
- [x] State auxiliary space separately from output space.
- [x] Explain whether sorting, hashing, or an extra data structure changes the trade-off.

## Daily checklist
- [x] Read the concept and trace a small example by hand.
- [x] Attempt the core LeetCode problem independently.
- [x] Attempt the HackerRank exercise or custom Python drill.
- [x] Test the edge cases above.
- [x] Explain the approach aloud without reading the solution.
- [x] Revisit this pattern after 2–3 days.

## Confirmed submission results

**Submission confirmation (November 19, 2026):** All four problems were reported Accepted.
- [x] LeetCode — Subsets
- [x] LeetCode — Permutations
- [x] HackerRank — Recursive Digit Sum
- [x] HackerRank — Crossword Puzzle

**Key revision:** Recursion needs a base case and a smaller recursive call. Backtracking follows choose → explore → undo. Subsets make include/exclude decisions; permutations track which values are already used.

## My attempt notes
**First approach:**  

**Where I got stuck:**  

**Hints used:**  

**Key insight / final approach:**  

**Time complexity:**  

**Auxiliary space complexity:**  

**What I learned / what to revise:**  
