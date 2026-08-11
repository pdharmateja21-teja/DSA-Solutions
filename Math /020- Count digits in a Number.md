# Count Total Digits in a Number

## Problem Statement

Given an integer `n`, count the total number of digits present in the number.

### Example

**Input**
```text
n = 12345
```

**Output**
```text
5
```

---

# Approach

We can count the digits by repeatedly removing the last digit of the number.

For every iteration:

1. Increase `count` by `1`.
2. Divide `n` by `10`.
3. This removes the last digit.
4. Continue until `n` becomes `0`.

For example:

```text
12345 → 1234 → 123 → 12 → 1 → 0
```

There are `5` iterations, so the number contains `5` digits.

---

# Code

```java
class Solution {
    public static int countDigits(int n) {
        int count = 0;

        while (n > 0) {
            count++;
            n /= 10;
        }

        return count;
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 12345
```

Initially:

```text
count = 0
n = 12345
```

The `while` loop continues as long as:

```text
n > 0
```

During every iteration, `n /= 10` removes the last digit.

---

## Iteration 1

```text
n = 12345
count = 0
```

Increase the count:

```text
count = 1
```

Remove the last digit:

```text
12345 / 10 = 1234
```

Current state:

```text
n = 1234
count = 1
```

---

## Iteration 2

```text
n = 1234
count = 1
```

Increase the count:

```text
count = 2
```

Remove the last digit:

```text
1234 / 10 = 123
```

Current state:

```text
n = 123
count = 2
```

---

## Iteration 3

```text
n = 123
count = 2
```

Increase the count:

```text
count = 3
```

Remove the last digit:

```text
123 / 10 = 12
```

Current state:

```text
n = 12
count = 3
```

---

## Iteration 4

```text
n = 12
count = 3
```

Increase the count:

```text
count = 4
```

Remove the last digit:

```text
12 / 10 = 1
```

Current state:

```text
n = 1
count = 4
```

---

## Iteration 5

```text
n = 1
count = 4
```

Increase the count:

```text
count = 5
```

Remove the last digit:

```text
1 / 10 = 0
```

Current state:

```text
n = 0
count = 5
```

Now the condition:

```text
n > 0
```

is false.

The loop stops and returns:

```text
5
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 12345
```

### Initial State

```text
count = 0
n = 12345
```

### Flow

```text
12345 → count = 1 → n = 1234
1234  → count = 2 → n = 123
123   → count = 3 → n = 12
12    → count = 4 → n = 1
1     → count = 5 → n = 0
```

Now:

```text
n = 0
```

The loop ends.

Return:

```text
5
```

---

# Dry Run

| Iteration | Current `n` | `count` Before | `count` After | `n` After `n /= 10` |
|----------:|------------:|---------------:|--------------:|---------------------:|
| 1 | 12345 | 0 | 1 | 1234 |
| 2 | 1234 | 1 | 2 | 123 |
| 3 | 123 | 2 | 3 | 12 |
| 4 | 12 | 3 | 4 | 1 |
| 5 | 1 | 4 | 5 | 0 |

Final result:

```text
5
```

---

# Why This Solution Works

Every integer division by `10` removes exactly one digit from the end of a positive number.

For example:

```text
12345 → 1234
1234  → 123
123   → 12
12    → 1
1     → 0
```

The number of times this operation is performed before reaching `0` is exactly the number of digits in the original number.

Therefore, increasing `count` once during every iteration gives the correct number of digits.

---

# Time Complexity

For a number containing `d` digits, the loop runs exactly `d` times.

Therefore:

**Time Complexity: O(log₁₀ n)**

---

# Space Complexity

Only the variables `count` and `n` are used.

No additional data structure is created.

**Space Complexity: O(1)**

---

# Key Takeaways

- `n /= 10` removes the last digit of the number.
- The loop executes once for every digit.
- `count` keeps track of how many digits have been removed.
- When `n` becomes `0`, all digits have been processed.
- The final value of `count` is the total number of digits.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Count Total Digits in a Number](https://www.geeksforgeeks.org/problems/count-total-digits-in-a-number/1)
