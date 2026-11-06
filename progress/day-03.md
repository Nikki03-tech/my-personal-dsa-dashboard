# Day 03 — Array traversal and prefix sums

**Date:** 2026-11-03  
**Status:** Completed  
**Language:** Python  
**LeetCode:** [Running Sum of 1D Array](https://leetcode.com/problems/running-sum-of-1d-array/) — Accepted  
**HackerRank:** [Arrays - DS](https://www.hackerrank.com/challenges/arrays-ds/problem) — Accepted (7 test cases)


## Updated dashboard assignments — four questions per day

> The original two-problem work for this day is preserved below. Under the revised dashboard, Q1 on each platform was completed in the earlier session; the newly added Q2 tasks are still pending. The historical completion status below does not mean the new Q2 tasks have been attempted.

### LeetCode

- [x] **Q1 — [Running Sum of 1D Array](https://leetcode.com/problems/running-sum-of-1d-array/)** — completed in the original plan
- [ ] **Q2 — [Build Array from Permutation](https://leetcode.com/problems/build-array-from-permutation/)** — newly added in the four-question plan; not yet attempted

### HackerRank

- [x] **Q1 — [Arrays - DS](https://www.hackerrank.com/challenges/arrays-ds/problem)** — completed in the original plan
- [ ] **Q2 — [Arrays: Left Rotation](https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem)** — newly added in the four-question plan; not yet attempted

## Today's focus

Array traversal, zero-based indexing, running sums / prefix sums, reverse traversal, and time and space complexity.

## Checklist

- [x] Review the concept and write a small example by hand.
- [x] Attempt the LeetCode problem independently — Running Sum of 1D Array (Accepted).
- [x] Attempt the HackerRank exercise — Arrays - DS (Accepted; 7 test cases).
- [x] Explain the approach and answer mock interview questions.
- [x] State the time and space complexity.
- [x] Record today's completed work in this progress log.

> Note: The dashboard's completion tick is stored separately in the browser; this GitHub progress file does not change that local dashboard state.

## My notes

**My first approach:**

For the running sum, initialize `total = 0` and an empty `result` list. Traverse each value in `nums`, add the current `number` to `total`, and append the updated total to `result`. Return the result after the loop.

For reverse traversal, start from the last valid index and move backwards to index zero, appending each indexed value to a new list.

**Where I got stuck:**

- Initially used `nums` instead of the current loop variable `number` when updating the running total.
- Needed to place `append()` inside the loop so each intermediate result is saved.
- Learned that `return` must be outside the loop when the full result is required; returning inside the loop exits the function early.
- Clarified that Python's `range()` excludes its stop value.
- Clarified the difference between output space and auxiliary space.

**Hint(s) used:**

Not specified in today's notes.

**Key insight / final approach:**

Running Sum:

```python
total = 0
result = []

for number in nums:
    total = total + number
    result.append(total)

return result
```

Reverse Array:

```python
result = []

for i in range(len(a) - 1, -1, -1):
    result.append(a[i])

return result
```

The accumulator stores the cumulative sum as the array is traversed. For reverse traversal, `range(len(a) - 1, -1, -1)` visits indexes from the last index down to zero. Return the completed list after the loop.

**Time complexity:**

- Running Sum: O(n), because each element is visited once.
- Reverse Array: O(n), because each element is visited once.

**Space complexity:**

- Running Sum: O(n) output space for the result list; O(1) auxiliary space excluding the output.
- Reverse Array: O(n) output space for the reversed list; O(1) auxiliary space excluding the output.

**What I learned today:**

I practiced traversing arrays, using zero-based indexes, maintaining cumulative totals with an accumulator, reversing an array with indexes, and explaining time and space complexity. I also practiced mock interview questions about the approach, the difference between `nums` and `number`, why `return` belongs after the loop, why the reverse range uses `-1`, and output space versus auxiliary space.

**Next step / revision needed:**

Review the accumulator pattern, reverse-loop boundaries, and the distinction between output space and auxiliary space.
