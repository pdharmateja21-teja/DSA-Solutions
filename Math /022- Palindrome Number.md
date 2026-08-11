# Palindrome Number

## Problem Statement

Given an integer `n`, determine whether the number is a palindrome.

A palindrome number remains the same when its digits are reversed.

### Example

**Input**
```text
n = 121
```

**Output**
```text
true
```

For example:

```text
121 → 121
```

Since the reversed number is the same as the original number, `121` is a palindrome.

---

# Approach

We can check whether a number is a palindrome by reversing its digits and comparing the reversed number with the original number.

The steps are:

1. Store the original number in a separate variable.
2. Reverse the number using `% 10` and `/= 10`.
3. Compare the reversed number with the original number.
4. If both are equal, return `true`.
5. Otherwise, return `false`.

The original number must be stored because the variable `n` changes while reversing it.

---

# Code

```java
public class Solution {
    public static boolean palindromeNumber(int n) {
        int original = n;
        int reverse = 0;

        while (n > 0) {
            int digit = n % 10;
            reverse = reverse * 10 + digit;
            n /= 10;
        }

        return reverse == original;
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 121
```

First, store the original number:

```text
original = 121
```

Then:

```text
reverse = 0
```

The number is reversed using the same digit extraction technique.

---

## Iteration 1

```text
n = 121
reverse = 0
```

Extract the last digit:

```text
digit = 121 % 10
digit = 1
```

Build the reversed number:

```text
reverse = 0 * 10 + 1
reverse = 1
```

Remove the last digit:

```text
n = 121 / 10
n = 12
```

Current state:

```text
original = 121
n = 12
reverse = 1
```

---

## Iteration 2

```text
n = 12
reverse = 1
```

Extract:

```text
digit = 12 % 10
digit = 2
```

Build:

```text
reverse = 1 * 10 + 2
reverse = 12
```

Remove the last digit:

```text
n = 12 / 10
n = 1
```

Current state:

```text
original = 121
n = 1
reverse = 12
```

---

## Iteration 3

```text
n = 1
reverse = 12
```

Extract:

```text
digit = 1 % 10
digit = 1
```

Build:

```text
reverse = 12 * 10 + 1
reverse = 121
```

Remove the last digit:

```text
n = 1 / 10
n = 0
```

The loop ends.

Now:

```text
original = 121
reverse = 121
```

Comparison:

```text
reverse == original
121 == 121
```

The condition is true.

Therefore, the method returns:

```text
true
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 121
```

### Initial State

```text
original = 121
reverse = 0
```

### Flow

```text
121 → digit = 1 → reverse = 1   → n = 12
12  → digit = 2 → reverse = 12  → n = 1
1   → digit = 1 → reverse = 121 → n = 0
```

After the loop:

```text
original = 121
reverse = 121
```

Comparison:

```text
121 == 121
```

Result:

```text
true
```

---

# Dry Run

| Iteration | Current `n` | Extracted `digit` | `reverse` Before | `reverse` After | `n` After |
|----------:|------------:|------------------:|-----------------:|----------------:|----------:|
| 1 | 121 | 1 | 0 | 1 | 12 |
| 2 | 12 | 2 | 1 | 12 | 1 |
| 3 | 1 | 1 | 12 | 121 | 0 |

Final comparison:

```text
reverse = 121
original = 121
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

The number is reversed:

```text
123 → 321
```

Now compare:

```text
original = 123
reverse = 321
```

Since:

```text
123 != 321
```

the method returns:

```text
false
```

Therefore, `123` is not a palindrome.

---

# Why This Solution Works

A palindrome number is exactly the same when read from left to right or right to left.

Reversing the number gives us the right-to-left version.

Therefore, we only need to compare:

```text
Original Number
```

with:

```text
Reversed Number
```

If they are equal, the number is a palindrome.

The variable `original` preserves the initial value because `n` is reduced to `0` during the reversal process.

---

# Time Complexity

For a number containing `d` digits, the loop processes each digit exactly once.

Therefore:

**Time Complexity: O(log₁₀ n)**

---

# Space Complexity

Only a few integer variables are used.

No additional array or data structure is created.

**Space Complexity: O(1)**

---

# Key Takeaways

- Store the original number before modifying `n`.
- Use `n % 10` to extract the last digit.
- Use `n /= 10` to remove the last digit.
- Build the reversed number using `reverse * 10 + digit`.
- Compare the reversed number with the original number.
- Equal values mean the number is a palindrome.

---

## 🔗 Problem Source

**Platform:** Naukri Code360

**Problem:** [Palindrome Number](https://www.naukri.com/code360/problems/palindrome-number_624662?leftPanelTabValue=SUBMISSION)
