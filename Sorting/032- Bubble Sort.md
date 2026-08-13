# Bubble Sort

## Problem Statement

Given an array of integers, sort the array in ascending order using the Bubble Sort technique.

Bubble Sort repeatedly compares elements and places smaller elements toward the beginning of the array by swapping elements when they are in the wrong order.

### Example

**Input**
```text
arr = [5, 1, 4, 2, 8]
```

**Output**
```text
[1, 2, 4, 5, 8]
```

---

# Approach

The given solution uses repeated comparisons and swaps to arrange the array in ascending order.

The steps are:

1. Start from the first element.
2. Compare `arr[i]` with every element after it.
3. If `arr[i]` is greater than `arr[j]`, swap them.
4. Continue until all elements are in ascending order.

For example:

```text
[5, 1, 4, 2, 8]
```

When `5` is compared with `1`, they are in the wrong order, so they are swapped.

```text
[1, 5, 4, 2, 8]
```

The same process continues until the entire array is sorted.

> **Note:** The provided implementation is commonly grouped under Bubble Sort, but its inner loop compares `arr[i]` with all later elements rather than only adjacent elements. It still correctly sorts the array, but it is not the standard adjacent-swap implementation of Bubble Sort.

---

# Code

```java
class Solution {
    public void bubbleSort(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] > arr[j]) {
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
        }
    }
}
```

---

# Understanding the Code

Suppose:

```text
arr = [5, 1, 4, 2]
```

Initially:

```text
[5, 1, 4, 2]
```

The outer loop starts with:

```text
i = 0
```

So:

```text
arr[i] = 5
```

The inner loop compares `5` with every element after it.

---

## Iteration 1

```text
i = 0
j = 1
```

Compare:

```text
arr[0] = 5
arr[1] = 1
```

Since:

```text
5 > 1
```

swap them.

Array becomes:

```text
[1, 5, 4, 2]
```

---

## Iteration 2

Now:

```text
i = 0
j = 2
```

Compare:

```text
arr[0] = 1
arr[2] = 4
```

Since:

```text
1 > 4
```

is false, no swap occurs.

Array remains:

```text
[1, 5, 4, 2]
```

---

## Iteration 3

Now:

```text
i = 0
j = 3
```

Compare:

```text
arr[0] = 1
arr[3] = 2
```

Since:

```text
1 > 2
```

is false.

Array remains:

```text
[1, 5, 4, 2]
```

The first position is now correctly placed.

---

## Next Outer Iteration

Now:

```text
i = 1
```

So:

```text
arr[i] = 5
```

Compare with the elements after it.

### Compare with `4`

```text
5 > 4
```

Swap:

```text
[1, 4, 5, 2]
```

### Compare with `2`

```text
5 > 2
```

Swap:

```text
[1, 4, 2, 5]
```

Now the second position is correctly determined relative to the remaining elements.

---

## Final Outer Iteration

Now:

```text
i = 2
```

Compare:

```text
arr[2] = 2
arr[3] = 5
```

Since:

```text
2 > 5
```

is false, no swap occurs.

Final array:

```text
[1, 4, 2, 5]
```

Wait — this shows an important detail about the exact code.

The previous step demonstrates that the provided implementation does **not** produce `[1, 2, 4, 5]` for this particular array because after swapping `5` with `4`, the later comparison does not revisit the earlier position.

Therefore, the supplied code is **not a correct general sorting implementation**.

---

# Correct Understanding of the Provided Code

The condition:

```java
if (arr[i] > arr[j])
```

compares the fixed position `i` with later positions.

This approach works for some arrays, but it does not correctly sort every possible input.

For example:

```text
arr = [5, 1, 4, 2]
```

The provided code produces:

```text
[1, 4, 2, 5]
```

which is not sorted.

Therefore, the code should be corrected before considering it a valid Bubble Sort solution.

---

# Correct Bubble Sort Code

Standard Bubble Sort compares **adjacent elements** and swaps them when they are in the wrong order.

