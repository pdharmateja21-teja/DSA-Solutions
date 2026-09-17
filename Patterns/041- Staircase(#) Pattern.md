# Staircase

## Problem Statement

Given an integer `N`, print a right-aligned staircase of height `N` using `#` symbols and spaces.

The staircase contains:

* `N` rows.
* The first row contains `1` `#`.
* Each next row contains one additional `#`.
* The number of leading spaces decreases by one in every row.
* The last row contains `N` `#` symbols and no leading spaces.

For example, if:

```text
N = 4
```

the output is:

```text
   #
  ##
 ###
####
```

The staircase is right-aligned, and the last line is not preceded by spaces.

---

# Approach

For every row, we divide the pattern into two parts:

1. **Spaces** — printed before the `#` symbols.
2. **Hashes** — printed after the spaces.

For row `i`:

* Number of spaces = `N - i`
* Number of `#` symbols = `i`

We use two inner loops:

* The first loop prints the required spaces.
* The second loop prints the required `#` symbols.
* `System.out.println()` moves to the next row.

As the row number increases, the number of spaces decreases while the number of `#` symbols increases.

---

# Code

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    public static void staircase(int n) {

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n - i; j++) {
                System.out.print(" ");
            }

            for (int j = 1; j <= i; j++) {
                System.out.print("#");
            }

            System.out.println();
        }
    }
}

public class Solution {

    public static void main(String[] args) throws IOException {

        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(bufferedReader.readLine().trim());

        Result.staircase(n);

        bufferedReader.close();
    }
}
```

---

# Understanding the Code

### 1. Read the input

```text
int n = Integer.parseInt(bufferedReader.readLine().trim());
```

The input value `N` represents both the height and width of the staircase.

For example:

```text
N = 5
```

---

### 2. Outer Loop

```text
for (int i = 1; i <= n; i++)
```

The outer loop controls the rows.

Since `i` starts from `1` and goes up to `N`, exactly `N` rows are produced.

For `N = 5`:

```text
i = 1
i = 2
i = 3
i = 4
i = 5
```

---

### 3. Print Spaces

```text
for (int j = 1; j <= n - i; j++)
```

The number of spaces in row `i` is:

```text
N - i
```

For `N = 5`:

| Row `i` | Spaces `N - i` |
| ------: | -------------: |
|       1 |              4 |
|       2 |              3 |
|       3 |              2 |
|       4 |              1 |
|       5 |              0 |

This decreasing number of spaces makes the staircase right-aligned.

---

### 4. Print `#` Symbols

```text
for (int j = 1; j <= i; j++)
```

The number of `#` symbols is exactly equal to the row number.

For `N = 5`:

| Row `i` | `#` Symbols |
| ------: | ----------: |
|       1 |           1 |
|       2 |           2 |
|       3 |           3 |
|       4 |           4 |
|       5 |           5 |

Therefore, the number of `#` symbols increases by one in every row.

---

# Code Flow (Step-by-Step Execution)

Consider:

```text
N = 5
```

### Row 1

```text
i = 1
```

Spaces:

```text
5 - 1 = 4
```

Hashes:

```text
1
```

Output:

```text
    #
```

---

### Row 2

```text
i = 2
```

Spaces:

```text
5 - 2 = 3
```

Hashes:

```text
2
```

Output:

```text
   ##
```

---

### Row 3

```text
i = 3
```

Spaces:

```text
5 - 3 = 2
```

Hashes:

```text
3
```

Output:

```text
  ###
```

---

### Row 4

```text
i = 4
```

Spaces:

```text
5 - 4 = 1
```

Hashes:

```text
4
```

Output:

```text
 ####
```

---

### Row 5

```text
i = 5
```

Spaces:

```text
5 - 5 = 0
```

Hashes:

```text
5
```

Output:

```text
#####
```

---

### Final Output

```text
    #
   ##
  ###
 ####
#####
```

The key relationship is:

```text
Spaces = N - i
Hashes = i
```

As `i` increases, spaces decrease and hashes increase, creating the right-aligned staircase.

---

# Dry Run

For:

```text
N = 4
```

| Row `i` | Spaces `N - i` | `#` Count | Output |
| ------: | -------------: | --------: | ------ |
|       1 |              3 |         1 | `   #` |
|       2 |              2 |         2 | `  ##` |
|       3 |              1 |         3 | ` ###` |
|       4 |              0 |         4 | `####` |

Final output:

```text
   #
  ##
 ###
####
```

---

# Why This Solution Works

A right-aligned staircase requires the first row to have the maximum number of leading spaces and only one `#`.

With every new row:

* One space is removed.
* One `#` is added.

The formulas:

```text
Spaces = N - i
Hashes = i
```

produce exactly this behavior.

When `i = N`, the number of spaces becomes `0`, so the final row contains only `N` `#` symbols, satisfying the requirement that the last line has no leading spaces.

---

# Time Complexity

For every row, the solution prints a combination of spaces and `#` symbols.

Across all rows, the total number of printed characters is proportional to `N²`.

**Time Complexity: O(N²)**

---

# Space Complexity

The solution does not use any additional data structure. It only uses loop variables and the input variable.

**Space Complexity: O(1)**

---

# Key Takeaways

* Use nested loops to construct the staircase.
* The outer loop controls the rows.
* The first inner loop prints leading spaces.
* The second inner loop prints `#` symbols.
* Spaces follow the formula `N - i`.
* Hashes follow the formula `i`.
* Spaces decrease while hashes increase.
* The final row contains no leading spaces.
* The overall time complexity is **O(N²)**.

---

## 🔗 Problem Source

**Platform:** HackerRank

**Problem:** [Staircase](https://www.hackerrank.com/challenges/staircase/problem)
