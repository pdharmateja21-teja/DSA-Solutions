# Inverted Letter Triangle Pattern

## Problem Statement

Given an integer `n`, print an inverted letter triangle pattern.

Each row starts from the character **'A'** and prints consecutive uppercase alphabets.
The number of characters decreases by **one** in every row.

### Example

Input:
```
n = 5
```

Output:
```
A B C D E
A B C D
A B C
A B
A
```

---

# Approach

The pattern consists of **n rows**.

- The **outer loop** is responsible for printing each row.
- The **inner loop** prints the letters in that row.
- For every new row, the number of printed letters decreases by one.
- To print alphabets, we use:
  ```java
  (char)('A' + j)
  ```
  Here,
  - `'A'` is the starting character.
  - `j` determines how many positions to move forward in the alphabet.

---

# Complete Code with Comments

```java
public class Solution {

    public static void nLetterTriangle(int n) {

        // Outer loop controls the number of rows.
        for (int i = 0; i < n; i++) {

            // Inner loop prints characters from 'A'
            // up to the required number of letters.
            // Number of letters in each row = (n - i)
            for (int j = 0; j < n - i; j++) {

                // Convert the current position into its
                // corresponding uppercase alphabet.
                System.out.print((char) ('A' + j) + " ");
            }

            // Move to the next line after completing one row.
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

Number of letters:

```
n - i
= 5 - 0
= 5
```

Inner loop values:

```
j = 0 → 'A'
j = 1 → 'B'
j = 2 → 'C'
j = 3 → 'D'
j = 4 → 'E'
```

Output

```
A B C D E
```

---

## Row 2

```
i = 1
```

Number of letters:

```
5 - 1 = 4
```

Inner loop values:

```
j = 0 → A
j = 1 → B
j = 2 → C
j = 3 → D
```

Output

```
A B C D
```

---

## Row 3

```
i = 2
```

Number of letters

```
5 - 2 = 3
```

Inner loop

```
A
B
C
```

Output

```
A B C
```

---

## Row 4

```
i = 3
```

Number of letters

```
5 - 3 = 2
```

Output

```
A B
```

---

## Row 5

```
i = 4
```

Number of letters

```
5 - 4 = 1
```

Output

```
A
```

Outer loop finishes.

Program Ends.

---

# Complete Code Flow

Input

```
n = 5
```

### Outer Loop (i = 0)

```
Letters = 5

j = 0 → A
j = 1 → B
j = 2 → C
j = 3 → D
j = 4 → E

Print:
A B C D E
```

---

### Outer Loop (i = 1)

```
Letters = 4

j = 0 → A
j = 1 → B
j = 2 → C
j = 3 → D

Print:
A B C D
```

---

### Outer Loop (i = 2)

```
Letters = 3

j = 0 → A
j = 1 → B
j = 2 → C

Print:
A B C
```

---

### Outer Loop (i = 3)

```
Letters = 2

j = 0 → A
j = 1 → B

Print:
A B
```

---

### Outer Loop (i = 4)

```
Letters = 1

j = 0 → A

Print:
A
```

Loop Ends.

---

# Dry Run

| Row | i | Number of Letters | Characters Printed |
|----:|--:|------------------:|--------------------|
| 1 | 0 | 5 | A B C D E |
| 2 | 1 | 4 | A B C D |
| 3 | 2 | 3 | A B C |
| 4 | 3 | 2 | A B |
| 5 | 4 | 1 | A |

---

# Why This Solution Works

- The outer loop ensures exactly **n rows** are printed.
- The expression **(n - i)** reduces the number of characters by one after every row.
- The expression **('A' + j)** generates consecutive uppercase letters starting from **A**.
- Since every row always starts from **A**, the desired inverted triangle pattern is formed correctly.

---

# Time Complexity

```
Outer Loop = n times

Inner Loop = n + (n-1) + (n-2) + ... + 1

= n(n + 1) / 2
```

**Time Complexity: O(n²)**

---

# Space Complexity

Only loop variables are used.

No extra arrays, lists, or recursion.

**Space Complexity: O(1)**

---

# Key Takeaways

- Use the **outer loop** to control the number of rows.
- Use the **inner loop** to control the number of characters in each row.
- `(char)('A' + j)` is a simple way to generate consecutive uppercase letters.
- The expression `(n - i)` creates the decreasing pattern by reducing one character in each row.
- This is a common pattern-printing technique useful for strengthening nested loop concepts.
