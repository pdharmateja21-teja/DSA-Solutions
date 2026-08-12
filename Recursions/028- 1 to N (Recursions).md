# Print 1 to N Without Using Loops

## Problem Statement

Given an integer `n`, print all the numbers from `1` to `n` without using any loop.

This solution intentionally uses **recursion** to understand how recursive function calls and the call stack work.

> **Note:** This problem can be solved easily using a loop, but recursion is used here specifically to understand the recursion concept.

### Example

**Input**
```text
n = 5
```

**Output**
```text
1 2 3 4 5
```

---

# Approach

We use recursion to print the numbers from `1` to `n`.

The recursive function has two important parts:

1. **Base Case:** When `n` becomes `0`, stop the recursion.
2. **Recursive Case:** First call the function with `n - 1`, then print `n`.

The important part is that the recursive call comes **before** the print statement:

```text
recursion(n - 1)
print n
```

Because of this order, the numbers are printed while the recursive calls are returning.

For:

```text
n = 5
```

the calls go down like this:

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

Then the calls return and print:

```text
1 2 3 4 5
```

---

# Code

```java
class Solution {
    void recursion(int n) {
        if (n == 0) {
            return;
        }

        recursion(n - 1);
        System.out.print(n + " ");
    }

    public void printTillN(int n) {
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
printTillN(5)
```

calls:

```text
recursion(5)
```

The function first checks the base case:

```text
n == 0
```

Since `5 != 0`, it makes another recursive call:

```text
recursion(4)
```

This continues until:

```text
recursion(0)
```

is reached.

---

## Recursive Call 1

```text
recursion(5)
```

The base condition is false.

So the function calls:

```text
recursion(4)
```

The print statement has not executed yet.

---

## Recursive Call 2

```text
recursion(4)
```

Again, the base condition is false.

Call:

```text
recursion(3)
```

The print statement is still waiting.

---

## Recursive Call 3

```text
recursion(3)
```

Call:

```text
recursion(2)
```

No number is printed yet.

---

## Recursive Call 4

```text
recursion(2)
```

Call:

```text
recursion(1)
```

Still no number is printed.

---

## Recursive Call 5

```text
recursion(1)
```

Call:

```text
recursion(0)
```

Still no number is printed.

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

The recursion stops going deeper.

Now the important part begins: **the previous function calls start returning**.

---

# Recursion Unwinding

The call `recursion(1)` continues after:

```text
recursion(0)
```

returns.

So it executes:

```text
System.out.print(1 + " ");
```

Output:

```text
1
```

Then `recursion(1)` returns to `recursion(2)`.

---

### `recursion(2)`

Now:

```text
System.out.print(2 + " ");
```

Output:

```text
1 2
```

---

### `recursion(3)`

Now:

```text
System.out.print(3 + " ");
```

Output:

```text
1 2 3
```

---

### `recursion(4)`

Now:

```text
System.out.print(4 + " ");
```

Output:

```text
1 2 3 4
```

---

### `recursion(5)`

Finally:

```text
System.out.print(5 + " ");
```

Output:

```text
1 2 3 4 5
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 5
```

### Going Down the Recursion

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

At `recursion(0)`:

```text
return
```

Now the recursion starts unwinding.

### Coming Back Up

```text
recursion(1) → print 1
recursion(2) → print 2
recursion(3) → print 3
recursion(4) → print 4
recursion(5) → print 5
```

Final output:

```text
1 2 3 4 5
```

---

# Dry Run

| Call | `n` | Action |
|-----:|----:|--------|
| 1 | 5 | Call `recursion(4)` |
| 2 | 4 | Call `recursion(3)` |
| 3 | 3 | Call `recursion(2)` |
| 4 | 2 | Call `recursion(1)` |
| 5 | 1 | Call `recursion(0)` |
| 6 | 0 | Base case → `return` |
| 5 | 1 | Print `1` |
| 4 | 2 | Print `2` |
| 3 | 3 | Print `3` |
| 2 | 4 | Print `4` |
| 1 | 5 | Print `5` |

Final output:

```text
1 2 3 4 5
```

---

# Understanding the Call Stack

For:

```text
n = 5
```

the recursive calls are stored in the call stack:

```text
recursion(5)
recursion(4)
recursion(3)
recursion(2)
recursion(1)
recursion(0)
```

When `recursion(0)` reaches the base case, it returns.

Then the most recent unfinished call is completed first:

```text
recursion(1)
```

Then:

```text
recursion(2)
```

Then:

```text
recursion(3)
```

and so on.

This is why the numbers are printed in increasing order.

---

# Why This Solution Works

The key is the position of the recursive call:

```text
recursion(n - 1);
System.out.print(n + " ");
```

The number is printed **after** the recursive call finishes.

Therefore, the function first reaches `0` and then prints numbers during the return phase:

```text
1 → 2 → 3 → 4 → 5
```

If the print statement were placed before the recursive call, the numbers would instead be printed while going deeper into the recursion.

This makes the solution a useful example for understanding **recursion unwinding**.

---

# Time Complexity

The function is called once for every value from `n` down to `0`.

Therefore:

**Time Complexity: O(n)**

---

# Space Complexity

Each recursive call remains in the call stack until the base case is reached.

There are `n` recursive levels.

Therefore:

**Space Complexity: O(n)**

---

# Key Takeaways

- This solution prints `1` to `n` without using a loop.
- Recursion is used to repeatedly reduce `n` by `1`.
- `n == 0` is the base case that stops the recursion.
- The recursive call is placed before the print statement.
- Because printing happens after the recursive call, numbers are printed during **recursion unwinding**.
- The call stack explains why `1` is printed before `2`, `2` before `3`, and so on.
- This is a good example for understanding the difference between the **going-down phase** and the **returning-up phase** of recursion.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Print 1 to N Without Using Loops](https://www.geeksforgeeks.org/problems/print-1-to-n-without-using-loops3621/1)
