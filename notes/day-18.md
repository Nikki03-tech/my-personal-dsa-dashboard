# Day 18 — Recursion and Advanced Backtracking

**Date:** November 18, 2026  
**Language:** Python  
**Status:** COMPLETED — 4/4 accepted (confirmed November 19, 2026)

## 1. Concepts Learned

- **Recursion:** a function solves a problem by calling itself on a smaller input.
- **Base case:** the stopping condition. Without it, recursion may continue until a recursion error.
- **Recursive case:** reduces the problem and moves toward the base case.
- **Call stack:** Python tracks active function calls and returns to the previous call when the current call finishes.
- **Backtracking:** choose an option, explore it recursively, then undo the choice before trying another option.
- **Subsets vs permutations:** subsets select items and ignore order; permutations arrange items, so order matters.

## 2. Important Logic

**Subsets — include or exclude**

At each index, explore two choices: include the current value, then exclude it. Save a copy of the current list so later backtracking does not change an already-saved subset.

~~~python
def subsets(nums):
    result = []
    current = []

    def backtrack(index):
        if index == len(nums):
            result.append(current.copy())
            return

        current.append(nums[index])
        backtrack(index + 1)
        current.pop()
        backtrack(index + 1)

    backtrack(0)
    return result
~~~

**Permutations — choose unused values**

Use a Boolean used array. Add one unused value, recurse, then remove it and mark it unused again.

~~~python
def permute(nums):
    result = []
    current = []
    used = [False] * len(nums)

    def backtrack():
        if len(current) == len(nums):
            result.append(current.copy())
            return
        for i in range(len(nums)):
            if used[i]:
                continue
            used[i] = True
            current.append(nums[i])
            backtrack()
            current.pop()
            used[i] = False

    backtrack()
    return result
~~~

**Recursive Digit Sum — reduce to one digit**

Calculate the sum of the digits in the initial string and multiply by k. Keep summing digits until one digit remains.

~~~python
def superDigit(n, k):
    total = sum(int(ch) for ch in n) * k

    def digit_sum(value):
        if value < 10:
            return value
        return digit_sum(sum(int(ch) for ch in str(value)))

    return digit_sum(total)
~~~

**Crossword Puzzle — place and undo**

Find horizontal and vertical word slots. For each word, try a compatible slot. Place only letters that were blank, recurse with the next word, and undo only the cells changed by that attempt if it fails. This is constraint-based backtracking.

## 3. Mistakes Corrected

- Do not forget the base case.
- Store a copy of the current path, not the changing list itself.
- Always undo a choice after the recursive call.
- Do not confuse subsets with permutations: order matters only for permutations.
- In crossword backtracking, restore only cells changed by the current attempt; do not erase fixed letters.

## 4. Coding Problems Completed

### LeetCode
- [x] [Subsets](https://leetcode.com/problems/subsets/) — Accepted
- [x] [Permutations](https://leetcode.com/problems/permutations/) — Accepted

### HackerRank
- [x] [Recursive Digit Sum](https://www.hackerrank.com/challenges/recursive-digit-sum/problem) — Accepted
- [x] [Crossword Puzzle](https://www.hackerrank.com/challenges/crossword-puzzle/problem) — Accepted

### Concept Review
- [x] Explain base case vs recursive case.
- [x] Trace choose → explore → undo.
- [x] Explain why a copy of the current path is required.
- [x] Compare subsets and permutations.

## 5. Time & Space Complexity

| Problem | Time complexity | Auxiliary space |
|---|---|---|
| Subsets | O(n × 2ⁿ), including copying each subset | O(n) recursion/path space, excluding output |
| Permutations | O(n × n!), including copying each permutation | O(n) recursion/path/used space, excluding output |
| Recursive Digit Sum | Proportional to the number of digits processed across reductions | O(log S) recursive depth for reduced value S |
| Crossword Puzzle | Exponential in the worst case because placements branch and backtrack | Board plus recursion/placement state |

Output space is separate from auxiliary space. Subsets produce 2ⁿ results and permutations produce n! results.

## 6. Mock Interview Questions & Answers

1. **What is a base case?** The condition that stops recursive calls.
2. **What is the call stack?** The memory structure that tracks active function calls and where each call should return.
3. **What is backtracking?** Trying a choice, exploring it, and undoing it when returning to explore another choice.
4. **Why save a copy of the current list?** To save a snapshot instead of a reference to a list that will keep changing.
5. **What is the difference between subsets and permutations?** Subsets ignore order; permutations treat different orders as different results.
6. **Why use a used array for permutations?** To avoid selecting the same input position more than once in one permutation.

## 7. Key Learning

Recursion breaks a problem into smaller versions. Backtracking explores multiple possible choices safely by undoing each choice after exploring it. Always identify the base case, make progress toward it, and restore shared state before exploring another branch.
