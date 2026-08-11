# Reverse Digits

## Problem Statement

Given an integer `n`, reverse the digits of the number and return the reversed number.

### Example

**Input**
```text
n = 12345
```

**Output**
```text
54321
```

---

# Approach

We can reverse the number by extracting its last digit one by one.

For every iteration:

1. Extract the last digit using `n % 10`.
2. Add that digit to the end of `reverse`.
3. Remove the last digit from `n` using `n /= 10`.
4. Continue until `n` becomes `0`.

The key operation is:

```text
reverse = reverse * 10 + digit
```

Multiplying `reverse` by `10` shifts its existing digits to the left, creating space for the new digit.

---

# Code

```java
class Solution {
    public int reverseDigits(int n) {
        int reverse = 0;

        while (n > 0) {
            int digit = n % 10;
            reverse = reverse * 10 + digit;
            n /= 10;
        }

        return reverse;
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
reverse = 0
n = 12345
```

The loop continues while:

```text
n > 0
```

In every iteration, we extract the last digit and add it to `reverse`.

---

## Iteration 1

```text
n = 12345
reverse = 0
```

Extract the last digit:

```text
digit = 12345 % 10
digit = 5
```

Update `reverse`:

```text
reverse = 0 * 10 + 5
reverse = 5
```

Remove the last digit:

```text
n = 12345 / 10
n = 1234
```

Current state:

```text
n = 1234
reverse = 5
```

---

## Iteration 2

```text
n = 1234
reverse = 5
```

Extract:

```text
digit = 1234 % 10
digit = 4
```

Update:

```text
reverse = 5 * 10 + 4
reverse = 54
```

Remove the last digit:

```text
n = 1234 / 10
n = 123
```

Current state:

```text
n = 123
reverse = 54
```

---

## Iteration 3

```text
n = 123
reverse = 54
```

Extract:

```text
digit = 123 % 10
digit = 3
```

Update:

```text
reverse = 54 * 10 + 3
reverse = 543
```

Remove the last digit:

```text
n = 123 / 10
n = 12
```

Current state:

```text
n = 12
reverse = 543
```

---

## Iteration 4

```text
n = 12
reverse = 543
```

Extract:

```text
digit = 12 % 10
digit = 2
```

Update:

```text
reverse = 543 * 10 + 2
reverse = 5432
```

Remove the last digit:

```text
n = 12 / 10
n = 1
```

Current state:

```text
n = 1
reverse = 5432
```

---

## Iteration 5

```text
n = 1
reverse = 5432
```

Extract:

```text
digit = 1 % 10
digit = 1
```

Update:

```text
reverse = 5432 * 10 + 1
reverse = 54321
```

Remove the last digit:

```text
n = 1 / 10
n = 0
```

Now the loop condition:

```text
n > 0
```

is false.

The loop ends and returns:

```text
54321
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 12345
```

### Initial State

```text
n = 12345
reverse = 0
```

### Flow

```text
12345 → digit = 5 → reverse = 5     → n = 1234
1234  → digit = 4 → reverse = 54    → n = 123
123   → digit = 3 → reverse = 543   → n = 12
12    → digit = 2 → reverse = 5432  → n = 1
1     → digit = 1 → reverse = 54321 → n = 0
```

Now:

```text
n = 0
```

The loop ends.

Return:

```text
54321
```

---

# Dry Run

| Iteration | Current `n` | `digit = n % 10` | `reverse` Before | `reverse` After | `n` After `n /= 10` |
|----------:|------------:|------------------:|-----------------:|----------------:|---------------------:|
| 1 | 12345 | 5 | 0 | 5 | 1234 |
| 2 | 1234 | 4 | 5 | 54 | 123 |
| 3 | 123 | 3 | 54 | 543 | 12 |
| 4 | 12 | 2 | 543 | 5432 | 1 |
| 5 | 1 | 1 | 5432 | 54321 | 0 |

Final result:

```text
54321
```

---

# Why This Solution Works

The last digit of a number can be obtained using:

```text
n % 10
```

For example:

```text
12345 % 10 = 5
```

After extracting the digit, integer division by `10` removes it:

```text
12345 / 10 = 1234
```

To build the reversed number, we use:

```text
reverse = reverse * 10 + digit
```

For example:

```text
reverse = 54
digit = 3

reverse = 54 * 10 + 3
        = 543
```

Therefore, each extracted digit is placed at the correct position in the reversed number.

---

# Time Complexity

For a number containing `d` digits, the loop runs exactly `d` times.

Therefore:

**Time Complexity: O(log₁₀ n)**

---

# Space Complexity

Only a few integer variables are used.

No additional data structure is created.

**Space Complexity: O(1)**

---

# Key Takeaways

- `n % 10` extracts the last digit.
- `n /= 10` removes the last digit.
- `reverse * 10` shifts the existing digits one position to the left.
- Adding the extracted digit builds the reversed number.
- The process continues until all digits of the original number are processed.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Reverse Digits](https://www.geeksforgeeks.org/problems/reverse-digit0316/1)
