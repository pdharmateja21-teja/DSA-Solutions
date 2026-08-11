# HCF and LCM

## Problem Statement

Given two integers `n` and `m`, find their **HCF (Highest Common Factor)**, also known as **GCD (Greatest Common Divisor)**.

The HCF is the largest positive integer that divides both numbers without leaving a remainder.

### Example

**Input**
```text
n = 12
m = 18
```

**Output**
```text
6
```

Because:

```text
Factors of 12 = 1, 2, 3, 4, 6, 12
Factors of 18 = 1, 2, 3, 6, 9, 18
```

The greatest common factor is:

```text
6
```

---

# Approach

This solution uses the **Euclidean Algorithm** to calculate the HCF efficiently.

The main idea is:

```text
GCD(n, m) = GCD(m, n % m)
```

We repeatedly replace the larger problem with the remainder until the second number becomes `0`.

The first number at that point is the HCF.

The steps are:

1. Store the current value of `n` temporarily.
2. Move `m` into `n`.
3. Replace `m` with `n % m` using the previous value of `n`.
4. Continue until `m` becomes `0`.
5. Return `n`.

---

# Code

```java
public class Solution {
    public static int calcGCD(int n, int m) {
        while (m != 0) {
            int temp = n;
            n = m;
            m = temp % m;
        }

        return n;
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 12
m = 18
```

Initially:

```text
n = 12
m = 18
```

The loop continues while:

```text
m != 0
```

During every iteration, the Euclidean Algorithm reduces the problem using the remainder.

---

## Iteration 1

Current values:

```text
n = 12
m = 18
```

Store `n`:

```text
temp = 12
```

Move `m` into `n`:

```text
n = 18
```

Calculate the remainder using the old `n`:

```text
m = 12 % 18
m = 12
```

Current state:

```text
n = 18
m = 12
```

---

## Iteration 2

Current values:

```text
n = 18
m = 12
```

Store `n`:

```text
temp = 18
```

Move `m` into `n`:

```text
n = 12
```

Calculate:

```text
m = 18 % 12
m = 6
```

Current state:

```text
n = 12
m = 6
```

---

## Iteration 3

Current values:

```text
n = 12
m = 6
```

Store `n`:

```text
temp = 12
```

Move `m` into `n`:

```text
n = 6
```

Calculate:

```text
m = 12 % 6
m = 0
```

Current state:

```text
n = 6
m = 0
```

Now:

```text
m != 0
```

is false.

The loop ends.

Return:

```text
6
```

Therefore:

```text
HCF = 6
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 12
m = 18
```

### Initial State

```text
n = 12
m = 18
```

### Flow

```text
n = 12, m = 18
        ↓
n = 18, m = 12
        ↓
n = 12, m = 6
        ↓
n = 6, m = 0
```

When `m` becomes `0`, the loop stops.

Return:

```text
6
```

---

# Dry Run

| Iteration | `n` Before | `m` Before | `temp` | `n` After | `m` After |
|----------:|-----------:|-----------:|-------:|----------:|----------:|
| 1 | 12 | 18 | 12 | 18 | 12 |
| 2 | 18 | 12 | 18 | 12 | 6 |
| 3 | 12 | 6 | 12 | 6 | 0 |

Final state:

```text
n = 6
m = 0
```

Return:

```text
6
```

---

# Why This Solution Works

The Euclidean Algorithm is based on the property:

```text
GCD(a, b) = GCD(b, a % b)
```

For:

```text
12 and 18
```

we calculate:

```text
18 % 12 = 6
12 % 6 = 0
```

When the remainder becomes `0`, the non-zero value is the HCF:

```text
6
```

The algorithm avoids checking every possible factor, making it much more efficient than a simple factor-search approach.

---

# Time Complexity

The Euclidean Algorithm reduces the values significantly in every iteration.

For two numbers `n` and `m`, the time complexity is:

**Time Complexity: O(log(min(n, m)))**

---

# Space Complexity

Only a few integer variables are used.

No additional data structure is created.

**Space Complexity: O(1)**

---

# Key Takeaways

- HCF and GCD refer to the same concept.
- The solution uses the Euclidean Algorithm.
- The key operation is `n % m`.
- `temp` preserves the old value of `n` before updating it.
- The loop continues until `m` becomes `0`.
- The remaining value of `n` is the HCF.
- The Euclidean Algorithm is efficient and commonly used for GCD problems.

---

## 🔗 Problem Source

**Platform:** Naukri Code360

**Problem:** [HCF and LCM](https://www.naukri.com/code360/problems/hcf-and-lcm_840448)
