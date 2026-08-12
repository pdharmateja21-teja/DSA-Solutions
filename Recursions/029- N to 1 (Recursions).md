# Print N to 1 Without Using Loop

## Problem Statement

Given an integer `n`, print all the numbers from `n` to `1` without using any loop.

This solution intentionally uses **recursion** to understand how recursive function calls work.

> **Note:** This problem can be solved using a loop, but recursion is used here specifically to understand the recursion concept.

### Example

**Input**
```text
n = 5
```

**Output**
```text
5 4 3 2 1
```

---

# Approach

We use recursion to print the numbers from `n` down to `1`.

The recursive function has two important parts:

1. **Base Case:** When `n` becomes `0`, stop the recursion.
2. **Recursive Case:** Print the current value of `n`, then call the function with `n - 1`.

The important difference from printing `1` to `n` is that the print statement comes **before** the recursive call.

The flow is:

```text
print n
↓
recursion(n - 1)
↓
print n - 1
↓
recursion(n - 2)
↓
...
↓
n = 0
↓
return
```

---

# Code

```java
class Solution {
    void recursion(int n) {
        if (n == 0) {
            return;
        }

        System.out.print(n + " ");
        recursion(n - 1);
    }

    void printNos(int n) {
        recursion(n);
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 5
```

The method:

```text
printNos(5)
```

calls:

```text
recursion(5)
```

Since `n` is not `0`, the function first prints `5` and then calls:

```text
recursion(4)
```

The same process continues until `n` becomes `0`.

---

## Recursive Call 1

```text
recursion(5)
```

The base condition:

```text
5 == 0
```

is false.

Print:

```text
5
```

Then call:

```text
recursion(4)
```

Output so far:

```text
5
```

---

## Recursive Call 2

```text
recursion(4)
```

The base condition is false.

Print:

```text
4
```

Then call:

```text
recursion(3)
```

Output so far:

```text
5 4
```

---

## Recursive Call 3

```text
recursion(3)
```

Print:

```text
3
```

Then call:

```text
recursion(2)
```

Output:

```text
5 4 3
```

---

## Recursive Call 4

```text
recursion(2)
```

Print:

```text
2
```

Then call:

```text
recursion(1)
```

Output:

```text
5 4 3 2
```

---

## Recursive Call 5

```text
recursion(1)
```

Print:

```text
1
```

Then call:

```text
recursion(0)
```

Output:

```text
5 4 3 2 1
```

---

## Base Case

Now:

```text
recursion(0)
```

The condition:

```text
n == 0
```

is true.

Therefore:

```text
return;
```

The recursion stops.

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 5
```

### Recursive Flow

```text
recursion(5)
    ↓
print 5
    ↓
recursion(4)
    ↓
print 4
    ↓
recursion(3)
    ↓
print 3
    ↓
recursion(2)
    ↓
print 2
    ↓
recursion(1)
    ↓
print 1
    ↓
recursion(0)
    ↓
return
```

Final output:

```text
5 4 3 2 1
```

---

# Dry Run

| Call | `n` | Action | Next Call |
|-----:|----:|--------|-----------|
| 1 | 5 | Print `5` | `recursion(4)` |
| 2 | 4 | Print `4` | `recursion(3)` |
| 3 | 3 | Print `3` | `recursion(2)` |
| 4 | 2 | Print `2` | `recursion(1)` |
| 5 | 1 | Print `1` | `recursion(0)` |
| 6 | 0 | Base case → `return` | Stops |

Final output:

```text
5 4 3 2 1
```

---

# Understanding the Recursion Flow

For:

```text
n = 5
```

the calls are created like this:

```text
recursion(5)
    ↓
recursion(4)
    ↓
recursion(3)
    ↓
recursion(2)
    ↓
recursion(1)
    ↓
recursion(0)
```

But unlike the `1 to N` recursion example, the number is printed **before** making the next recursive call.

Therefore, the output is produced immediately while going deeper:

```text
5
4
3
2
1
```

Then `recursion(0)` reaches the base case and stops further calls.

---

# Why This Solution Works

Each recursive call performs exactly one printing operation and decreases `n` by `1`.

For:

```text
n = 5
```

the values printed are:

```text
5 → 4 → 3 → 2 → 1
```

When `n` becomes `0`, the base case stops the recursion.

Therefore, every number from `n` down to `1` is printed exactly once.

The position of the print statement is important:

```text
System.out.print(n + " ");
recursion(n - 1);
```

Since printing happens **before** the recursive call, the numbers appear in decreasing order.

---

# Comparison With 1 to N Recursion

For printing `1` to `N`, the recursive call comes first:

```text
recursion(n - 1);
print n;
```

This prints while the recursion is **unwinding**:

```text
1 2 3 4 5
```

For printing `N` to `1`, the print comes first:

```text
print n;
recursion(n - 1);
```

This prints while the recursion is **going deeper**:

```text
5 4 3 2 1
```

This difference is an important recursion concept.

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

- This solution prints `N` to `1` without using a loop.
- Recursion repeatedly decreases `n` by `1`.
- `n == 0` is the base case.
- The current number is printed before the recursive call.
- Because printing happens before recursion, the numbers appear in decreasing order.
- `recursion(n - 1)` moves the problem toward the base case.
- The placement of the print statement determines whether recursion prints in increasing or decreasing order.
- This is a useful example for understanding the difference between **printing before recursion** and **printing after recursion**.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Print N to 1 Without Loop](https://www.geeksforgeeks.org/problems/print-n-to-1-without-loop/1)
