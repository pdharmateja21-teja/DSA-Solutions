

# Alphabet Triangle Pattern

## Problem Statement

Given an integer `N`, print an alphabet triangle where:

* The pattern contains `N` rows.
* The first row contains `A`.
* The second row contains `A B`.
* The third row contains `A B C`.
* Each row starts again from `A`.
* The number of characters increases by one in every row.

For example, when:

```text
N = 5
```

the output is:

```text
A
A B
A B C
A B C D
A B C D E
```

This is an increasing alphabet triangle pattern.

---

# Approach

The solution uses two nested loops.

* The **outer loop** controls the number of rows.
* The **inner loop** controls the number of alphabets printed in each row.

A character variable:

```text
char ch = 'A';
```

is initialized at the beginning of every row.

The inner loop then prints the current character and increments it:

```text
System.out.print(ch + " ");
ch++;
```

Because `ch` is reset to `'A'` for every new row, every row starts with `A`.

The number of characters printed in row `i` is exactly `i`.

Therefore:

```text
Row 1 → A
Row 2 → A B
Row 3 → A B C
...
```

---

# Code

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        for (int i = 1; i <= n; i++) {
            char ch = 'A';

            for (int j = 1; j <= i; j++) {
                System.out.print(ch + " ");
                ch++;
            }

            System.out.println();
        }
    }
}
```

---

# Understanding the Code

## 1. Read the Input

```text
int n = sc.nextInt();
```

The program reads the number of rows.

For example:

```text
N = 5
```

---

## 2. Outer Loop

```text
for (int i = 1; i <= n; i++)
```

The outer loop controls the rows.

For `N = 5`:

```text
i = 1
i = 2
i = 3
i = 4
i = 5
```

Therefore, the pattern contains **5 rows**.

---

## 3. Reset the Character

Inside the outer loop:

```text
char ch = 'A';
```

This is an important part of your approach.

The character is reset to `A` at the beginning of every row.

For example:

```text
Row 1 → A starts from A
Row 2 → A starts from A
Row 3 → A starts from A
Row 4 → A starts from A
```

Therefore, the pattern does **not** continue alphabetically across rows.

---

## 4. Inner Loop

```text
for (int j = 1; j <= i; j++)
```

The inner loop prints exactly `i` characters.

Therefore:

| Row `i` | Number of characters |
| ------: | -------------------: |
|       1 |                    1 |
|       2 |                    2 |
|       3 |                    3 |
|       4 |                    4 |
|       5 |                    5 |

---

## 5. Print and Increment

Inside the inner loop:

```text
System.out.print(ch + " ");
ch++;
```

The current character is printed first.

Then:

```text
ch++;
```

moves to the next alphabet.

For example:

```text
A → B → C → D → E
```

---

# Code Flow — Step-by-Step Execution

Consider:

```text
N = 5
```

---

## Row 1

```text
i = 1
```

First:

```text
ch = 'A'
```

Inner loop runs once:

```text
j = 1 → print A
```

Row output:

```text
A
```

---

## Row 2

```text
i = 2
```

Again:

```text
ch = 'A'
```

The inner loop runs twice:

```text
j = 1 → print A
j = 2 → print B
```

Row output:

```text
A B
```

---

## Row 3

```text
i = 3
```

Again, `ch` is reset:

```text
ch = 'A'
```

The inner loop runs three times:

```text
j = 1 → A
j = 2 → B
j = 3 → C
```

Row output:

```text
A B C
```

---

## Row 4

```text
i = 4
```

The character is reset to `A`.

The inner loop prints:

```text
A B C D
```

---

## Row 5

```text
i = 5
```

The character is reset to `A`.

The inner loop prints:

```text
A B C D E
```

---

# Dry Run

For:

```text
N = 5
```

| Row `i` | Starting `ch` | Inner Loop | Output      |
| ------: | ------------- | ---------: | ----------- |
|       1 | `A`           |     1 time | `A`         |
|       2 | `A`           |    2 times | `A B`       |
|       3 | `A`           |    3 times | `A B C`     |
|       4 | `A`           |    4 times | `A B C D`   |
|       5 | `A`           |    5 times | `A B C D E` |

Final output:

```text
A
A B
A B C
A B C D
A B C D E
```

---

# Why This Solution Works

The pattern requires every row to start from `A` and contain an increasing number of consecutive alphabets.

The outer loop determines the row number.

For every row, the character is reset:

```text
ch = 'A'
```

The inner loop then prints `i` characters while incrementing `ch` after every print.

For row `i`:

```text
Number of characters = i
Starting character = A
Ending character = A + i - 1
```

Therefore:

```text
Row 1 → A
Row 2 → A B
Row 3 → A B C
...
```

which produces the required triangular pattern.

---

# Approach Evaluation

**Approach Type:** Nested Loops + Character Increment

Your approach is **correct and straightforward** for this pattern.

The use of:

```text
char ch = 'A';
```

inside the outer loop is particularly important because it ensures that every row starts from `A`.

An alternative approach could calculate the character directly from `j`, but your `ch++` approach clearly demonstrates how characters progress from `A` to the required alphabet.

---

# Time Complexity

The inner loop runs:

```text
1 + 2 + 3 + ... + N
```

times.

The sum is:

```text
N(N + 1) / 2
```

Therefore:

**Time Complexity: O(N²)**

---

# Space Complexity

The solution uses only the variables `n`, `i`, `j`, and `ch`.

No additional data structure is used.

**Space Complexity: O(1)**

---

# Key Takeaways

* The outer loop controls the rows.
* The inner loop controls the number of alphabets in each row.
* Every row starts with `A`.
* `ch++` moves to the next alphabet.
* Row `i` contains exactly `i` characters.
* The pattern grows by one character per row.
* Time Complexity: **O(N²)**
* Space Complexity: **O(1)**

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Triangular Patterns of Alphabets](https://www.geeksforgeeks.org/dsa/program-for-triangular-patterns-of-alphabets/)

[1]: https://www.geeksforgeeks.org/dsa/program-for-triangular-patterns-of-alphabets/?utm_source=chatgpt.com "Program for triangular patterns of alphabets - GeeksforGeeks"