```java
class Solution {
    public void bubbleSort(int[] arr) {
        int n = arr.length;

        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
}
```

---

# Understanding Correct Bubble Sort

For:

```text
arr = [5, 1, 4, 2]
```

the first pass compares adjacent elements.

### Compare 5 and 1

```text
5 > 1
```

Swap:

```text
[1, 5, 4, 2]
```

### Compare 5 and 4

```text
5 > 4
```

Swap:

```text
[1, 4, 5, 2]
```

### Compare 5 and 2

```text
5 > 2
```

Swap:

```text
[1, 4, 2, 5]
```

At the end of the first pass:

```text
[1, 4, 2, 5]
```

The largest element, `5`, has reached the end.

---

## Second Pass

Compare:

```text
1 and 4
```

No swap.

```text
[1, 4, 2, 5]
```

Compare:

```text
4 and 2
```

Swap.

```text
[1, 2, 4, 5]
```

Now the array is sorted.

---

# Code Flow (Step-by-Step Execution)

For:

```text
arr = [5, 1, 4, 2]
```

### Pass 1

```text
[5, 1, 4, 2]
```

Compare `5` and `1`:

```text
[1, 5, 4, 2]
```

Compare `5` and `4`:

```text
[1, 4, 5, 2]
```

Compare `5` and `2`:

```text
[1, 4, 2, 5]
```

Largest element `5` is now at the end.

---

### Pass 2

```text
[1, 4, 2, 5]
```

Compare `1` and `4`:

```text
[1, 4, 2, 5]
```

Compare `4` and `2`:

```text
[1, 2, 4, 5]
```

---

### Pass 3

The remaining elements are already sorted.

Final result:

```text
[1, 2, 4, 5]
```

---

# Dry Run

| Pass | Comparison | Action | Array |
|-----:|-------------|--------|-------|
| 1 | `5 > 1` | Swap | `[1, 5, 4, 2]` |
| 1 | `5 > 4` | Swap | `[1, 4, 5, 2]` |
| 1 | `5 > 2` | Swap | `[1, 4, 2, 5]` |
| 2 | `1 > 4` | No swap | `[1, 4, 2, 5]` |
| 2 | `4 > 2` | Swap | `[1, 2, 4, 5]` |

Final result:

```text
[1, 2, 4, 5]
```

---

# Why Bubble Sort Works

Bubble Sort repeatedly compares adjacent elements.

If the left element is greater than the right element, they are swapped.

Therefore, larger elements gradually move toward the end of the array after every pass.

For example:

```text
5
```

moves rightward:

```text
[5, 1, 4, 2]
     ↓
[1, 5, 4, 2]
        ↓
[1, 4, 5, 2]
           ↓
[1, 4, 2, 5]
```

After the first pass, the largest element is at the end.

The process repeats for the remaining unsorted portion until the entire array is sorted.

---

# Time Complexity

For the standard Bubble Sort implementation:

**Worst-case Time Complexity: O(n²)**

**Average-case Time Complexity: O(n²)**

The provided implementation also uses two nested loops, so its time complexity is:

**Time Complexity: O(n²)**

---

# Space Complexity

Bubble Sort sorts the array in-place and uses only a temporary variable for swapping.

Therefore:

**Space Complexity: O(1)**

---

# Key Takeaways

- Bubble Sort repeatedly compares adjacent elements.
- If two adjacent elements are in the wrong order, they are swapped.
- After each pass, the largest remaining element moves to its correct position.
- The algorithm works directly on the original array.
- It requires `O(1)` extra space.
- Standard Bubble Sort has `O(n²)` time complexity.
- The code initially provided uses a different comparison pattern and does **not** correctly sort all arrays.
- For a correct Bubble Sort solution, adjacent elements should be compared using `arr[j]` and `arr[j + 1]`.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Bubble Sort](https://www.geeksforgeeks.org/problems/bubble-sort/1)
