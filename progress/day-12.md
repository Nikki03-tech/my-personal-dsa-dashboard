# Day 12 — Intervals and merging ranges

**Date:** November 12, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4 assigned problems submitted and accepted.

## Updated dashboard assignments — four questions per day

### LeetCode
- [x] **Q1 — [Merge Intervals](https://leetcode.com/problems/merge-intervals/)** — Accepted
- [x] **Q2 — [Insert Interval](https://leetcode.com/problems/insert-interval/)** — Accepted

### HackerRank
- [x] **Q1 — [Interval Selection](https://www.hackerrank.com/challenges/interval-selection/problem)** — Accepted
- [x] **Q2 — [Gridland Metro](https://www.hackerrank.com/challenges/gridland-metro/problem)** — Accepted

## Today's learning goals
- [x] Represent an interval as [start, end]
- [x] Sort by start value
- [x] Detect overlap and extend the current end
- [x] Insert a new interval while preserving sorted order
- [x] Use a greedy strategy for interval selection
- [x] Merge track ranges row by row in a grid

## Core patterns learned

1. **Merge Intervals:** Sort by start. Merge when the next start is at or before the current end.
2. **Insert Interval:** Add intervals before the new range, merge all overlaps, then append the remaining intervals.
3. **Interval Selection:** Sort by start. Keep at most two selected intervals covering any point; if three overlap, remove the one with the latest ending point.
4. **Gridland Metro:** Group track segments by row, merge overlapping/adjacent ranges, count occupied cells, and subtract from the total grid cells.

## Important edge cases
- Empty input and a single interval.
- Touching endpoints, e.g. [1, 4] and [4, 5].
- One interval fully contained inside another.
- Intervals already sorted in reverse order.
- Three intervals sharing a common point in Interval Selection.
- Multiple or overlapping track segments in the same Gridland Metro row.
- No train tracks in Gridland Metro.

## Complexity review
- **Merge Intervals:** O(n log n) time for sorting; O(n) output space.
- **Insert Interval:** O(n) time; O(n) output space.
- **Interval Selection:** O(n log n) time; O(n) auxiliary space for heaps and active intervals.
- **Gridland Metro:** O(k log k) time overall for sorting track segments; O(k) auxiliary space.

## Daily checklist
- [x] Read the concept and trace small examples.
- [x] Complete both LeetCode questions.
- [x] Complete both HackerRank questions.
- [x] Test the supplied examples and HackerRank test cases.
- [x] Review edge cases and time/space complexity.
- [x] Review the final approaches.

## My attempt notes
**First approach:** Learned interval sorting, overlap detection, merging, and greedy selection.

**Where I got stuck:** The Interval Selection submission initially had a typo, `heapq.heappo`, which caused an AttributeError.

**Fix:** Corrected it to `heapq.heappop` and submitted the corrected solution.

**Key insight / final approach:** Sort intervals by their starting values. Merge overlapping ranges for Q1/Q2; use a greedy heap strategy for Q3; group and merge track ranges by row for Q4.

**Submission result:** All four assigned problems were submitted and accepted, as confirmed by the user.

**What I learned / what to revise:** Inclusive interval endpoints matter. For Interval Selection, the condition is that no point is covered by more than two selected intervals (not that every selected pair must be disjoint). For Gridland Metro, overlapping track cells in one row must only be counted once.
