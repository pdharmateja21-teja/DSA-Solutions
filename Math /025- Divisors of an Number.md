# All Divisors of a Number

## Problem Statement

Given an integer `n`, find all the divisors of the number and return them in sorted order.

A divisor is a number that divides `n` completely without leaving a remainder.

### Example

**Input**
```text
n = 12
```

**Output**
```text
[1, 2, 3, 4, 6, 12]
```

The divisors of `12` are:

```text
1, 2, 3, 4, 6, 12
```

---

# Approach

Instead of checking every number from `1` to `n`, we only need to check numbers up to `√n`.

Whenever `i` divides `n`, we get two divisors:

```text
i
n / i
```

For example, when:

```text
n = 12
i = 3
```

we get:

```text
3
12 / 3 = 4
```

So both `3` and `4` are divisors.

The solution uses two lists:

- `result` stores the smaller divisors in increasing order.
- `large` stores the corresponding larger divisors.

The `large` list is traversed in reverse at the end so that all divisors appear in sorted order.

---

# Code

```java
class Solution {
    public ArrayList<Integer> getDivisors(int n) {
        ArrayList<Integer> result = new ArrayList<>();
        ArrayList<Integer> large = new ArrayList<>();

        for (int i = 1; i * i <= n; i++) {
            if (n % i == 0) {
                result.add(i);

                if (i != n / i) {
                    large.add(n / i);
                }
            }
        }

        for (int i = large.size() - 1; i >= 0; i--) {
            result.add(large.get(i));
        }

        return result;
    }
}
```

---

# Understanding the Code

Suppose:

```text
n = 12
```

Initially:

```text
result = []
large = []
```

The loop checks values of `i` while:

```text
i * i <= n
```

For `n = 12`, we check:

```text
i = 1
i = 2
i = 3
```

The next value would be:

```text
i = 4
```

But:

```text
4 * 4 = 16 > 12
```

so the loop stops.

---

## Iteration 1

```text
i = 1
```

Check:

```text
12 % 1 == 0
```

So `1` is a divisor.

Add it to `result`:

```text
result = [1]
```

Its corresponding divisor is:

```text
12 / 1 = 12
```

Since:

```text
1 != 12
```

add `12` to `large`:

```text
large = [12]
```

---

## Iteration 2

```text
i = 2
```

Check:

```text
12 % 2 == 0
```

So `2` is a divisor.

Add it to `result`:

```text
result = [1, 2]
```

Corresponding divisor:

```text
12 / 2 = 6
```

Since:

```text
2 != 6
```

add `6` to `large`:

```text
large = [12, 6]
```

---

## Iteration 3

```text
i = 3
```

Check:

```text
12 % 3 == 0
```

So `3` is a divisor.

Add it to `result`:

```text
result = [1, 2, 3]
```

Corresponding divisor:

```text
12 / 3 = 4
```

Since:

```text
3 != 4
```

add `4` to `large`:

```text
large = [12, 6, 4]
```

---

# Building the Final Result

At this point:

```text
result = [1, 2, 3]
large = [12, 6, 4]
```

The values in `large` are in decreasing order because they were found as:

```text
12, 6, 4
```

To maintain sorted order, the second loop traverses `large` backwards.

First:

```text
large[2] = 4
```

Add to `result`:

```text
[1, 2, 3, 4]
```

Then:

```text
large[1] = 6
```

Result:

```text
[1, 2, 3, 4, 6]
```

Then:

```text
large[0] = 12
```

Final result:

```text
[1, 2, 3, 4, 6, 12]
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
n = 12
```

### Initial State

```text
result = []
large = []
```

### Flow

```text
i = 1
12 % 1 = 0
result = [1]
large = [12]

i = 2
12 % 2 = 0
result = [1, 2]
large = [12, 6]

i = 3
12 % 3 = 0
result = [1, 2, 3]
large = [12, 6, 4]
```

The next value:

```text
i = 4
```

does not satisfy:

```text
4 * 4 <= 12
```

So the first loop ends.

Now traverse `large` backwards:

```text
4 → 6 → 12
```

Add them to `result`:

```text
[1, 2, 3, 4, 6, 12]
```

Return:

```text
[1, 2, 3, 4, 6, 12]
```

---

# Dry Run

For:

```text
n = 12
```

| `i` | `n % i` | Small Divisor | Large Divisor | `result` | `large` |
|----:|--------:|--------------:|--------------:|----------|---------|
| 1 | 0 | 1 | 12 | `[1]` | `[12]` |
| 2 | 0 | 2 | 6 | `[1, 2]` | `[12, 6]` |
| 3 | 0 | 3 | 4 | `[1, 2, 3]` | `[12, 6, 4]` |

After reversing the order of `large`:

```text
4, 6, 12
```

Final result:

```text
[1, 2, 3, 4, 6, 12]
```

---

# Important Case: Perfect Square

Suppose:

```text
n = 16
```

When:

```text
i = 4
```

we get:

```text
16 / 4 = 4
```

Here:

```text
i == n / i
```

So `4` should only be added once.

That is why the code checks:

```text
if (i != n / i)
```

Without this condition, a perfect square would contain a duplicate divisor.

For example, the correct divisors of `16` are:

```text
[1, 2, 4, 8, 16]
```

not:

```text
[1, 2, 4, 4, 8, 16]
```

---

# Why This Solution Works

Every divisor pair of `n` has the form:

```text
i × (n / i) = n
```

If `i` is a divisor, then `n / i` is also a divisor.

For example, for `12`:

```text
1 × 12 = 12
2 × 6  = 12
3 × 4  = 12
```

Once we reach `√n`, all divisor pairs have already been found.

Therefore, checking only up to:

```text
i * i <= n
```

is enough to find every divisor.

The smaller divisors are collected in increasing order, while the larger divisors are collected in decreasing order and later added in reverse.

This produces the final sorted list efficiently.

---

# Time Complexity

The first loop checks values only up to `√n`.

Therefore:

```text
Number of iterations ≈ √n
```

The second loop processes the found larger divisors.

The overall time complexity is:

**Time Complexity: O(√n)**

---

# Space Complexity

The solution stores all divisors in the two lists.

The number of divisors is at most proportional to `√n` for this storage approach.

Therefore:

**Space Complexity: O(√n)**

---

# Key Takeaways

- A divisor divides a number without leaving a remainder.
- Divisors occur in pairs: `i` and `n / i`.
- We only need to check up to `√n`.
- `i * i <= n` prevents unnecessary iterations.
- `i != n / i` prevents duplicate values for perfect squares.
- Smaller divisors are stored in `result`.
- Larger divisors are stored in `large` and added in reverse order.
- The final result is returned in sorted order.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [All Divisors of a Number](https://www.geeksforgeeks.org/problems/all-divisors-of-a-number/1)
