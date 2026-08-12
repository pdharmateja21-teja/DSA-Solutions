# Count Primes

## Problem Statement

Given an integer `n`, count how many prime numbers are strictly less than `n`.

A prime number is a number greater than `1` that has exactly two factors:

```text
1 and itself
```

### Example

**Input**
```text
n = 10
```

**Output**
```text
4
```

The prime numbers less than `10` are:

```text
2, 3, 5, 7
```

Therefore, the answer is:

```text
4
```

---

# Approach

We use the **Sieve of Eratosthenes** to efficiently find all prime numbers less than `n`.

The idea is:

1. Create a boolean array `res` of size `n`.
2. Initially mark every number from `2` to `n - 1` as potentially prime.
3. Start from `2`.
4. If a number is still marked as prime, mark all of its multiples as non-prime.
5. Start marking from `i * i` because smaller multiples would already have been handled by smaller prime numbers.
6. Finally, count all numbers that are still marked as prime.

---

# Code

```java
class Solution {
    public int countPrimes(int n) {
        if (n <= 2) {
            return 0;
        }

        boolean[] res = new boolean[n];

        for (int i = 2; i < n; i++) {
            res[i] = true;
        }

        for (int i = 2; i * i <= n; i++) {
            if (res[i]) {
                for (int j = i * i; j < n; j += i) {
                    res[j] = false;
                }
            }
        }

        int count = 0;

        for (int i = 2; i < n; i++) {
            if (res[i]) {
                count++;
            }
        }

        return count;
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 10
```

We need to find all prime numbers strictly less than `10`.

The numbers we need to consider are:

```text
2, 3, 4, 5, 6, 7, 8, 9
```

Initially, every number from `2` to `9` is marked as `true`.

```text
2 → true
3 → true
4 → true
5 → true
6 → true
7 → true
8 → true
9 → true
```

At this stage, we have not yet identified which numbers are composite.

---

# Code Flow (Step-by-Step Execution)

## Step 1: Handle Small Values

The code first checks:

```text
n <= 2
```

If this is true, there are no prime numbers strictly less than `n`.

For example:

```text
n = 2
```

The only number below `2` is `1`, which is not prime.

Therefore:

```text
return 0
```

For our example:

```text
n = 10
```

so the algorithm continues.

---

## Step 2: Create the Boolean Array

Create:

```text
boolean[] res = new boolean[10]
```

Initially, all values are `false`.

Then the first loop marks numbers from `2` to `9` as `true`.

Conceptually:

```text
Number:  0  1  2  3  4  5  6  7  8  9
Status:  -  -  T  T  T  T  T  T  T  T
```

Here:

```text
T = potentially prime
```

---

## Step 3: Start the Sieve

The outer loop starts with:

```text
i = 2
```

Check:

```text
res[2] == true
```

So `2` is considered prime.

Now mark all multiples of `2` starting from:

```text
2 * 2 = 4
```

The values are:

```text
4
6
8
```

Mark them as `false`.

Current state:

```text
Number:  2  3  4  5  6  7  8  9
Status:  T  T  F  T  F  T  F  T
```

---

## Step 4: Process 3

Next:

```text
i = 3
```

Since:

```text
res[3] == true
```

`3` is prime.

Start from:

```text
3 * 3 = 9
```

Mark multiples of `3`:

```text
9
```

as `false`.

Current state:

```text
Number:  2  3  4  5  6  7  8  9
Status:  T  T  F  T  F  T  F  F
```

---

## Step 5: Stop the Sieve

The outer loop condition is:

```text
i * i <= n
```

For:

```text
i = 4
```

we get:

```text
4 * 4 = 16
```

Since:

```text
16 > 10
```

the loop stops.

There is no need to process `4` or any larger value because all composite numbers below `10` have already been marked.

---

## Step 6: Count the Remaining Prime Numbers

The final loop checks all numbers from `2` to `9`.

The values still marked as `true` are:

```text
2
3
5
7
```

Therefore:

```text
count = 4
```

The method returns:

```text
4
```

---

# Dry Run

For:

```text
n = 10
```

| Step | Number / Action | Result |
|-----:|-----------------|--------|
| 1 | Mark `2` to `9` as prime candidates | All `true` |
| 2 | `i = 2` | Mark `4, 6, 8` as `false` |
| 3 | `i = 3` | Mark `9` as `false` |
| 4 | `i = 4` | `4 × 4 > 10`, stop |
| 5 | Count remaining `true` values | `2, 3, 5, 7` |
| 6 | Final count | `4` |

Final result:

```text
4
```

---

# Why Start From `i * i`?

When processing a number `i`, the code starts marking multiples from:

```text
i * i
```

instead of:

```text
i * 2
```

For example, when processing `5`, the smaller multiples:

```text
10
15
20
```

may already have been identified as composite by smaller prime numbers.

For example:

```text
10 = 2 × 5
15 = 3 × 5
```

Therefore, we only need to start from:

```text
5 × 5 = 25
```

This avoids unnecessary work.

---

# Why This Solution Works

The Sieve of Eratosthenes works by identifying prime numbers and eliminating their multiples.

If `i` is prime, then every multiple of `i` greater than `i` is composite.

For example, when `i = 2`:

```text
4, 6, 8, 10, 12, ...
```

are composite.

When `i = 3`:

```text
6, 9, 12, 15, ...
```

are composite.

After all required multiples are marked as `false`, the numbers still marked `true` are exactly the prime numbers.

Therefore, counting those values gives the number of primes less than `n`.

---

# Time Complexity

The Sieve of Eratosthenes processes numbers and their multiples efficiently.

**Time Complexity: O(n log log n)**

---

# Space Complexity

A boolean array of size `n` is created.

```text
boolean[] res = new boolean[n]
```

Therefore:

**Space Complexity: O(n)**

---

# Key Takeaways

- The problem asks for primes strictly less than `n`.
- The Sieve of Eratosthenes is an efficient way to find them.
- `true` represents a number that is still considered prime.
- Multiples of confirmed primes are marked as `false`.
- Multiples are marked starting from `i * i`.
- After the sieve finishes, count the remaining `true` values.
- The final count is the number of prime numbers less than `n`.

---

## 🔗 Problem Source

**Platform:** LeetCode

**Problem:** [Count Primes](https://leetcode.com/problems/count-primes/description/)
