# Day 13 — Binary Search Fundamentals

**Date:** November 13, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4 assigned problems submitted and accepted.

## Updated dashboard assignments — four questions per day

### LeetCode
- [x] **Q1 — [Binary Search](https://leetcode.com/problems/binary-search/)** — Accepted
- [x] **Q2 — [Search Insert Position](https://leetcode.com/problems/search-insert-position/)** — Accepted

### HackerRank
- [x] **Q1 — [Intro to Tutorial Challenges](https://www.hackerrank.com/challenges/tutorial-intro/problem)** — Accepted
- [x] **Q2 — [Minimum Time Required](https://www.hackerrank.com/challenges/minimum-time-required/problem)** — Accepted

## Today's learning goals
- [x] Understand the `low`, `mid`, and `high` boundaries.
- [x] Understand why Binary Search requires sorted input.
- [x] Calculate the middle index using integer division.
- [x] Update the search range by moving left or right.
- [x] Find an insertion position when a target is absent.
- [x] Apply Binary Search on Answer to find a minimum feasible time.

## Core patterns learned

1. **Binary Search:** Calculate `mid`, compare `nums[mid]` with the target, and discard the half that cannot contain the target.
2. **Search Insert Position:** Use the same binary search; when the target is absent, the final `low` is its insertion position.
3. **Intro to Tutorial Challenges:** Use binary search on the sorted array and return the matching index.
4. **Minimum Time Required:** Binary search a range of possible times. Count production with `mid // machine`; if the goal is reached, try a smaller time, otherwise try a larger time.

## Important edge cases to review
- Empty array and one-element array for index-based binary search.
- Target at the first or last position.
- Target smaller than every element or larger than every element.
- Target not present between two elements.
- For Minimum Time Required, a goal that can be reached by one machine and a goal that requires multiple machines.
- A candidate time that produces exactly the goal versus more than the goal.

## Complexity review
- **Binary Search:** O(log n) time; O(1) auxiliary space.
- **Search Insert Position:** O(log n) time; O(1) auxiliary space.
- **Intro to Tutorial Challenges:** O(log n) time; O(1) auxiliary space.
- **Minimum Time Required:** O(n × log(min(machines) × goal)) time; O(1) auxiliary space.

## Daily checklist
- [x] Read the concept and trace examples.
- [x] Complete both LeetCode questions.
- [x] Complete both HackerRank questions.
- [x] Review the final approaches.
- [x] Review time and space complexity.
- [ ] Independently test additional edge cases.
- [ ] Revisit this pattern after 2–3 days.

## My attempt notes
**First approach:** Learned standard binary search using `low`, `high`, and `mid`, then applied the same idea to insertion position and tutorial search.

**Where I got stuck:** Initially calculated the middle index incorrectly. For `low = 0` and `high = 5`, the correct `mid` is `2`.

**Key insight / final approach:** For index search, compare the middle value and discard half the range. For Search Insert Position, return `low` after the loop. For Minimum Time Required, binary search the possible time and count how many items the machines can produce.

**Submission result:** All four assigned problems were submitted and accepted, as confirmed by the user.

**What I learned / what to revise:** Revise the middle-index formula, boundary updates, the difference between returning `-1` and `low`, and the feasibility check used in Binary Search on Answer.
