# Alpha Ramp Pattern

## Problem Statement

Given an integer `n`, print an alphabet ramp pattern where each row contains the same uppercase letter.

- The first row contains **A** once.
- The second row contains **B** twice.
- The third row contains **C** three times.
- This continues until the `n`th row.

### Example

**Input**
```
n = 5
```

**Output**
```
A
B B
C C C
D D D D
E E E E E
```

---

# Approach

The pattern consists of `n` rows.

- The **outer loop** controls the number of rows.
- The **inner loop** prints the current row's character.
- The character depends on the current row number (`i`).
- The number of times the character is printed is also determined by the current row.

The expression:

```java
(char)('A' + i)
```

generates the character for the current row.

---

# Code

```java
public class Solution {
    public static void alphaRamp(int n) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <= i; j++) {
                System.out.print((char) ('A' + i) + " ");
            }
            System.out.println();
        }
    }
}
```

---

# Understanding the Code

Suppose,

```
n = 5
```

Initially,

```
Number of Rows = 5
```

The outer loop starts.

---

## Row 1

```
i = 0
```

Character to print:

```
'A' + 0 = 'A'
```

Number of times printed:

```
i + 1 = 1
```

Output

```
A
```

---

## Row 2

```
i = 1
```

Character:

```
'A' + 1 = 'B'
```

Number of times printed:

```
2
```

Output

```
B B
```

---

## Row 3

```
i = 2
```

Character:

```
'A' + 2 = 'C'
```

Number of times printed:

```
3
```

Output

```
C C C
```

---

## Row 4

```
i = 3
```

Character:

```
'A' + 3 = 'D'
```

Number of times printed:

```
4
```

Output

```
D D D D
```

---

## Row 5

```
i = 4
```

Character:

```
'A' + 4 = 'E'
```

Number of times printed:

```
5
```

Output

```
E E E E E
```

The outer loop finishes.

Program Ends.

---

# Code Flow (Step-by-Step Execution)

### Input

```
n = 5
```

### Outer Loop (i = 0)

```
Character = A

Inner Loop

j = 0

Print:
A
```

---

### Outer Loop (i = 1)

```
Character = B

Inner Loop

j = 0
j = 1

Print:
B B
```

---

### Outer Loop (i = 2)

```
Character = C

Inner Loop

j = 0
j = 1
j = 2

Print:
C C C
```

---

### Outer Loop (i = 3)

```
Character = D

Inner Loop

j = 0
j = 1
j = 2
j = 3

Print:
D D D D
```

---

### Outer Loop (i = 4)

```
Character = E

Inner Loop

j = 0
j = 1
j = 2
j = 3
j = 4

Print:
E E E E E
```

Loop Ends.

---

# Dry Run

| Row | i | Character | Times Printed | Output |
|----:|--:|:---------:|--------------:|--------|
| 1 | 0 | A | 1 | A |
| 2 | 1 | B | 2 | B B |
| 3 | 2 | C | 3 | C C C |
| 4 | 3 | D | 4 | D D D D |
| 5 | 4 | E | 5 | E E E E E |

---

# Why This Solution Works

- The outer loop ensures exactly `n` rows are printed.
- The expression `(char)('A' + i)` selects the correct alphabet for the current row.
- The inner loop runs `i + 1` times, so the same character is printed repeatedly in that row.
- Since both the character and the number of repetitions depend on the current row, the required ramp pattern is formed correctly.

---

# Time Complexity

The outer loop runs `n` times.

The inner loop executes:

```
1 + 2 + 3 + ... + n
= n(n + 1) / 2
```

Therefore,

**Time Complexity: O(n²)**

---

# Space Complexity

The solution only uses loop variables.

No extra arrays, lists, or recursion are used.

**Space Complexity: O(1)**

---

# Key Takeaways

- The **outer loop** determines the current row.
- The **inner loop** determines how many times the character is printed.
- `(char)('A' + i)` generates the correct uppercase alphabet for each row.
- `i + 1` controls the number of repetitions.
- This pattern demonstrates how the **row number can simultaneously control both the value being printed and the number of times it is printed.**
