# Day 12 Notes — Intervals and Greedy Algorithms

**Date:** November 12, 2026  
**Language:** Python  
**Progress:** All 4 assigned questions submitted and accepted.

## 1. What is an interval?

An interval represents a continuous range using two values:

`[start, end]`

For example, `[2, 6]` covers the values from 2 through 6.

Two intervals overlap when their ranges share at least one point. In these problems, endpoints are inclusive, so `[1, 4]` and `[4, 7]` overlap at 4.

---

## Q1. LeetCode — Merge Intervals

Problem: https://leetcode.com/problems/merge-intervals/

**Goal:** Merge all overlapping intervals.

### Python solution

```python
def merge(intervals):
    intervals.sort()
    result = []

    for start, end in intervals:
        if not result or start > result[-1][1]:
            result.append([start, end])
        else:
            result[-1][1] = max(result[-1][1], end)

    return result
```

### Example

```python
intervals = [[1, 4], [4, 5], [7, 9], [8, 10]]
print(merge(intervals))
```

Output:

```text
[[1, 5], [7, 10]]
```

### How it works

1. Sort intervals by their starting value.
2. If the result is empty, add the current interval.
3. If the current start is greater than the last saved end, there is no overlap; add a new interval.
4. Otherwise, merge by updating the last end with `max(old_end, current_end)`.

**Remember:** Use `start > previous_end` to detect a separate interval. If start equals the previous end, the intervals touch and must merge.

**Complexity:** O(n log n) time due to sorting; O(n) output space.

---

## Q2. LeetCode — Insert Interval

Problem: https://leetcode.com/problems/insert-interval/

**Goal:** Insert a new interval into an already sorted, non-overlapping list and merge any overlaps.

### Python solution

```python
def insert(intervals, newInterval):
    result = []
    i = 0
    n = len(intervals)

    # 1. Add intervals that finish before newInterval begins
    while i < n and intervals[i][1] < newInterval[0]:
        result.append(intervals[i])
        i += 1

    # 2. Merge every interval that overlaps newInterval
    while i < n and intervals[i][0] <= newInterval[1]:
        newInterval[0] = min(newInterval[0], intervals[i][0])
        newInterval[1] = max(newInterval[1], intervals[i][1])
        i += 1

    # 3. Add the merged interval
    result.append(newInterval)

    # 4. Add all remaining intervals
    while i < n:
        result.append(intervals[i])
        i += 1

    return result
```

### Example

```python
intervals = [[1, 3], [6, 9]]
newInterval = [2, 5]
print(insert(intervals, newInterval))
```

Output:

```text
[[1, 5], [6, 9]]
```

### How it works

- First loop: copy intervals completely before the new interval.
- Second loop: merge overlapping intervals using `min()` for the start and `max()` for the end.
- Append the merged new interval.
- Final loop: copy intervals that come after it.

**Complexity:** O(n) time; O(n) output space.

---

## Q3. HackerRank — Interval Selection

Problem: https://www.hackerrank.com/challenges/interval-selection/problem

**Important:** This problem does not require every selected interval to be pairwise non-overlapping. The goal is to select as many intervals as possible so that **no point is covered by more than two selected intervals**.

### Greedy idea

1. Sort intervals by starting point.
2. Keep track of selected intervals that are still active.
3. When an interval ends before the next interval starts, remove it from the active set.
4. If three selected intervals overlap, remove the one with the latest ending point. This leaves more room for future intervals.

### Python solution

```python
import heapq

def intervalSelection(intervals):
    intervals.sort(key=lambda x: x[0])

    min_heap = []
    max_heap = []
    active = set()
    selected = 0

    for i, (start, end) in enumerate(intervals):
        # Remove selected intervals that ended before this starts
        while min_heap and min_heap[0][0] < start:
            old_end, idx = heapq.heappop(min_heap)
            if idx in active:
                active.remove(idx)

        # Select the current interval
        active.add(i)
        selected += 1

        heapq.heappush(min_heap, (end, i))
        heapq.heappush(max_heap, (-end, i))

        # At most two selected intervals may cover a point
        if len(active) > 2:
            while max_heap:
                neg_end, idx = heapq.heappop(max_heap)
                if idx in active:
                    active.remove(idx)
                    selected -= 1
                    break

    return selected
```

