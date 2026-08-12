# Print GFG N Times

## Problem Statement

Given an integer `n`, print the string `GFG` exactly `n` times.

This solution intentionally uses **recursion** to understand how recursive function calls work.

> **Note:** This problem can also be solved easily using a loop. However, recursion is used here specifically to understand the recursion concept, including the base case and recursive call.

### Example

**Input**
```text
n = 5
```

**Output**
```text
GFG GFG GFG GFG GFG
```

---

# Approach

We use recursion to print `GFG` exactly `n` times.

The recursive function follows two important parts:

1. **Base Case:**  
   When `n` becomes `0`, stop the recursion.

2. **Recursive Case:**  
   Print `GFG` once and call the same function with `n - 1`.

The flow is:

```text
print GFG
↓
call printGFG(n - 1)
↓
print GFG
↓
call printGFG(n - 2)
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
import java.util.Scanner;

class GFG {
    static void printGFG(int n) {
        if (n == 0) {
            return;
        }

        System.out.print("GFG ");
        printGFG(n - 1);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        printGFG(n);
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 3
```

The first call is:

```text
printGFG(3)
```

Since `n` is not `0`, the function prints:

```text
GFG
```

Then it calls:

```text
printGFG(2)
```

The same process continues until `n` becomes `0`.

---

## Recursive Call 1

```text
printGFG(3)
```

Condition:

```text
3 == 0
```

is false.

Print:

```text
GFG
```

Then call:

```text
printGFG(2)
```

Output so far:

```text
GFG
```

---

## Recursive Call 2

```text
printGFG(2)
```

Condition:

```text
2 == 0
```

is false.

Print:

```text
GFG
```

Then call:

```text
printGFG(1)
```

Output so far:

```text
GFG GFG
```

---

## Recursive Call 3

```text
printGFG(1)
```

Condition:

```text
1 == 0
```

is false.

Print:

```text
GFG
```

Then call:

```text
printGFG(0)
```

Output so far:

```text
GFG GFG GFG
```

---

## Base Case

Now:

```text
printGFG(0)
```

The condition:

```text
n == 0
```

is true.

So:

```text
return;
```

The function stops making recursive calls.

Final output:

```text
GFG GFG GFG
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 3
```

### Recursive Flow

```text
printGFG(3)
    ↓
print GFG
    ↓
printGFG(2)
    ↓
print GFG
    ↓
printGFG(1)
    ↓
print GFG
    ↓
printGFG(0)
    ↓
return
```

Final output:

```text
GFG GFG GFG
```

---

# Dry Run

| Call | `n` | Action | Next Call |
|-----:|----:|--------|-----------|
| 1 | 3 | Print `GFG` | `printGFG(2)` |
| 2 | 2 | Print `GFG` | `printGFG(1)` |
| 3 | 1 | Print `GFG` | `printGFG(0)` |
| 4 | 0 | Base case → `return` | Stops |

Final output:

```text
GFG GFG GFG
```

---

# Understanding the Base Case

The base case is:

```java
if (n == 0) {
    return;
}
```

This is what stops the recursion.

Without a base case, the function would continue calling itself indefinitely.

For example:

```text
printGFG(3)
→ printGFG(2)
→ printGFG(1)
→ printGFG(0)
→ printGFG(-1)
→ printGFG(-2)
→ ...
```

The base case prevents this from happening.

---

# Understanding the Recursive Case

The recursive call is:

```java
printGFG(n - 1);
```

Every recursive call decreases `n` by `1`.

For:

```text
n = 5
```

the calls become:

```text
printGFG(5)
printGFG(4)
printGFG(3)
printGFG(2)
printGFG(1)
printGFG(0)
```

Therefore, `GFG` is printed exactly five times.

---

# Why This Solution Works

Each function call prints `GFG` exactly once and then reduces `n` by `1`.

Starting from `n`, the function continues until it reaches the base case:

```text
n = 0
```

Therefore, the function makes exactly `n` printing operations.

For example, with:

```text
n = 4
```

there are four printing calls:

```text
printGFG(4) → GFG
printGFG(3) → GFG
printGFG(2) → GFG
printGFG(1) → GFG
printGFG(0) → stop
```

So the output contains exactly four `GFG` strings.

---

# Recursion Flow

The important concept is that each function call creates another function call before the current call finishes.

For:

```text
n = 3
```

the call chain is:

```text
printGFG(3)
    |
    └── printGFG(2)
            |
            └── printGFG(1)
                    |
                    └── printGFG(0)
                            |
                            └── return
```

The printing happens **before** the recursive call, so the output is produced while the recursive calls are being created.

---

# Time Complexity

The function is called once for every value of `n` until `0`.

Therefore:

**Time Complexity: O(n)**

---

# Space Complexity

Each recursive call is stored in the call stack until the base case is reached.

For `n` recursive levels:

**Space Complexity: O(n)**

---

# Key Takeaways

- Recursion means a function calls itself.
- Every recursive solution needs a stopping condition called the **base case**.
- Here, the base case is `n == 0`.
- Each call prints `GFG` once.
- `n - 1` moves the problem toward the base case.
- For understanding recursion, the important part is the relationship between the **base case** and the **recursive call**.
- Although a loop could solve this problem, recursion is used here specifically to understand recursive execution.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Print GFG N Times](https://www.geeksforgeeks.org/problems/print-gfg-n-times/1)
