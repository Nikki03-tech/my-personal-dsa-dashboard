# DSA Notes — Day 1

**Date:** November 1, 2026  
**Topic:** Conditions, loops, modulo, time complexity and space complexity  
**Status:** <badge>COMPLETED</badge>


## Updated dashboard assignments — four questions per day

> The original two-problem work for this day is preserved below. Under the revised dashboard, Q1 on each platform was completed in the earlier session; the newly added Q2 tasks are still pending. The historical completion status below does not mean the new Q2 tasks have been attempted.

### LeetCode

- [x] **Q1 — [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)** — completed in the original plan
- [ ] **Q2 — [Number of Steps to Reduce a Number to Zero](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/)** — newly added in the four-question plan; not yet attempted

### HackerRank

- [x] **Q1 — [Solve Me First](https://www.hackerrank.com/challenges/solve-me-first/problem)** — completed in the original plan
- [ ] **Q2 — [Python Loops](https://www.hackerrank.com/challenges/python-loops/problem)** — newly added in the four-question plan; not yet attempted

## 1. Python concepts covered

| Concept | Meaning |
|---|---|
| `if` | Checks a condition |
| `elif` | Checks another condition if the previous condition was false |
| `else` | Runs when the earlier conditions are false |
| `for` | Repeats a task for each item in a sequence |
| `range(1, n + 1)` | Generates numbers from 1 through n |
| `%` | Modulo operator; gives the remainder |
| `and` | Both conditions must be true |
| `append()` | Adds an item to a list |
| `str()` | Converts a value to a string |
| `print()` | Displays output |
| `return` | Sends a value back to the function caller and ends the function |

## 2. Fizz Buzz — LeetCode

**Problem:** [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)  
**Result:** Accepted

### Important logic

- Divisible by both 3 and 5 → `FizzBuzz`
- Divisible by 3 → `Fizz`
- Divisible by 5 → `Buzz`
- Neither → Convert the number to a string

**Remember:** Check divisibility by both 3 and 5 first. Otherwise, a number like 15 would match the condition for 3 before reaching the combined condition.

### Mistakes corrected

- Use `number`, the current loop variable, when checking the current value.
- Use `result.append()` to add each answer to the list.
- Use `str(number)` to convert a number into a string.
- Keep `return result` outside the loop so the function returns the complete list after processing every number.

### Complexity

- **Time:** O(n), because the loop visits each number once.
- **Auxiliary space:** O(1), excluding the returned output list.
- **Output space:** O(n), because the result list stores one item for each input number.

## 3. HackerRank — Solve Me First

**Problem:** [Solve Me First](https://www.hackerrank.com/challenges/solve-me-first/problem)  
**Result:** Accepted

```python
def solveMeFirst(a, b):
    return a + b
```

- **Time complexity:** O(1)
- **Auxiliary space:** O(1)

The function performs one addition and uses a fixed amount of extra working memory.

## 4. Time and space complexity

**Time complexity** describes how the amount of work an algorithm performs grows as the input size increases.

**Space complexity** describes how the memory used by an algorithm grows as the input size increases.

### Common Big O categories reviewed

| Complexity | Name | Basic idea |
|---|---|---|
| O(1) | Constant | Work stays roughly the same as input grows |
| O(log n) | Logarithmic | Work grows slowly as the input grows |
| O(n) | Linear | Work grows in proportion to input size |
| O(n²) | Quadratic | Work can grow with the square of input size |

### Useful patterns

- One loop over n items → usually O(n) time.
- Two nested loops over n items → often O(n²) time.
- One list that grows with n → O(n) space.
- An n-row by n-column matrix → O(n²) space.
- A fixed number of extra variables → O(1) auxiliary space.

**Important:** Big O describes the growth rate, not the exact number of seconds.

### Fizz Buzz space distinction

The returned list needs O(n) output space. When that output is excluded, the additional working memory is O(1) auxiliary space.

## 5. print() versus return

- `print()` displays a value.
- `return` sends a value back to the caller so it can be stored or reused.
- `return` also ends the function.

For Fizz Buzz, the platform expects the completed list to be returned, not merely printed.

## 6. Interview-style questions reviewed

**Q1. What is the difference between print() and return?**  
Print displays output, whereas return sends a value back to the function caller so it can be stored and reused.

**Q2. Why use return result instead of print(result) in Fizz Buzz?**  
LeetCode expects the function to return the completed list, not just display it.

**Q3. Why is Fizz Buzz time complexity O(n)?**  
The loop visits every number from 1 to n exactly once, doing a fixed amount of work for each number.

**Q4. Why is Fizz Buzz auxiliary space O(1)?**  
Excluding the output list, the solution uses only a fixed amount of extra working memory.

**Q5. Why is Fizz Buzz output space O(n)?**  
The result list stores one string for every input number.

**Q6. What is the complexity of one loop that visits every number?**  
Time: O(n). Auxiliary space: O(1), assuming no input-sized extra structure is created.

**Q7. What is the space complexity of a list containing n doubled numbers?**  
O(n), because the list grows with the input size.

**Q8. Why is an n × n matrix O(n²) space?**  
It stores n rows with n elements in each row, for n × n total elements.

## 7. Day 1 completion checklist

- [x] Reviewed conditions and loops.
- [x] Practiced the modulo operator.
- [x] Completed LeetCode — Fizz Buzz (Accepted).
- [x] Completed HackerRank — Solve Me First (Accepted).
- [x] Studied time complexity.
- [x] Studied space complexity.
- [x] Reviewed O(1), O(log n), O(n), and O(n²).
- [x] Reviewed auxiliary space versus output space.
- [x] Reviewed print() versus return.
- [x] Practiced interview-style questions and answers.

## 8. Reflection and next steps

**What went well:** Completed both assigned coding problems and understood the basic role of conditions, loops, modulo, and complexity analysis.

**Revision needed:** Continue practicing auxiliary space and identifying Big O patterns from short code snippets.

**Next step:** Move to Day 2 — number logic and conditionals, while briefly revising today's complexity concepts.

---

**Day 1 status: COMPLETED ✅**
