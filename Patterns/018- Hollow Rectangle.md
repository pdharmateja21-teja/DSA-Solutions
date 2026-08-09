# Hollow Rectangle Pattern

## Problem Statement

Given two integers `n` and `m`, print a hollow rectangle pattern using `*`.

- `n` represents the number of rows.
- `m` represents the number of columns.
- The boundary of the rectangle should contain `*`.
- The inner portion of the rectangle should contain spaces.

### Example

**Input**
```text
n = 4
m = 6
```

**Output**
```text
******
*    *
*    *
******
```

---

# Approach

For every position in the rectangle, check whether it belongs to the boundary.

A position is on the boundary if:

- It is in the first row.
- It is in the last row.
- It is in the first column.
- It is in the last column.

If any of these conditions is true, print `*`.

Otherwise, print a space.

The outer loop controls the rows, while the inner loop controls the columns.

---

# Code

```java
import java.util.Scanner;

class GFG {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int m = sc.nextInt();

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= m; j++) {
                if (i == 1 || i == n || j == 1 || j == m) {
                    System.out.print("*");
                } else {
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }
}
```

---

# Understanding the Code

Suppose the input is:

```text
n = 4
m = 6
```

This means we need:

```text
4 rows
6 columns
```

The outer loop runs from `1` to `n`, so it creates the rows.

The inner loop runs from `1` to `m`, so it creates the columns.

For every position `(i, j)`, the condition checks:

```text
i == 1
i == n
j == 1
j == m
```

These four conditions represent the four boundaries of the rectangle.

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 4
m = 6
```

### Initial State

```text
Rows = 4
Columns = 6
```

---

### Iteration 1

```text
i = 1
```

Since:

```text
i == 1
```

is true, every column belongs to the first row.

Therefore, every position prints `*`.

```text
******
```

---

### Iteration 2

```text
i = 2
```

Now we are inside the rectangle.

#### Column 1

```text
j = 1
```

Since:

```text
j == 1
```

is true, print `*`.

#### Columns 2 to 5

These positions are inside the rectangle.

The boundary condition is false, so spaces are printed.

#### Column 6

```text
j = 6
```

Since:

```text
j == m
```

is true, print `*`.

The complete row becomes:

```text
*    *
```

---

### Iteration 3

```text
i = 3
```

This is another inner row.

```text
j = 1  → *
j = 2  → space
j = 3  → space
j = 4  → space
j = 5  → space
j = 6  → *
```

The row becomes:

```text
*    *
```

---

### Iteration 4

```text
i = 4
```

Since:

```text
i == n
```

is true, this is the last row.

Every column prints `*`.

```text
******
```

The outer loop finishes.

---

# Dry Run

For:

```text
n = 4
m = 6
```

| Row `i` | Column `j` | Boundary Condition | Output |
|--------:|-----------:|--------------------|:------:|
| 1 | 1 to 6 | `i == 1` | `*` |
| 2 | 1 | `j == 1` | `*` |
| 2 | 2 to 5 | False | Space |
| 2 | 6 | `j == m` | `*` |
| 3 | 1 | `j == 1` | `*` |
| 3 | 2 to 5 | False | Space |
| 3 | 6 | `j == m` | `*` |
| 4 | 1 to 6 | `i == n` | `*` |

Final output:

```text
******
*    *
*    *
******
```

---

# Why This Solution Works

A rectangle has four boundaries:

```text
Top
Bottom
Left
Right
```

The condition:

```text
i == 1 || i == n || j == 1 || j == m
```

checks all four boundaries.

- `i == 1` identifies the top row.
- `i == n` identifies the bottom row.
- `j == 1` identifies the left column.
- `j == m` identifies the right column.

Whenever the current position belongs to one of these boundaries, `*` is printed.

All other positions are inside the rectangle, so a space is printed.

This produces the required hollow rectangle.

---

# Time Complexity

The outer loop runs `n` times.

For every row, the inner loop runs `m` times.

Therefore, the total number of iterations is:

```text
n × m
```

**Time Complexity: O(n × m)**

---

# Space Complexity

Only the loop variables and input variables are used.

No additional data structure is created.

**Space Complexity: O(1)**

---

# Key Takeaways

- The outer loop controls the rows.
- The inner loop controls the columns.
- Boundary conditions determine where `*` should be printed.
- The first and last rows are completely filled with `*`.
- The first and last columns contain `*` for the inner rows.
- All remaining positions contain spaces.
- This boundary-checking technique is commonly used for hollow pattern problems.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Hollow Rectangle Pattern](https://www.geeksforgeeks.org/problems/print-the-pattern-set-1/1)
