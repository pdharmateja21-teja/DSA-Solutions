
# Alpha Hill Pattern

## Problem Statement

Given an integer `n`, print a hill-shaped alphabet pattern.

- Each row begins with the letter **A**.
- The letters increase sequentially up to the current row's highest letter.
- Then the letters decrease back to **A**, forming a symmetric hill.

### Example

**Input**
```
n = 5
```

**Output**
```
    A
   A B A
  A B C B A
 A B C D C B A
A B C D E D C B A
```

---

# Approach

The pattern is divided into three parts for every row:

1. **Leading Spaces**
   - Print spaces before the letters so that the pattern is centered.

2. **Increasing Alphabets**
   - Print characters from **A** up to the current row's character.

3. **Decreasing Alphabets**
   - Print characters in reverse order back to **A**.
   - We start from `i - 2` because the highest character has already been printed in the increasing part.

---

# Code

```java
public class Solution {
    public static void alphaHill(int n) {
        for (int i = 1; i <= n; i++) {
            for (int j = 0; j < n - i; j++) {
                System.out.print(" ");
            }
            for (int j = 0; j < i; j++) {
                System.out.print((char) ('A' + j) + " ");
            }
            for (int j = i - 2; j >= 0; j--) {
                System.out.print((char) ('A' + j) + " ");
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

The pattern contains **5 rows**.

Each row consists of:

```
Leading Spaces
+
Increasing Alphabets
+
Decreasing Alphabets
```

---

## Row 1

```
i = 1
```

Leading Spaces

```
5 - 1 = 4
```

Increasing Part

```
A
```

Decreasing Part

```
No characters
```

Output

```
    A
```

---

## Row 2

```
i = 2
```

Leading Spaces

```
5 - 2 = 3
```

Increasing Part

```
A B
```

Decreasing Part

```
A
```

Output

```
   A B A
```

---

## Row 3

```
i = 3
```

Leading Spaces

```
5 - 3 = 2
```

Increasing Part

```
A B C
```

Decreasing Part

```
B A
```

Output

```
  A B C B A
```

---

## Row 4

```
i = 4
```

Leading Spaces

```
5 - 4 = 1
```

Increasing Part

```
A B C D
```

Decreasing Part

```
C B A
```

Output

```
 A B C D C B A
```

---

## Row 5

```
i = 5
```

Leading Spaces

```
0
```

Increasing Part

```
A B C D E
```

Decreasing Part

```
D C B A
```

Output

```
A B C D E D C B A
```

The outer loop finishes.

Program Ends.

---

# Code Flow (Step-by-Step Execution)

### Input

```
n = 5
```

### Outer Loop (i = 1)

```
Spaces = 4

Increasing:
A

Decreasing:
-

Print:
    A
```

---

### Outer Loop (i = 2)

```
Spaces = 3

Increasing:
A B

Decreasing:
A

Print:
   A B A
```

---

### Outer Loop (i = 3)

```
Spaces = 2

Increasing:
A B C

Decreasing:
B A

Print:
  A B C B A
```

---

### Outer Loop (i = 4)

```
Spaces = 1

Increasing:
A B C D

Decreasing:
C B A

Print:
 A B C D C B A
```

---

### Outer Loop (i = 5)

```
Spaces = 0

Increasing:
A B C D E

Decreasing:
D C B A

Print:
A B C D E D C B A
```

Loop Ends.

---

# Dry Run

| Row | Leading Spaces | Increasing Part | Decreasing Part | Output |
|----:|---------------:|-----------------|-----------------|--------|
| 1 | 4 | A | - | A |
| 2 | 3 | A B | A | A B A |
| 3 | 2 | A B C | B A | A B C B A |
| 4 | 1 | A B C D | C B A | A B C D C B A |
| 5 | 0 | A B C D E | D C B A | A B C D E D C B A |

---

# Why This Solution Works

- The **outer loop** prints each row.
- The **first inner loop** prints the leading spaces, centering the pattern.
- The **second inner loop** prints characters from **A** to the current row's highest character.
- The **third inner loop** prints the characters in reverse order, excluding the highest character to avoid duplication.
- Combining these three parts produces a perfectly symmetric alphabet hill.

---

# Time Complexity

The outer loop runs **n** times.

For each row:

- Leading spaces take at most **n** iterations.
- Increasing characters take at most **n** iterations.
- Decreasing characters take at most **n** iterations.

Overall,

**Time Complexity: O(n²)**

---

# Space Complexity

The solution only uses loop variables.

No extra arrays, lists, or recursion are used.

**Space Complexity: O(1)**

---

# Key Takeaways

- Divide complex patterns into smaller sections (spaces, increasing part, decreasing part).
- `(char)('A' + j)` is used to generate consecutive uppercase alphabets.
- The decreasing loop starts from `i - 2` to avoid printing the peak character twice.
- Center alignment is achieved by printing `n - i` leading spaces.
- Breaking the pattern into independent parts makes it easier to understand and implement.

