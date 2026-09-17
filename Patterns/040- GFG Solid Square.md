# Print Solid Square

## Problem Statement

Given an integer `N`, print a solid square pattern of size `N × N` using stars.

For example, if:

```text
N = 4
```

the output should be:

```text
* * * *
* * * *
* * * *
* * * *
```

---

# Approach

The pattern is a square, so it contains:

* `N` rows
* `N` stars in every row

We use two nested loops:

* The **outer loop** controls the rows.
* The **inner loop** prints `N` stars in each row.
* After printing all stars in one row, `System.out.println()` moves to the next row.

Since both loops run `N` times, the pattern contains `N × N` stars.

---

# Code

```java
import java.util.Scanner;

class GFG {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

---

# Understanding the Code

### 1. Read the input

```text
int n = sc.nextInt();
```

The value of `N` is read from the input.

For example:

```text
N = 4
```

---

### 2. Outer Loop

```text
for (int i = 0; i < n; i++)
```

The outer loop determines how many rows the square will have.

For `N = 4`:

```text
i = 0
i = 1
i = 2
i = 3
```

So, the loop creates exactly **4 rows**.

---

### 3. Inner Loop

```text
for (int j = 0; j < n; j++)
```

The inner loop determines how many stars are printed in each row.

For `N = 4`:

```text
j = 0 → *
j = 1 → *
j = 2 → *
j = 3 → *
```

Therefore, every row contains exactly **4 stars**.

---

### 4. Move to the Next Row

After the inner loop finishes:

```text
System.out.println();
```

moves the cursor to the next line.

This allows the next set of stars to be printed on a new row.

---

# Code Flow (Step-by-Step Execution)

Consider:

```text
N = 4
```

The execution can be visualized as a **4 × 4 square**.

### Row 1

Outer loop:

```text
i = 0
```

Inner loop runs four times:

```text
j = 0 → *
j = 1 → *
j = 2 → *
j = 3 → *
```

Row becomes:

```text
* * * *
```

Then `println()` moves to the next line.

---

### Row 2

```text
i = 1
```

Again, the inner loop prints four stars:

```text
* * * *
```

---

### Row 3

```text
i = 2
```

The inner loop again prints:

```text
* * * *
```

---

### Row 4

```text
i = 3
```

The inner loop prints:

```text
* * * *
```

---

### Final Output

```text
* * * *
* * * *
* * * *
* * * *
```

The important point is that **every row follows exactly the same pattern**: the inner loop prints `N` stars, and the outer loop repeats that row `N` times.

---

# Dry Run

For:

```text
N = 3
```

| Outer Loop `i` | Inner Loop `j` | Row Produced |
| -------------- | -------------- | ------------ |
| 0              | 0, 1, 2        | `* * *`      |
| 1              | 0, 1, 2        | `* * *`      |
| 2              | 0, 1, 2        | `* * *`      |

Final output:

```text
* * *
* * *
* * *
```

---

# Why This Solution Works

A solid square of size `N × N` requires exactly `N` rows, with `N` stars in every row.

The outer loop provides the `N` rows, while the inner loop provides the `N` stars in each row.

Therefore, the nested loops generate exactly the required square pattern.

---

# Time Complexity

The outer loop executes `N` times.

For every outer-loop iteration, the inner loop also executes `N` times.

Therefore, the total number of operations is approximately:

```text
N × N = N²
```

**Time Complexity: O(N²)**

---

# Space Complexity

The solution uses only the loop variables and the input variable. No additional data structure is used.

**Space Complexity: O(1)**

---

# Key Takeaways

* Nested loops are used to generate the square.
* The outer loop controls the number of rows.
* The inner loop controls the number of stars in each row.
* Both loops run `N` times.
* Every row contains exactly `N` stars.
* The solution uses constant extra space.
* The overall time complexity is **O(N²)**.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Print Solid Square](https://www.geeksforgeeks.org/problems/print-square-wall-1605682270/1)

