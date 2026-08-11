# Ninja and the Number Pattern I

## Problem Statement

Given an integer `n`, print a number pattern of size `(2n - 1) × (2n - 1)`.

The pattern is formed using concentric layers of numbers.

- The outermost layer contains `n`.
- The next inner layer contains `n - 1`.
- This continues until the center contains `1`.
- The pattern is symmetric horizontally and vertically.

### Example

**Input**
```text
n = 4
```

**Output**
```text
4444444
4333334
4322234
4321234
4322234
4333334
4444444
```

---

# Approach

The complete pattern has:

```text
2 × n - 1
```

rows and columns.

For every position `(i, j)`, determine its distance from the four boundaries:

- Distance from the top
- Distance from the bottom
- Distance from the left
- Distance from the right

The smallest of these four distances tells us which layer the current position belongs to.

We calculate:

```text
layer = minimum distance from any boundary
```

Then the number to print is:

```text
num = n - layer
```

This automatically creates all the concentric layers.

---

# Code

```java
public class Solution {
    public static void getNumberPattern(int n) {
        int size = 2 * n - 1;

        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                int top = i;
                int left = j;
                int bottom = size - 1 - i;
                int right = size - 1 - j;

                int layer = Math.min(
                    Math.min(top, bottom),
                    Math.min(left, right)
                );

                int num = n - layer;

                System.out.print(num);
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

First, calculate the size:

```text
size = 2 × 4 - 1
     = 7
```

So the pattern contains:

```text
7 rows
7 columns
```

The pattern has four layers:

```text
Layer 0 → 4
Layer 1 → 3
Layer 2 → 2
Layer 3 → 1
```

The outermost layer is `0`, so:

```text
num = 4 - 0 = 4
```

The next layer is `1`:

```text
num = 4 - 1 = 3
```

The next layer is `2`:

```text
num = 4 - 2 = 2
```

The center belongs to layer `3`:

```text
num = 4 - 3 = 1
```

Therefore, the numbers naturally form concentric layers.

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 4
```

### Step 1: Calculate Pattern Size

```text
size = 2 * n - 1

size = 2 * 4 - 1
size = 7
```

Therefore, both loops run from:

```text
0 to 6
```

---

### Step 2: First Position

Consider:

```text
i = 0
j = 0
```

Calculate the distances:

```text
top = 0
left = 0
bottom = 6
right = 6
```

The minimum distance is:

```text
layer = 0
```

Therefore:

```text
num = 4 - 0
num = 4
```

Print:

```text
4
```

Since this position is on the outer boundary, it belongs to the outermost layer.

---

### Step 3: Move Across the First Row

Consider:

```text
i = 0
j = 3
```

Distances:

```text
top = 0
left = 3
bottom = 6
right = 3
```

Minimum:

```text
layer = 0
```

Number:

```text
num = 4
```

So the first row contains only `4`.

```text
4444444
```

---

### Step 4: Move Into the Second Layer

Consider:

```text
i = 1
j = 1
```

Distances:

```text
top = 1
left = 1
bottom = 5
right = 5
```

Minimum:

```text
layer = 1
```

Number:

```text
num = 4 - 1
num = 3
```

So this position contains:

```text
3
```

---

### Step 5: Move Into the Third Layer

Consider:

```text
i = 2
j = 2
```

Distances:

```text
top = 2
left = 2
bottom = 4
right = 4
```

Minimum:

```text
layer = 2
```

Number:

```text
num = 4 - 2
num = 2
```

So this position contains:

```text
2
```

---

### Step 6: Reach the Center

The center of a `7 × 7` pattern is:

```text
i = 3
j = 3
```

Distances:

```text
top = 3
left = 3
bottom = 3
right = 3
```

Minimum:

```text
layer = 3
```

Number:

```text
num = 4 - 3
num = 1
```

Therefore, the center contains:

```text
1
```

---

# Complete Pattern Flow

For:

```text
n = 4
```

The layers are:

```text
Layer 0 → 4
Layer 1 → 3
Layer 2 → 2
Layer 3 → 1
```

The pattern becomes:

```text
4444444
4333334
4322234
4321234
4322234
4333334
4444444
```

The same layer calculation works for every position, which automatically creates the symmetric pattern.

---

# Dry Run

For:

```text
n = 4
size = 7
```

| Position `(i, j)` | Top | Bottom | Left | Right | Layer | Number |
|-------------------|----:|-------:|-----:|------:|------:|-------:|
| `(0, 0)` | 0 | 6 | 0 | 6 | 0 | 4 |
| `(0, 3)` | 0 | 6 | 3 | 3 | 0 | 4 |
| `(1, 1)` | 1 | 5 | 1 | 5 | 1 | 3 |
| `(2, 2)` | 2 | 4 | 2 | 4 | 2 | 2 |
| `(3, 3)` | 3 | 3 | 3 | 3 | 3 | 1 |
| `(4, 2)` | 4 | 2 | 2 | 4 | 2 | 2 |
| `(5, 1)` | 5 | 1 | 1 | 5 | 1 | 3 |
| `(6, 0)` | 6 | 0 | 0 | 6 | 0 | 4 |

This shows how the same layer logic works from the outside toward the center and back outward.

---

# Why This Solution Works

Every position belongs to one of the concentric layers.

The key idea is to find the **minimum distance from the four boundaries**.

For example:

```text
layer = min(top, bottom, left, right)
```

This tells us how deep the current position is inside the pattern.

Then:

```text
num = n - layer
```

converts the layer number into the required value.

For `n = 4`:

```text
Layer 0 → 4
Layer 1 → 3
Layer 2 → 2
Layer 3 → 1
```

Because the distance calculation is based on all four boundaries, the same value appears symmetrically on every side.

---

# Time Complexity

The pattern has:

```text
(2n - 1) × (2n - 1)
```

positions.

Every position is processed once.

Therefore:

```text
Time = O((2n - 1)²)
```

Ignoring constants:

**Time Complexity: O(n²)**

---

# Space Complexity

The solution uses only a fixed number of integer variables.

No additional array or data structure is used.

**Space Complexity: O(1)**

---

# Key Takeaways

- The pattern size is `2n - 1`.
- Every position belongs to a concentric layer.
- The minimum distance from the four boundaries identifies the layer.
- `num = n - layer` determines the number to print.
- This approach avoids writing separate conditions for every layer.
- The same logic works for any valid value of `n`.

---

## 🔗 Problem Source

**Platform:** Naukri Code360

**Problem:** [Ninja and the Number Pattern I](https://www.naukri.com/code360/problems/ninja-and-the-number-pattern-i_6581959?leftPanelTabValue=PROBLEM)
