# Concatenation of Array

## Problem Statement

Given an integer array `nums` of size `n`, create a new array `ans` of size `2n` such that:

- The first `n` elements of `ans` are the elements of `nums`.
- The next `n` elements of `ans` are again the elements of `nums`.

In simple words, append the original array to itself.

### Example

**Input**
```text
nums = [1, 2, 3]
```

**Output**
```text
[1, 2, 3, 1, 2, 3]
```

---

# Approach

Since the resulting array must contain the original array twice:

1. Find the size of the original array.
2. Create a new array of size `2 × n`.
3. Traverse the original array once.
4. Store each element:
   - At index `i`.
   - Again at index `i + n`.
5. Return the newly created array.

This approach copies every element exactly twice in a single traversal.

---

# Code

```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int n = nums.length;
        int[] ans = new int[2 * n];

        for (int i = 0; i < n; i++) {
            ans[i] = nums[i];
            ans[i + n] = nums[i];
        }

        return ans;
    }
}
```

---

# Understanding the Code

Suppose,

```text
nums = [1, 2, 3]

n = 3
```

Create a new array of size:

```text
2 × 3 = 6
```

Initially,

```text
ans = [_, _, _, _, _, _]
```

Now the loop starts.

---

## Iteration 1

```text
i = 0

nums[i] = 1
```

Store at

```text
ans[0] = 1
ans[0 + 3] = ans[3] = 1
```

Array becomes

```text
[1, _, _, 1, _, _]
```

---

## Iteration 2

```text
i = 1

nums[i] = 2
```

Store at

```text
ans[1] = 2
ans[4] = 2
```

Array becomes

```text
[1, 2, _, 1, 2, _]
```

---

## Iteration 3

```text
i = 2

nums[i] = 3
```

Store at

```text
ans[2] = 3
ans[5] = 3
```

Array becomes

```text
[1, 2, 3, 1, 2, 3]
```

The loop finishes.

Return

```text
[1, 2, 3, 1, 2, 3]
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
nums = [1, 2, 3]
```

### Initial State

```text
n = 3

ans = [_, _, _, _, _, _]
```

---

### Iteration 1

```text
i = 0

nums[i] = 1

ans[0] = 1
ans[3] = 1

Current ans

[1, _, _, 1, _, _]
```

---

### Iteration 2

```text
i = 1

nums[i] = 2

ans[1] = 2
ans[4] = 2

Current ans

[1, 2, _, 1, 2, _]
```

---

### Iteration 3

```text
i = 2

nums[i] = 3

ans[2] = 3
ans[5] = 3

Current ans

[1, 2, 3, 1, 2, 3]
```

Loop Ends.

Return

```text
[1, 2, 3, 1, 2, 3]
```

---

# Dry Run

| Iteration | i | nums[i] | First Copy (`ans[i]`) | Second Copy (`ans[i+n]`) | Current `ans` |
|----------:|--:|--------:|----------------------:|-------------------------:|---------------|
| 1 | 0 | 1 | ans[0] = 1 | ans[3] = 1 | [1, _, _, 1, _, _] |
| 2 | 1 | 2 | ans[1] = 2 | ans[4] = 2 | [1, 2, _, 1, 2, _] |
| 3 | 2 | 3 | ans[2] = 3 | ans[5] = 3 | [1, 2, 3, 1, 2, 3] |

---

# Why This Solution Works

- The answer array has twice the size of the original array.
- During each iteration, one element is copied into two positions:
  - The first half (`i`).
  - The second half (`i + n`).
- Since every element is copied exactly twice, the final array becomes the original array concatenated with itself.

---

# Time Complexity

The loop traverses the original array only once.

```text
Number of iterations = n
```

Therefore,

**Time Complexity: O(n)**

---

# Space Complexity

A new array of size `2n` is created to store the result.

```text
Extra Space = 2n
```

Ignoring constant factors,

**Space Complexity: O(n)**

---

# Key Takeaways

- Create a new array with double the original size.
- Copy each element twice in a single traversal.
- `ans[i]` stores the first copy.
- `ans[i + n]` stores the second copy.
- This approach is efficient because it completes the task in one pass through the original array.
