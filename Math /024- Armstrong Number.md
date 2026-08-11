# Armstrong Number

## Problem Statement

Given an integer `n`, determine whether the number is an Armstrong number.

An Armstrong number is a number where the sum of the cubes of its digits is equal to the original number.

For example:

```text
153 = 1³ + 5³ + 3³
   = 1 + 125 + 27
   = 153
```

Therefore, `153` is an Armstrong number.

### Example

**Input**
```text
n = 153
```

**Output**
```text
true
```

---

# Approach

We can check whether a number is an Armstrong number by extracting each digit and adding its cube to `sum`.

The steps are:

1. Store the original number in `original`.
2. Extract the last digit using `n % 10`.
3. Calculate the cube of the digit.
4. Add the cube to `sum`.
5. Remove the last digit using `n / 10`.
6. Repeat until `n` becomes `0`.
7. Compare `sum` with the original number.
8. If both are equal, return `true`; otherwise, return `false`.

---

# Code

```java
class Solution {
    static boolean armstrongNumber(int n) {
        int sum = 0;
        int original = n;

        while (n > 0) {
            int digit = n % 10;
            sum = sum + digit * digit * digit;
            n = n / 10;
        }

        return sum == original;
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 153
```

First, store the original number:

```text
original = 153
```

This is necessary because `n` will be reduced to `0` during the process.

Initially:

```text
sum = 0
n = 153
```

The loop extracts each digit from right to left.

---

## Iteration 1

```text
n = 153
sum = 0
```

Extract the last digit:

```text
digit = 153 % 10
digit = 3
```

Calculate its cube:

```text
3 × 3 × 3 = 27
```

Add it to `sum`:

```text
sum = 0 + 27
sum = 27
```

Remove the last digit:

```text
n = 153 / 10
n = 15
```

Current state:

```text
original = 153
n = 15
sum = 27
```

---

## Iteration 2

```text
n = 15
sum = 27
```

Extract:

```text
digit = 15 % 10
digit = 5
```

Calculate the cube:

```text
5 × 5 × 5 = 125
```

Add it to `sum`:

```text
sum = 27 + 125
sum = 152
```

Remove the last digit:

```text
n = 15 / 10
n = 1
```

Current state:

```text
original = 153
n = 1
sum = 152
```

---

## Iteration 3

```text
n = 1
sum = 152
```

Extract:

```text
digit = 1 % 10
digit = 1
```

Calculate the cube:

```text
1 × 1 × 1 = 1
```

Add it to `sum`:

```text
sum = 152 + 1
sum = 153
```

Remove the last digit:

```text
n = 1 / 10
n = 0
```

Current state:

```text
original = 153
n = 0
sum = 153
```

Now:

```text
n > 0
```

is false, so the loop ends.

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 153
```

### Initial State

```text
original = 153
sum = 0
```

### Flow

```text
153 → digit = 3 → 3³ = 27  → sum = 27  → n = 15
15  → digit = 5 → 5³ = 125 → sum = 152 → n = 1
1   → digit = 1 → 1³ = 1   → sum = 153 → n = 0
```

After the loop:

```text
sum = 153
original = 153
```

Comparison:

```text
sum == original
153 == 153
```

Therefore, the method returns:

```text
true
```

---

# Dry Run

| Iteration | Current `n` | Digit | Digit Cube | `sum` Before | `sum` After | `n` After |
|----------:|------------:|------:|-----------:|-------------:|------------:|----------:|
| 1 | 153 | 3 | 27 | 0 | 27 | 15 |
| 2 | 15 | 5 | 125 | 27 | 152 | 1 |
| 3 | 1 | 1 | 1 | 152 | 153 | 0 |

Final comparison:

```text
sum = 153
original = 153
```

Result:

```text
true
```

---

# Another Example

Suppose:

```text
n = 123
```

Calculate the cubes:

```text
1³ + 2³ + 3³
```

```text
1 + 8 + 27 = 36
```

Compare:

```text
sum = 36
original = 123
```

Since:

```text
36 != 123
```

the method returns:

```text
false
```

Therefore, `123` is not an Armstrong number.

---

# Why This Solution Works

The solution processes every digit exactly once.

For each digit:

```text
digit = n % 10
```

extracts the last digit.

Then:

```text
digit * digit * digit
```

calculates its cube.

The cube is added to `sum`, and:

```text
n = n / 10
```

removes the processed digit.

After all digits are processed, `sum` contains the sum of the cubes of all digits.

If:

```text
sum == original
```

the number satisfies the Armstrong condition.

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

- Store the original number before modifying `n`.
- `n % 10` extracts the last digit.
- `digit * digit * digit` calculates the cube of the digit.
- `n / 10` removes the last digit.
- `sum` stores the total of all digit cubes.
- Finally, compare `sum` with `original`.
- If both are equal, the number is an Armstrong number.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Armstrong Numbers](https://www.geeksforgeeks.org/problems/armstrong-numbers2727/1)
