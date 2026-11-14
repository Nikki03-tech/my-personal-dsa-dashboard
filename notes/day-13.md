# Day 13 — Binary Search Fundamentals

**Date:** November 13, 2026  
**Language:** Python  
**Status:** Completed ✅

### 1. Concepts Learned

- Binary Search finds a target efficiently in a sorted array by repeatedly dividing the search range in half.
- \`low\` is the starting index, \`high\` is the ending index, and \`mid\` is the middle index.
- Calculate the middle using \`mid = (low + high) // 2\`.
- If the middle value is smaller than the target, search the right half.
- If the middle value is greater than the target, search the left half.
- Search Insert Position uses the final value of \`low\` as the insertion index when the target is missing.
- Binary Search on Answer searches a range of possible answers, such as the minimum number of days needed to produce a goal.
- Binary Search takes O(log n) time because the search range is halved each time.

### 2. Important Logic

**Binary Search — LeetCode**

\`\`\`python
class Solution:
    def search(self, nums, target):
        low = 0
        high = len(nums) - 1

        while low <= high:
            mid = (low + high) // 2

            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                low = mid + 1
            else:
                high = mid - 1

        return -1
\`\`\`

**Search Insert Position — LeetCode**

\`\`\`python
class Solution:
    def searchInsert(self, nums, target):
        low = 0
        high = len(nums) - 1

        while low <= high:
            mid = (low + high) // 2

            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                low = mid + 1
            else:
                high = mid - 1

        return low
\`\`\`

**Intro to Tutorial Challenges — HackerRank**

\`\`\`python
def introTutorial(V, arr):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2

        if arr[mid] == V:
            return mid
        elif arr[mid] < V:
            low = mid + 1
        else:
            high = mid - 1

    return -1
\`\`\`

**Minimum Time Required — HackerRank**

\`\`\`python
def minTime(machines, goal):
    low = 1
    high = min(machines) * goal

    while low < high:
        mid = (low + high) // 2
        total = 0

        for machine in machines:
            total += mid // machine
            if total >= goal:
                break

        if total >= goal:
            high = mid
        else:
            low = mid + 1

    return low
\`\`\`

### 3. Mistakes Corrected

- Corrected the middle-index calculation: when \`low = 0\` and \`high = 5\`, \`mid = 2\), not 3.
- Learned that Binary Search needs sorted input so we can safely discard half of the range.
- Understood why \`low = mid + 1\` moves right and \`high = mid - 1\` moves left.
- Learned the difference between returning \`-1\` when a target is missing and returning \`low\` as an insertion position.
- Understood why Minimum Time Required keeps the current midpoint as \`high\` when enough items are produced: a smaller time may also work.
- Learned that \`mid // machine\` calculates the number of items a machine can produce in the chosen time.

### 4. Coding Problems Completed

| **Platform** | **Problem** | **Result** |
|---|---|---|
| LeetCode | Binary Search | Accepted ✅ |
| LeetCode | Search Insert Position | Accepted ✅ |
| HackerRank | Intro to Tutorial Challenges | Accepted ✅ |
| HackerRank | Minimum Time Required | Accepted ✅ |

**Problem Links:**

- [LeetCode — Binary Search](https://leetcode.com/problems/binary-search/)
- [LeetCode — Search Insert Position](https://leetcode.com/problems/search-insert-position/)
- [HackerRank — Intro to Tutorial Challenges](https://www.hackerrank.com/challenges/tutorial-intro/problem)
- [HackerRank — Minimum Time Required](https://www.hackerrank.com/challenges/minimum-time-required/problem)

### 5. Time & Space Complexity

| **Problem** | **Time** | **Space** |
|---|---|---|
| Binary Search | O(log n) | O(1) |
| Search Insert Position | O(log n) | O(1) |
| Intro to Tutorial Challenges | O(log n) | O(1) |
| Minimum Time Required | O(n × log(min(machines) × goal)) | O(1) |

**Remember:**

- \`n\` = number of array elements or machines.
- \`//\` performs integer division.
- \`O(log n)\` means the search range is repeatedly divided in half.
- \`mid // machine\` gives the number of items one machine produces in the given time.
- In Minimum Time Required, the outer binary search checks possible times and the loop over machines counts production.

### 6. Mock Interview Questions & Answers

1. **What is Binary Search?**  
   A searching technique that repeatedly divides a sorted search range in half.

2. **Why must the array be sorted?**  
   Sorting lets us decide which half can be discarded after checking the middle element.

3. **What are \`low\`, \`high\`, and \`mid\`?**  
   \`low\` is the starting boundary, \`high\` is the ending boundary, and \`mid\` is the middle index.

4. **Why do we use \`mid + 1\` and \`mid - 1\`?**  
   We have already checked the middle element, so we move past it when searching the remaining half.

5. **What is the time complexity of Binary Search?**  
   O(log n), because the search range is halved at each step.

6. **What is the difference between Binary Search and Search Insert Position?**  
   Binary Search returns -1 if the target is absent; Search Insert Position returns the index where it should be inserted.

7. **What is Binary Search on Answer?**  
   It searches through possible answers and checks whether a candidate answer is feasible.

8. **How does Minimum Time Required work?**  
   It checks how many items all machines can produce in a given time, then searches for the smallest time that reaches the goal.

### 7. Key Learning

Learned how to use Binary Search to find values and insertion positions in sorted arrays, and how to apply Binary Search on Answer to find a minimum feasible time. Practised updating search boundaries, calculating the middle index, checking feasibility, and analysing time and space complexity.

**Day 13 Completed! ✅**