### Why two heaps?

- `min_heap` finds intervals that have finished.
- `max_heap` (using negative end values) finds the selected interval that ends latest.
- `active` tells us which heap entries are still selected. Heap entries for removed intervals are ignored when they appear later.
- `selected` counts how many intervals remain selected overall.

### HackerRank sample-style test

Input intervals by test case:

```text
(1, 2), (2, 3), (2, 4)       -> 2
(1, 5), (1, 5), (1, 5)       -> 2
(1,10), (1, 3), (4, 6), (7,10) -> 4
(1,10), (1, 3), (3, 6), (7,10) -> 3
```

Expected output:

```text
2
2
4
3
```

**Common submission typo:** Write `heapq.heappop(max_heap)`, not `heapq.heappo(max_heap)`.

**Complexity:** O(n log n) time; O(n) auxiliary space for the heaps and active set.

---

## Q4. HackerRank — Gridland Metro

Problem: https://www.hackerrank.com/challenges/gridland-metro/problem

**Goal:** Find how many grid cells are not occupied by train tracks.

Each track is represented as:

`[row, start_column, end_column]`

### Python solution

```python
def gridlandMetro(n, m, k, track):
    if not track:
        return n * m

    rows = {}

    # Group track intervals by row
    for r, c1, c2 in track:
        if r not in rows:
            rows[r] = []
        rows[r].append((c1, c2))

    occupied = 0

    # Merge ranges separately in each row
    for intervals in rows.values():
        intervals.sort()

        start, end = intervals[0]

        for s, e in intervals[1:]:
            if s <= end:
                end = max(end, e)
            else:
                occupied += end - start + 1
                start, end = s, e

        occupied += end - start + 1

    return n * m - occupied
```

### Example

```python
n = 4
m = 4
k = 2
track = [[2, 2, 3], [3, 1, 4]]

print(gridlandMetro(n, m, k, track))
```

Output:

```text
10
```

### How it works

- Total grid cells = `n * m`.
- Group all track ranges by row because tracks in different rows cannot overlap.
- Sort the ranges in each row.
- Merge overlapping ranges so a cell is never counted twice.
- Count occupied cells using `end - start + 1`.
- Return total cells minus occupied cells.

**Example of merging:** `[1, 3]` and `[2, 5]` become `[1, 5]`, which contains 5 occupied cells, not 6.

**Complexity:** O(k log k) time overall; O(k) auxiliary space.

---

## Day 12 — Quick revision

| Problem | Main pattern | Time |
|---|---|---|
| Merge Intervals | Sorting + merging | O(n log n) |
| Insert Interval | Three-phase insertion | O(n) |
| Interval Selection | Greedy + min/max heaps | O(n log n) |
| Gridland Metro | Group by row + merge ranges | O(k log k) |

## Important Python tools

- `sort()`: sorts intervals.
- `max(a, b)`: extends an interval's ending point.
- `min(a, b)`: finds the earliest starting point.
- `heapq.heappush()`: inserts into a heap.
- `heapq.heappop()`: removes the smallest heap item.
- `set()`: tracks which intervals are currently selected.

## Common mistakes to avoid

1. Forgetting that interval endpoints are inclusive.
2. Using `<` instead of `<=` when checking overlap in Merge Intervals.
3. Forgetting to update both the start and end when inserting an interval.
4. Solving Interval Selection as ordinary pairwise non-overlapping activity selection; its rule is that no point may be covered by more than two selected intervals.
5. Counting overlapping Gridland Metro track cells more than once.
6. Forgetting that Gridland Metro counts columns inclusively, hence `end - start + 1`.

## Completion record

- [x] LeetCode Q1 — Merge Intervals — Accepted
- [x] LeetCode Q2 — Insert Interval — Accepted
- [x] HackerRank Q1 — Interval Selection — Accepted
- [x] HackerRank Q2 — Gridland Metro — Accepted

**Day 12 completed on November 12, 2026.**
