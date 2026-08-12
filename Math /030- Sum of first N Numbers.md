# Sum of First N Numbers

## Problem Statement

Given a positive integer `n`, find the sum of all numbers from `1` to `n`.

In other words:

```text
1 + 2 + 3 + ... + n
```

### Example

**Input**
```text
n = 5
```

**Output**
```text
15
```

Because:

```text
1 + 2 + 3 + 4 + 5 = 15
```

---

# Approach

Instead of using a loop or recursion, we use the mathematical formula for the sum of the first `n` natural numbers:

```text
n × (n + 1) / 2
```

The steps are:

1. Take the given value `n`.
2. Calculate `n + 1`.
3. Multiply `n` by `n + 1`.
4. Divide the result by `2`.
5. Return the calculated sum.

This allows us to calculate the answer directly without processing every number from `1` to `n`.

---

# Code

```java
public class Solution {
    public static long sumFirstN(long n) {
        return n * (n + 1) / 2;
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 5
```

The formula is:

```text
n × (n + 1) / 2
```

Substitute `n = 5`:

```text
5 × (5 + 1) / 2
```

First calculate:

```text
5 + 1 = 6
```

Then:

```text
5 × 6 = 30
```

Finally:

```text
30 / 2 = 15
```

Therefore:

```text
sumFirstN(5) = 15
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 5
```

### Step 1

Calculate:

```text
n + 1
= 5 + 1
= 6
```

### Step 2

Multiply:

```text
n × (n + 1)
= 5 × 6
= 30
```

### Step 3

Divide by `2`:

```text
30 / 2 = 15
```

### Final Result

```text
15
```

---

# Dry Run

| Step | Calculation | Result |
|-----:|-------------|-------:|
| 1 | `n + 1` | `6` |
| 2 | `n × (n + 1)` | `30` |
| 3 | `30 / 2` | `15` |

Final answer:

```text
15
```

---

# Another Example

Suppose:

```text
n = 10
```

Using the formula:

```text
10 × (10 + 1) / 2
```

```text
10 × 11 / 2
```

```text
110 / 2
```

```text
55
```

Therefore:

```text
1 + 2 + 3 + ... + 10 = 55
```

---

# Why This Solution Works

The sum of the first `n` natural numbers follows the mathematical formula:

```text
n × (n + 1) / 2
```

For example, for `n = 5`:

```text
1 + 2 + 3 + 4 + 5
```

Pairing the numbers:

```text
1 + 5 = 6
2 + 4 = 6
```

The middle value is `3`.

The formula provides the same result directly:

```text
5 × 6 / 2 = 15
```

Therefore, there is no need to iterate through all the numbers.

---

# Why `long` Is Used

The method uses:

```java
long
```

instead of `int` because the value of:

```text
n × (n + 1)
```

can become large.

Using `long` provides a larger range for storing the result and helps avoid integer overflow for larger valid inputs.

---

# Time Complexity

The solution performs only a fixed number of arithmetic operations regardless of the value of `n`.

Therefore:

**Time Complexity: O(1)**

---

# Space Complexity

Only the input and a few arithmetic values are used.

No additional data structure or recursion stack is required.

Therefore:

**Space Complexity: O(1)**

---

# Key Takeaways

- The sum from `1` to `n` can be calculated using `n × (n + 1) / 2`.
- No loop is required.
- No recursion is required.
- The formula gives the answer directly.
- The solution takes constant time.
- `long` is used to safely handle larger values.

---

## 🔗 Problem Source

**Platform:** Naukri Code360

**Problem:** [Sum of First N Numbers](https://www.naukri.com/code360/problems/sum-of-first-n-numbers_8876068)
