# Alpha Triangle Pattern

## Problem Statement

Given an integer `n`, print an alphabet triangle where each row starts from the highest required alphabet and ends at the last alphabet.

- The first row contains only the last alphabet.
- Every new row adds one more alphabet to the **left**.
- The alphabets are printed in ascending order from left to right.

### Example

**Input**
```
n = 5
```

**Output**
```
E
D E
C D E
B C D E
A B C D E
```

---

# Approach

The pattern consists of `n` rows.

- The **outer loop** controls the number of rows.
- The **inner loop** prints the characters in the current row.
- The starting alphabet of each row moves one position backward.
- The ending alphabet always remains the last alphabet (`'A' + n - 1`).

The expression

```java
(char)('A' + j)
```

converts the integer position into its corresponding uppercase alphabet.

---

# Code

```java
public class Solution {
    public static void alphaTriangle(int n) {
        for (int i = 0; i < n; i++) {
            for (int j = n - 1; j >= n - i - 1; j--) {
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

The last alphabet is

```
'A' + (5 - 1)
= 'A' + 4
= E
```

Every row starts one alphabet earlier than the previous row.

---

## Row 1

```
i = 0
```

Inner Loop

```
j starts from 4
j ends at 4
```

Characters

```
'A' + 4 = E
```

Output

```
E
```

---

## Row 2

```
i = 1
```

Inner Loop

```
j = 4
j = 3
```

Characters Printed

```
E
D
```

Since the loop runs backward, the output becomes

```
D E
```

---

## Row 3

```
i = 2
```

Inner Loop

```
j = 4
j = 3
j = 2
```

Characters

```
E
D
C
```

Output

```
C D E
```

---

## Row 4

```
i = 3
```

Inner Loop

```
j = 4
j = 3
j = 2
j = 1
```

Output

```
B C D E
```

---

## Row 5

```
i = 4
```

Inner Loop

```
j = 4
j = 3
j = 2
j = 1
j = 0
```

Output

```
A B C D E
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
Starting Index = 4

j = 4

Characters:
E

Print:
E
```

---

### Outer Loop (i = 1)

```
Starting Index = 3

j = 4
j = 3

Characters:
E
D

Output Order:
D E
```

---

### Outer Loop (i = 2)

```
Starting Index = 2

j = 4
j = 3
j = 2

Characters:
E
D
C

Output Order:
C D E
```

---

### Outer Loop (i = 3)

```
Starting Index = 1

j = 4
j = 3
j = 2
j = 1

Output Order:
B C D E
```

---

### Outer Loop (i = 4)

```
Starting Index = 0

j = 4
j = 3
j = 2
j = 1
j = 0

Output Order:
A B C D E
```

Loop Ends.

---

# Dry Run

| Row | i | j Values | Output |
|----:|--:|----------------|--------|
| 1 | 0 | 4 | E |
| 2 | 1 | 4, 3 | D E |
| 3 | 2 | 4, 3, 2 | C D E |
| 4 | 3 | 4, 3, 2, 1 | B C D E |
| 5 | 4 | 4, 3, 2, 1, 0 | A B C D E |

---

# Why This Solution Works

- The **outer loop** prints exactly `n` rows.
- The **inner loop** starts from the last alphabet index (`n - 1`) and extends one position further left in every new row.
- Although `j` decreases, each character is printed immediately, resulting in the required sequence for the pattern.
- By reducing the lower limit (`n - i - 1`) after every row, one additional alphabet is included, producing the desired triangle.

---

# Time Complexity

The outer loop runs **n** times.

The inner loop executes:

```
1 + 2 + 3 + ... + n
= n(n + 1) / 2
```

Therefore,

**Time Complexity: O(n²)**

---

# Space Complexity

Only loop variables are used.

No extra arrays, lists, or recursion are required.

**Space Complexity: O(1)**

---

# Key Takeaways

- The outer loop controls the rows.
- The inner loop expands the range of printed alphabets by one in each row.
- `(char)('A' + j)` converts an index into its corresponding uppercase alphabet.
- The lower limit `n - i - 1` determines where each row begins.
- This pattern demonstrates how changing only the loop boundaries can generate different alphabet patterns while keeping the overall logic simple.
