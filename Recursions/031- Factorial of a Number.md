# Factorial

## Problem Statement

Given a non-negative integer `n`, find its factorial.

The factorial of a number `n` is the product of all positive integers from `1` to `n`.

It is represented as:

```text
n! = n × (n - 1) × (n - 2) × ... × 2 × 1
```

### Example

**Input**
```text
n = 5
```

**Output**
```text
120
```

Because:

```text
5! = 5 × 4 × 3 × 2 × 1
   = 120
```

---

# Approach

This solution uses **recursion** to calculate the factorial.

The recursive function `product()` follows two important parts:

1. **Base Case:** When `n` becomes `0`, return `1`.
2. **Recursive Case:** Multiply the current `n` by the factorial of `n - 1`.

The recursive formula is:

```text
n! = n × (n - 1)!
```

The recursion continues until:

```text
n = 0
```

At that point:

```text
0! = 1
```

The function then returns back through the previous calls and calculates the final product.

---

# Code

```java
class Solution {
    static int product(int n) {
        if (n == 0) {
            return 1;
        }

        return n * product(n - 1);
    }

    int factorial(int n) {
        int result = product(n);
        return result;
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 5
```

The `factorial()` method calls:

```text
product(5)
```

The function does not immediately calculate the final answer.

Instead, it keeps calling itself with `n - 1`.

The calls are:

```text
product(5)
    ↓
product(4)
    ↓
product(3)
    ↓
product(2)
    ↓
product(1)
    ↓
product(0)
```

When `product(0)` is reached, the base case returns:

```text
1
```

Now the recursive calls start returning and multiplying their values.

---

# Recursive Call 1

```text
product(5)
```

Since:

```text
5 != 0
```

the function returns:

```text
5 × product(4)
```

It must first calculate `product(4)`.

---

# Recursive Call 2

```text
product(4)
```

The function returns:

```text
4 × product(3)
```

---

# Recursive Call 3

```text
product(3)
```

The function returns:

```text
3 × product(2)
```

---

# Recursive Call 4

```text
product(2)
```

The function returns:

```text
2 × product(1)
```

---

# Recursive Call 5

```text
product(1)
```

The function returns:

```text
1 × product(0)
```

---

# Base Case

Now:

```text
product(0)
```

The condition:

```text
n == 0
```

is true.

Therefore:

```text
return 1;
```

This represents the mathematical rule:

```text
0! = 1
```

Now the recursive calls begin to return.

---

# Recursion Unwinding

The result from:

```text
product(0)
```

is:

```text
1
```

So:

```text
product(1)
= 1 × 1
= 1
```

Then:

```text
product(2)
= 2 × 1
= 2
```

Then:

```text
product(3)
= 3 × 2
= 6
```

Then:

```text
product(4)
= 4 × 6
= 24
```

Finally:

```text
product(5)
= 5 × 24
= 120
```

Therefore:

```text
factorial(5) = 120
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 5
```

### Going Down the Recursion

```text
product(5)
    ↓
5 × product(4)
    ↓
4 × product(3)
    ↓
3 × product(2)
    ↓
2 × product(1)
    ↓
1 × product(0)
    ↓
return 1
```

Now the recursion starts unwinding.

### Coming Back Up

```text
product(1) = 1 × 1 = 1
product(2) = 2 × 1 = 2
product(3) = 3 × 2 = 6
product(4) = 4 × 6 = 24
product(5) = 5 × 24 = 120
```

Final result:

```text
120
```

---

# Dry Run

| Call | `n` | Action | Returned Value |
|-----:|----:|--------|---------------:|
| 1 | 5 | `5 × product(4)` | 120 |
| 2 | 4 | `4 × product(3)` | 24 |
| 3 | 3 | `3 × product(2)` | 6 |
| 4 | 2 | `2 × product(1)` | 2 |
| 5 | 1 | `1 × product(0)` | 1 |
| 6 | 0 | Base case → return `1` | 1 |

Final answer:

```text
120
```

---

# Understanding the Call Stack

For:

```text
n = 5
```

the recursive calls are stored in the call stack:

```text
product(5)
product(4)
product(3)
product(2)
product(1)
product(0)
```

At `product(0)`, the base case returns `1`.

Then the stack starts unwinding:

```text
product(1) → 1
product(2) → 2
product(3) → 6
product(4) → 24
product(5) → 120
```

This is an important recursion concept: **the recursive calls go deeper first, and the multiplication is completed while the calls return.**

---

# Why This Solution Works

The factorial of `n` can be defined recursively as:

```text
n! = n × (n - 1)!
```

The solution directly follows this definition.

For example:

```text
5!
= 5 × 4!
= 5 × 4 × 3!
= 5 × 4 × 3 × 2!
= 5 × 4 × 3 × 2 × 1!
= 5 × 4 × 3 × 2 × 1 × 0!
```

Since:

```text
0! = 1
```

the final result becomes:

```text
5 × 4 × 3 × 2 × 1
= 120
```

Therefore, the recursive solution correctly calculates the factorial.

---

# Important Recursion Concept

There are two essential parts in this solution.

### Base Case

```text
if (n == 0)
```

This stops the recursion and returns `1`.

### Recursive Case

```text
n * product(n - 1)
```

This reduces the problem size by `1` and continues the recursion.

Without the base case, the function would continue calling itself indefinitely.

---

# Time Complexity

The function is called once for every value from `n` down to `0`.

Therefore:

**Time Complexity: O(n)**

---

# Space Complexity

Each recursive call is stored in the call stack until the base case is reached.

There are `n` recursive levels.

Therefore:

**Space Complexity: O(n)**

---

# Key Takeaways

- Factorial means multiplying all positive integers from `1` to `n`.
- The recursive formula is `n! = n × (n - 1)!`.
- `n == 0` is the base case.
- `0! = 1`.
- The recursive calls go deeper until the base case is reached.
- The multiplication happens while the recursion unwinds.
- The solution demonstrates how recursion can naturally represent a mathematical definition.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Factorial](https://www.geeksforgeeks.org/problems/factorial5739/1)
