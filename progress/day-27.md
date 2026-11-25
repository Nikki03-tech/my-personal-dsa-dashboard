# Day 27 — Greedy algorithms

**Date:** November 27, 2026  
**Language:** Python  
**Status:** COMPLETED — all 4/4 online-judge submissions reported Accepted on November 25, 2026.

## Confirmed dashboard assignments — 4/4 Accepted

### LeetCode
- [x] **Q1 — [Jump Game](https://leetcode.com/problems/jump-game/)** — Accepted
- [x] **Q2 — [Gas Station](https://leetcode.com/problems/gas-station/)** — Accepted

### HackerRank
- [x] **Q1 — [Mark and Toys](https://www.hackerrank.com/challenges/mark-and-toys/problem)** — Accepted
- [x] **Q2 — [Greedy Florist](https://www.hackerrank.com/challenges/greedy-florist/problem)** — Accepted

**Submission confirmation:** The user reported that all four questions for Day 27 were run, submitted, and all test cases passed on November 25, 2026. This day was completed ahead of its scheduled calendar date.

**Digital study notes:** [Open Day 27 notes](../notes/day-27.md)

## 1. Concepts Learned

- [x] Greedy choice and feasibility
- [x] Track the farthest reachable index
- [x] Running totals and candidate resets
- [x] Sort-first greedy optimization

## 2. Important Logic

Track the farthest reachable position for Jump Game. For Gas Station, track total fuel and the current candidate tank. Sort ascending for Mark and Toys and descending for Greedy Florist.

## 3. Edge Cases Reviewed

Test an unreachable jump, a zero blocking progress, no feasible gas station, exact budget use, one friend, and more flowers than friends.

## 4. Coding Problems Completed

- [x] LeetCode Q1 — Jump Game
- [x] LeetCode Q2 — Gas Station
- [x] HackerRank Q1 — Mark and Toys
- [x] HackerRank Q2 — Greedy Florist

## 5. Time and Space Complexity

Jump Game and Gas Station O(n) time and O(1) auxiliary space. Mark and Toys and Greedy Florist O(n log n) time due to sorting.

## 6. Mock Interview Questions and Answers

1. **What is a greedy algorithm?** It makes a locally optimal choice at each step.
2. **What does farthest reach represent?** The maximum position reachable so far.
3. **Why reset the Gas Station candidate?** A negative running tank rules out the failed candidate segment.
4. **Why sort Mark and Toys ascending?** To buy the maximum number within the budget.
5. **Why sort Greedy Florist descending?** To assign lower multipliers to more expensive flowers.

## 7. Key Learning

Greedy algorithms require a justified local choice. Reachability, running balances and sorting order make these solutions efficient.

**Day 27 completed — 4/4 Accepted.**
