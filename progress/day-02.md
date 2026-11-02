# Day 02 — Number logic, reversing numbers and array sum

**Date:** November 2, 2026  
**Status:** COMPLETED

**LeetCode:** [Palindrome Number](https://leetcode.com/problems/palindrome-number/) — Easy — **Accepted**  
**HackerRank:** [Simple Array Sum](https://www.hackerrank.com/challenges/simple-array-sum/problem) — **Accepted**

## 1. Important Python concepts

| Syntax | Purpose |
|---|---|
| `number % 10` | Extract the last digit |
| `number // 10` | Remove the last digit |
| `while number > 0` | Repeat while digits remain |
| `reverse * 10 + digit` | Build the reversed number |
| `original == reverse` | Compare the original and reversed numbers |
| `total = total + number` | Update a running sum |
| `return total` | Return the final sum |

## 2. LeetCode — Palindrome Number

**Problem:** Check whether a number reads the same forward and backward.

Examples:
- `121` → `True`
- `123` → `False`
- `1331` → `True`
- `-121` → `False`
- `0` → `True`

### Logic building

1. Check whether the number is negative. If it is, return `False`.
2. Save the original number.
3. Initialize `reverse = 0`.
4. Start a `while` loop while `number > 0`.
5. Extract the last digit using `% 10`.
6. Build the reversed number using `reverse * 10 + digit`.
7. Remove the last digit using `// 10`.
8. Compare the original and reversed numbers.

**Important:** Use a separate variable for the changing number so the original value is preserved.

### Complexity

- **Time:** `O(log n)`, because one digit is removed in every iteration.
- **Auxiliary space:** `O(1)`, because only a fixed number of variables are used.

**Result:** LeetCode Accepted.

## 3. HackerRank — Simple Array Sum

**Problem:** Calculate the sum of all elements in an array.

Example: `[1, 2, 3, 4, 5]` → `15`

### Logic building

1. Initialize `total = 0`.
2. Use a `for` loop to visit every element.
3. Add the current number to the total.
4. Return the total after the loop finishes.

Important pattern:

```python
total = 0

for number in arr:
    total = total + number

return total
```

This is called the **Accumulator Pattern**.

### Complexity

- **Time:** `O(n)`, because every array element is visited once.
- **Auxiliary space:** `O(1)`, because only a fixed amount of additional memory is used.

**Result:** HackerRank Accepted.

## 4. Important mistakes corrected

- Use `False` with a capital F in Python.
- Use `number > 0` for the changing number in the reversal loop.
- Preserve the original number before reversing.
- Place `return` outside the loop when the entire loop must finish.
- `return` immediately ends the function.
- A function without an explicit return statement returns `None`.
- One growing result list requires `O(n)` output space.
- Updating one accumulator variable requires `O(1)` auxiliary space.

## 5. Technical interview questions and answers

**Q1. What happens to total during array traversal?**  
The updated total is carried into the next iteration and added to the next element.

**Q2. What happens when return is inside a for loop?**  
The function immediately terminates after the first executed return.

**Q3. What happens with `[0, 5, 7]` when return is inside the loop?**  
The function returns `0` during the first iteration.

**Q4. What is the difference between print() and return?**  
Print displays a value; return sends a value back to the function caller.

**Q5. What happens to code written after return?**  
It will not execute when that return statement is reached.

**Q6. What happens when a function prints 10 and then returns 20?**  
The screen displays 10, and the returned value is 20.

**Q7. Why is Simple Array Sum O(n) time and O(1) auxiliary space?**  
The loop visits every element once, but only a fixed number of extra variables are used.

**Q8. What is the space complexity of a new list containing n doubled numbers?**  
O(n), because the new list stores n elements.

**Q9. What if we double every number but update only a total variable?**  
Time is O(n), auxiliary space is O(1), because no growing list is created.

**Q10. Why is zero a palindrome?**  
Zero has one digit. The while loop does not execute, but the original and reversed values are both zero, so the comparison returns True.

## 6. Day 2 completion checklist

- [x] Understand modulo and integer division.
- [x] Learn to extract digits.
- [x] Reverse a number using a while loop.
- [x] Understand palindrome comparison.
- [x] Learn the accumulator pattern.
- [x] Understand print() versus return.
- [x] Practise time and space complexity.
- [x] Complete LeetCode Palindrome Number.
- [x] Complete HackerRank Simple Array Sum.
- [x] Complete technical mock interview practice.

## 7. Key insight / final approach

For Palindrome Number, preserve the original value, reverse the digits one at a time using modulo and integer division, then compare the reversed value with the original. For Simple Array Sum, use an accumulator: start at zero, add each array element once, and return the total after the loop.

## 8. What I learned today

I learned how to extract and reverse digits using `% 10` and `// 10`, how to handle negative numbers and zero in a palindrome check, and how the accumulator pattern builds a running sum. I also reinforced that `return` ends a function immediately and that space complexity depends on whether the solution creates a growing output list or uses only a fixed number of variables.

## 9. Revision needed

- Auxiliary space and output space.
- The effect of placing `return` inside a loop.
- Tracing each step of number reversal.
