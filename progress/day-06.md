# Day 06 — 2D arrays and matrix traversal

**Date:** November 6, 2026  
**Language:** Python  
**Status:** COMPLETED ✅

## 1. Concepts learned

- A 2D array (matrix) stores values in rows and columns.
- Access an element with matrix[row][column]; Python indexes start at 0.
- len(matrix) gives the number of rows.
- len(matrix[0]) gives the number of columns for a non-empty rectangular matrix.
- Nested loops traverse rows and the elements within each row.
- Total elements in an R × C matrix = R × C.
- Primary diagonal positions use matrix[i][i].
- Secondary diagonal positions use matrix[i][n - 1 - i] in an n × n square matrix.
- In an odd-sized square matrix, the centre belongs to both diagonals and must be counted only once.
- Matrix transpose swaps row and column positions: matrix[r][c] becomes transposed[c][r].
- Column-wise traversal uses the column as the outer loop and the row as the inner loop.

## 2. Important logic

### Matrix Diagonal Sum — LeetCode Q1

~~~python
n = len(mat)
total = 0

for i in range(n):
    total += mat[i][i]
    total += mat[i][n - 1 - i]

if n % 2 == 1:
    total -= mat[n // 2][n // 2]

return total
~~~

The loop adds both diagonals. If n is odd, subtract the centre once because it was added twice.

### Transpose Matrix — LeetCode Q2

~~~python
rows = len(matrix)
columns = len(matrix[0])
transposed = []

for c in range(columns):
    new_row = []
    for r in range(rows):
        new_row.append(matrix[r][c])
    transposed.append(new_row)

return transposed
~~~

Each original column becomes one row in the transposed matrix. An R × C matrix becomes C × R.

### 2D Array - DS (Hourglass Sum) — HackerRank Q1

An hourglass has this shape:

~~~text
a b c
  d
e f g
~~~

For a starting position (i, j), add:

- arr[i][j], arr[i][j+1], arr[i][j+2]
- arr[i+1][j+1]
- arr[i+2][j], arr[i+2][j+1], arr[i+2][j+2]

For a 6 × 6 matrix, valid starting indexes are i = 0..3 and j = 0..3, giving 16 hourglasses. Track the maximum sum. Initialize the maximum to negative infinity because matrix values can be negative.

### Matrix Script — HackerRank Q2

~~~python
decoded = []

for column in range(m):
    for row in range(n):
        decoded.append(matrix[row][column])

decoded = ''.join(decoded)
result = re.sub(
    r'(?<=[A-Za-z0-9])[^A-Za-z0-9]+(?=[A-Za-z0-9])',
    ' ',
    decoded
)

print(result)
~~~

Read the matrix column by column, join the characters, then replace each sequence of non-alphanumeric characters between alphanumeric characters with one space. Preserve the matrix input exactly; do not strip meaningful spaces from its rows.

## 3. Coding problems completed

| Platform | Problem | Result |
|---|---|---|
| LeetCode Q1 | Matrix Diagonal Sum | Accepted ✅ |
| LeetCode Q2 | Transpose Matrix | Accepted ✅ |
| HackerRank Q1 | 2D Array - DS (Hourglass Sum) | Accepted ✅ |
| HackerRank Q2 | Matrix Script | Accepted ✅ |

## 4. Time and space complexity

| Problem | Time complexity | Space complexity |
|---|---|---|
| Matrix Diagonal Sum | O(n) | O(1) auxiliary |
| Transpose Matrix | O(R × C) | O(R × C) output; O(1) auxiliary |
| 2D Array - DS | O(1) for fixed 6 × 6; O(R × C) generalized | O(1) auxiliary |
| Matrix Script | O(R × C) | O(R × C) for collected characters/output |

Where R is the number of rows, C is the number of columns, and n is the side length of a square matrix.

## 5. Common mistakes and reminders

- The first index is the row; the second index is the column.
- The outer loop does not automatically mean rows: in column-wise traversal, the outer loop selects columns.
- For a square matrix, do not add the centre element twice in the diagonal sum.
- A transpose swaps indexes and changes the dimensions from R × C to C × R.
- For an hourglass, only the middle element of the middle row is included.
- Use negative infinity as the initial maximum for hourglass sums so all-negative inputs are handled.
- Preserve spaces in Matrix Script input rows; avoid strip() or rstrip() on matrix rows.

## 6. Day 6 completion checklist

- [x] Understand row and column indexes.
- [x] Understand nested loops and matrix dimensions.
- [x] Identify primary and secondary diagonals.
- [x] Understand the centre-cell rule.
- [x] Complete LeetCode Q1 — Matrix Diagonal Sum (Accepted).
- [x] Complete LeetCode Q2 — Transpose Matrix (Accepted).
- [x] Complete HackerRank Q1 — 2D Array - DS (Accepted).
- [x] Complete HackerRank Q2 — Matrix Script (Accepted).

## 7. Key learning

Practised reading and updating 2D arrays, traversing matrices row-wise and column-wise, calculating diagonal sums, transposing rectangular matrices, and scanning every valid hourglass position.

**Day 6 Completed! ✅**
