# Day 04 — Hash sets

**Date:** November 4, 2026  
**Language:** Python  
**Status:** COMPLETED

**LeetCode:** [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) — Easy — **Accepted**  
**HackerRank:** [Sparse Arrays](https://www.hackerrank.com/challenges/sparse-arrays/problem) — **Accepted**


## Updated dashboard assignments — four questions per day

> The original two-problem work for this day is preserved below. Under the revised dashboard, Q1 on each platform was completed in the earlier session; the newly added Q2 tasks are still pending. The historical completion status below does not mean the new Q2 tasks have been attempted.

### LeetCode

- [x] **Q1 — [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)** — completed in the original plan
- [ ] **Q2 — [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)** — newly added in the four-question plan; not yet attempted

### HackerRank

- [x] **Q1 — [Sparse Arrays](https://www.hackerrank.com/challenges/sparse-arrays/problem)** — completed in the original plan
- [ ] **Q2 — [Set .add()](https://www.hackerrank.com/challenges/py-set-add/problem)** — newly added in the four-question plan; not yet attempted

## 1. Concepts learned

- Sets store unique elements and do not contain duplicates.
- Sets are mutable; elements can be added and removed.
- Lists are mutable and allow duplicates.
- Strings are immutable.
- `set()` creates an empty set.
- `.add()` inserts an element into a set.
- `in` checks whether an element exists.
- `not in` checks whether an element does not exist.
- Sets do not guarantee element order.
- The `in` membership operator is different from the `is` identity operator.

## 2. Important logic

### Contains Duplicate

```python
seen = set()

for number in nums:
    if number in seen:
        return True
    seen.add(number)

return False
```

The set stores values that have already been visited. If the current number is already in `seen`, a duplicate exists. Otherwise, add it and continue. Return `False` only after the full traversal finds no duplicate.

### Sparse Arrays

```python
result = []

for query in queries:
    count = 0

    for word in stringList:
        if word == query:
            count = count + 1

    result.append(count)

return result
```

The outer loop selects each query. The inner loop checks that query against every string and counts its occurrences. Each count is appended to the result list.

## 3. Mistakes corrected

- Initially thought sets were immutable; learned that sets are mutable.
- Learned that lists are also mutable, while strings are immutable.
- Understood that creating a set removes duplicates from the new set, not from the original list.
- Learned the difference between `in` and `is`.
- Understood why `return True` belongs inside the loop when a duplicate is found, while `return False` belongs after the loop.
- Corrected a variable-name mistake in HackerRank (`string` versus `stringList`).

## 4. Coding problems completed

| Platform | Problem | Result |
|---|---|---|
| LeetCode | Contains Duplicate | **Accepted** |
| HackerRank | Sparse Arrays | **Accepted** |

## 5. Time and space complexity

| Problem | Time | Space |
|---|---|---|
| Contains Duplicate | O(n) average | O(n) auxiliary space for the set |
| Sparse Arrays | O(q × s) | O(q) output + O(1) auxiliary space |

Where:
- `n` = number of array elements.
- `q` = number of queries.
- `s` = number of strings.

Important complexity facts:
- Set lookup: O(1) average time.
- List lookup: O(n) time.
- Contains Duplicate traverses the array once, with average O(1) set membership checks.
- Sparse Arrays compares each query with every string, giving O(q × s) time.
- The Sparse Arrays result list grows with the number of queries, so output space is O(q).

## 6. Mock interview questions and answers

**Q1. What is a Set?**  
A collection of unique elements that does not allow duplicates.

**Q2. What is the difference between a List and a Set?**  
Lists allow duplicates and preserve insertion order. Sets store unique elements and do not guarantee element order.

**Q3. How do we detect duplicates?**  
Check whether the current number exists in `seen`. If it does, return `True`; otherwise, add it to the set.

**Q4. Why is Contains Duplicate O(n) average time?**  
We traverse the array once and use average O(1) set membership checks.

**Q5. Why use two loops in Sparse Arrays?**  
The outer loop selects each query; the inner loop checks it against every string.

**Q6. What is Sparse Arrays complexity?**  
O(q × s) time because each of the q queries is compared with all s strings.

**Q7. Why is a Set more efficient than a List for duplicate detection?**  
Set membership takes O(1) average time, whereas list membership takes O(n) time.

## 7. Key insight / final approach

For Contains Duplicate, keep a set of previously seen numbers. Check membership before adding the current number. This detects a duplicate in one traversal using average O(1) membership checks. For Sparse Arrays, count each query by comparing it with every string and store the counts in a result list.

## 8. What I learned today

I learned how to use sets to detect duplicates efficiently, check membership, and understand the difference between mutable sets/lists and immutable strings. I also practised counting string occurrences using nested loops and explaining the time and space complexity of both approaches.

## 9. Revision needed

- Set versus list membership complexity.
- The difference between `in` and `is`.
- Why `return True` can be inside the loop but `return False` must be after it.
- Sparse Arrays nested-loop complexity: O(q × s).
- Output space versus auxiliary space.
