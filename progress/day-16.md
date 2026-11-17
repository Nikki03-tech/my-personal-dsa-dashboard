# Day 16 — Stacks, Queues & Monotonic Stacks

**Date:** November 16, 2026  
**Language:** Python  
**Status:** COMPLETED ✅

## 1. Concepts Learned

- A Stack follows LIFO (Last In, First Out).
- `append()` adds an element to the top of a stack.
- `pop()` removes the top element.
- `stack[-1]` accesses the top element without removing it.
- A Monotonic Stack maintains elements in increasing or decreasing order.
- Monotonic Stacks help solve Next Greater Element, Daily Temperatures and Largest Rectangle problems.
- A Queue follows FIFO (First In, First Out).
- A Dictionary stores key-value pairs and provides efficient lookups.
- Stack problems can often be solved in O(n) time because each element is pushed and popped at most once.

## 2. Important Logic

### Daily Temperatures — LeetCode

```python
class Solution:
    def dailyTemperatures(self, temperatures):
        result = [0] * len(temperatures)
        stack = []

        for i, temp in enumerate(temperatures):
            while stack and temp > temperatures[stack[-1]]:
                previous = stack.pop()
                result[previous] = i - previous

            stack.append(i)

        return result
```

- Store indexes in the stack.
- When a warmer temperature appears, pop the previous index.
- Calculate waiting days using `i - previous`.

### Next Greater Element I — LeetCode

```python
class Solution:
    def nextGreaterElement(self, nums1, nums2):
        stack = []
        greater = {}

        for num in nums2:
            while stack and num > stack[-1]:
                previous = stack.pop()
                greater[previous] = num

            stack.append(num)

        result = []

        for num in nums1:
            result.append(greater.get(num, -1))

        return result
```

- Use a stack to find the next greater element.
- Store the answers in a dictionary.
- Use `get(num, -1)` when no greater element exists.

### Balanced Brackets — HackerRank

```python
def isBalanced(s):
    stack = []

    pairs = {
        ')': '(',
        '}': '{',
        ']': '['
    }

    for char in s:
        if char in "({[":
            stack.append(char)
        else:
            if not stack:
                return "NO"

            if stack.pop() != pairs[char]:
                return "NO"

    if not stack:
        return "YES"

    return "NO"
```

- Push opening brackets into the stack.
- Match every closing bracket with the top opening bracket.
- Return NO if brackets do not match or remain unclosed.

### Largest Rectangle — HackerRank

```python
def largestRectangle(heights):
    stack = []
    max_area = 0

    heights = heights + [0]

    for i in range(len(heights)):
        while stack and heights[stack[-1]] > heights[i]:
            height = heights[stack.pop()]

            if not stack:
                width = i
            else:
                width = i - stack[-1] - 1

            area = height * width
            max_area = max(max_area, area)

        stack.append(i)

    return max_area
```

- Maintain increasing building heights in a stack.
- When a smaller height appears, calculate the rectangle area for the taller building.
- Area = height × width.
- Keep the maximum area.

## 3. Mistakes Corrected / Important Points

- Learned to use `while` instead of `if` when multiple previous elements may need to be popped.
- Understood why indexes are stored in Daily Temperatures instead of temperatures.
- Learned why a dictionary is useful for storing Next Greater Element results.
- Understood why the stack must be empty at the end of Balanced Brackets.
- Learned why a closing bracket must match the most recently opened bracket.
- Understood why we append `0` at the end of Largest Rectangle to process the remaining stack.
- Learned how to calculate rectangle width using the current index and the previous smaller element.
- Understood that each element is pushed and popped at most once in these stack approaches.

## 4. Coding Problems Completed

| Platform | Problem | Result |
|---|---|---|
| LeetCode | [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) | Completed ✅ |
| LeetCode | [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/) | Completed ✅ |
| HackerRank | [Balanced Brackets](https://www.hackerrank.com/challenges/balanced-brackets/problem) | Completed ✅ |
| HackerRank | [Largest Rectangle](https://www.hackerrank.com/challenges/largest-rectangle/problem) | Completed ✅ |

## 5. Time & Space Complexity

| Problem | Time | Space |
|---|---|---|
| Daily Temperatures | O(n) | O(n) |
| Next Greater Element I | O(n + m) | O(n + m) including output |
| Balanced Brackets | O(n) | O(n) |
| Largest Rectangle | O(n) | O(n) |

### Complexity Notes

- `n` = number of elements or brackets.
- `m` = length of the second array in Next Greater Element I.
- `append()` adds an element to a stack.
- `pop()` removes the top element.
- `stack[-1]` accesses the top element.
- `dictionary.get(key, -1)` returns a stored value or -1.
- Area of rectangle = height × width.
- Auxiliary space excludes the returned output.

## 6. Mock Interview Questions & Answers

1. **What is a Stack?**  
   A linear data structure that follows LIFO (Last In, First Out).

2. **What is a Monotonic Stack?**  
   A stack that maintains elements in increasing or decreasing order.

3. **Why do we use a stack in Daily Temperatures?**  
   To keep track of previous temperatures that are waiting for a warmer day.

4. **Why do we store indexes instead of values in Daily Temperatures?**  
   To calculate the number of days between two temperatures.

5. **What is the purpose of a Dictionary in Next Greater Element I?**  
   To store the next greater value for each number and retrieve it efficiently.

6. **How do we check Balanced Brackets?**  
   We push opening brackets and match each closing bracket with the top element of the stack.

7. **How do we calculate the largest rectangle?**  
   Multiply the height of a rectangle by its maximum possible width and track the largest area.

8. **What is the time complexity of a Monotonic Stack solution?**  
   Usually O(n), because every element is pushed and popped at most once.

## 7. Key Learning

Learned how to use stacks, dictionaries and monotonic stacks to solve temperature comparison, next greater element, bracket matching and largest rectangle problems. Improved understanding of LIFO, stack operations, index tracking, rectangle area calculation, and time and space complexity.

**Day 16 Completed! ✅**
