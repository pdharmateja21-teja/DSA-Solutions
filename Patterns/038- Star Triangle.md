# Star Triangle

## Problem Statement

Given an integer `n`, print a star triangle pattern with `n` rows.

For each row:

- Print spaces before the stars to center the pattern.
- Print an odd number of stars.
- The number of stars increases by `2` for every next row.

### Example

**Input**
```text
n = 4
```

**Output**
```text
   *
  ***
 *****
*******
```

---

# Approach

The pattern contains `n` rows.

For every row `i`:

1. Print `n - i - 1` spaces.
2. Print `2 × i + 1` stars.
3. Move to the next line.

The number of spaces decreases by `1` in every row, while the number of stars increases by `2`.

For `n = 4`:

```text
Row 1 → 3 spaces + 1 star
Row 2 → 2 spaces + 3 stars
Row 3 → 1 space  + 5 stars
Row 4 → 0 spaces + 7 stars
```

---

# Code

```java
public class Solution {
    public static void nStarTriangle(int n) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                System.out.print(" ");
            }

            for (int j = 0; j < 2 * i + 1; j++) {
                System.out.print("*");
            }

            System.out.println();
        }
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 4
```

The outer loop:

```java
for (int i = 0; i < n; i++)
```

controls the rows.

So `i` takes these values:

```text
0
1
2
3
```

For every row, there are two inner loops:

```text
First loop  → prints spaces
Second loop → prints stars
```

The important formulas are:

```text
Spaces = n - i - 1
Stars  = 2 × i + 1
```

---

# Row 1

```text
i = 0
```

Spaces:

```text
n - i - 1
= 4 - 0 - 1
= 3
```

Stars:

```text
2 × i + 1
= 2 × 0 + 1
= 1
```

So the row becomes:

```text
   *
```

---

# Row 2

```text
i = 1
```

Spaces:

```text
4 - 1 - 1 = 2
```

Stars:

```text
2 × 1 + 1 = 3
```

So the row becomes:

```text
  ***
```

---

# Row 3

```text
i = 2
```

Spaces:

```text
4 - 2 - 1 = 1
```

Stars:

```text
2 × 2 + 1 = 5
```

So the row becomes:

```text
 *****
```

---

# Row 4

```text
i = 3
```

Spaces:

```text
4 - 3 - 1 = 0
```

Stars:

```text
2 × 3 + 1 = 7
```

So the row becomes:

```text
*******
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 4
```

---

### Iteration 1

```text
i = 0

Spaces = 3
Stars = 1
```

Output:

```text
   *
```

---

### Iteration 2

```text
i = 1

Spaces = 2
Stars = 3
```

Output:

```text
  ***
```

---

### Iteration 3

```text
i = 2

Spaces = 1
Stars = 5
```

Output:

```text
 *****
```

---

### Iteration 4

```text
i = 3

Spaces = 0
Stars = 7
```

Output:

```text
*******
```

Final pattern:

```text
   *
  ***
 *****
*******
```

---

# Dry Run

| Row | `i` | Spaces | Stars | Pattern |
|----:|----:|-------:|------:|---------|
| 1 | 0 | 3 | 1 | `   *` |
| 2 | 1 | 2 | 3 | `  ***` |
| 3 | 2 | 1 | 5 | ` *****` |
| 4 | 3 | 0 | 7 | `*******` |

---

# Understanding the Pattern Formula

The number of stars follows:

```text
1, 3, 5, 7, ...
```

This is why the formula is:

```text
2 × i + 1
```

For each value of `i`:

```text
i = 0 → 1 star
i = 1 → 3 stars
i = 2 → 5 stars
i = 3 → 7 stars
```

The number of spaces follows:

```text
3, 2, 1, 0
```

This is why the formula is:

```text
n - i - 1
```

As the row number increases, the spaces decrease and the stars increase.

---

# Why This Solution Works

The pattern needs to be centered.

For every row:

- The number of leading spaces decreases by `1`.
- The number of stars increases by `2`.

For `n = 4`:

```text
   *
  ***
 *****
*******
```

The first row has the maximum number of spaces and the minimum number of stars.

The final row has no leading spaces and the maximum number of stars.

Therefore, the pattern forms a centered triangle.

---

# Time Complexity

The solution prints every character that appears in the pattern.

For `n` rows, the total number of printed characters is proportional to `n²`.

Therefore:

**Time Complexity: O(n²)**

---

# Space Complexity

The solution does not create any additional array or data structure.

Only loop variables are used.

Therefore:

**Space Complexity: O(1)**

---

# Key Takeaways

- The outer loop controls the number of rows.
- The first inner loop prints leading spaces.
- The second inner loop prints stars.
- Spaces are calculated using `n - i - 1`.
- Stars are calculated using `2 × i + 1`.
- Spaces decrease by `1` for every row.
- Stars increase by `2` for every row.
- Time Complexity is `O(n²)`.
- Space Complexity is `O(1)`.

---

## 🔗 Problem Source

**Platform:** Code360

**Problem:** [Star Triangle](https://www.naukri.com/code360/problems/star-triangle_6573671?leftPanelTabValue=SUBMISSION)
