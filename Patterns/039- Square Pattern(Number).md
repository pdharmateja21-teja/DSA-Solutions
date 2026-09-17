# Square Pattern

## Problem Statement

Given an integer `N`, print a square pattern of size `N × N` where every position contains the value `N`.

For example, if `N = 4`, the output should be:

```text
4444
4444
4444
4444
```

---

# Approach

The pattern contains exactly `N` rows and `N` columns.

We use two nested loops:

* The outer loop runs `N` times to create `N` rows.
* The inner loop runs `N` times to print `N` in each row.
* After completing each row, `System.out.println()` moves the cursor to the next line.

The important observation is that both the number of rows and the number of elements in each row are equal to `N`.

---

# Code

```java
import java.util.*;

public class Solution {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        for (int k = 0; k < n; k++) {
            for (int j = 0; j < n; j++) {
                System.out.print(n);
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

The value of `N` is taken from the user.

For example:

```text
N = 4
```

### 2. Outer loop

```text
for (int k = 0; k < n; k++)
```

This loop controls the number of rows.

Since `k` goes from `0` to `n - 1`, it executes exactly `N` times.

For `N = 4`:

```text
k = 0
k = 1
k = 2
k = 3
```

Therefore, 4 rows are created.

### 3. Inner loop

```text
for (int j = 0; j < n; j++)
```

This loop controls how many times `N` is printed in each row.

For `N = 4`, it prints:

```text
4 4 4 4
```

without spaces because `System.out.print(n)` is used.

### 4. Move to the next row

```text
System.out.println();
```

After printing `N` exactly `N` times, this moves the cursor to the next line.

---

# Code Flow (Step-by-Step Execution)

Consider:

```text
N = 4
```

### Row 1

Outer loop:

```text
k = 0
```

Inner loop prints `4` four times:

```text
4444
```

Then `println()` moves to the next line.

### Row 2

```text
k = 1
```

Again, the inner loop prints:

```text
4444
```

### Row 3

```text
k = 2
```

Output:

```text
4444
```

### Row 4

```text
k = 3
```

Output:

```text
4444
```

Final output:

```text
4444
4444
4444
4444
```

---

# Dry Run

For `N = 3`:

| Outer Loop `k` | Inner Loop Executions | Current Row |
| -------------- | --------------------: | ----------- |
| 0              |                     3 | `333`       |
| 1              |                     3 | `333`       |
| 2              |                     3 | `333`       |

Final output:

```text
333
333
333
```

---

# Why This Solution Works

A square of size `N × N` requires:

* `N` rows
* `N` values in every row

The outer loop produces the `N` rows, while the inner loop prints `N` for each position in a row.

Therefore, the resulting pattern always contains exactly `N × N` occurrences of the number `N`.

---

# Time Complexity

The outer loop executes `N` times and for every outer-loop iteration, the inner loop also executes `N` times.

Therefore:

**Time Complexity: O(N²)**

---

# Space Complexity

The solution uses only a few variables and does not use any additional data structure.

**Space Complexity: O(1)**

---

# Key Takeaways

* Use nested loops for a square pattern.
* The outer loop controls the number of rows.
* The inner loop controls the number of elements in each row.
* Both loops execute `N` times.
* Each position contains the input value `N`.
* The overall time complexity is **O(N²)**.

---

## 🔗 Problem Source

**Platform:** Code360

**Problem:** [Square Pattern](https://www.naukri.com/code360/problems/square-pattern_626545?leftPanelTabValue=PROBLEM)

