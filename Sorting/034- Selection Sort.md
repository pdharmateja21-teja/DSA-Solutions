# Selection Sort

## Problem Statement

Given an array of integers, sort the array in ascending order using the **Selection Sort** technique.

Selection Sort repeatedly finds the smallest element from the unsorted portion of the array and places it at the beginning of that portion.

### Example

**Input**
```text
arr = [64, 25, 12, 22, 11]
```

**Output**
```text
[11, 12, 22, 25, 64]
```

---

# Approach

Selection Sort divides the array into two parts:

- **Sorted portion:** Elements on the left that are already in their correct positions.
- **Unsorted portion:** Remaining elements on the right.

For every position:

1. Assume the current position contains the smallest element.
2. Search the remaining unsorted portion.
3. Find the actual smallest element.
4. Store its index in `store`.
5. Swap the smallest element with the element at the current position.
6. Move to the next position.

The main idea is:

```text
Find Minimum → Swap → Expand Sorted Portion
```

---

# Code

```java
class Solution {
    void selectionSort(int[] arr) {
        int n = arr.length;

        for (int i = 0; i < n - 1; i++) {
            int store = i;

            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[store]) {
                    store = j;
                }
            }

            int temp = arr[i];
            arr[i] = arr[store];
            arr[store] = temp;
        }
    }
}
```

---

# Understanding the Code

Suppose:

```text
arr = [64, 25, 12, 22, 11]
```

Initially, no elements are considered sorted.

The outer loop starts with:

```text
i = 0
```

We assume:

```text
store = 0
```

This means we initially assume:

```text
arr[0] = 64
```

is the smallest element in the unsorted portion.

The inner loop then searches for a smaller element.

---

# Iteration 1

Current array:

```text
[64, 25, 12, 22, 11]
```

```text
i = 0
store = 0
```

Initially:

```text
arr[store] = 64
```

Now the inner loop starts.

### Compare 25

```text
arr[1] = 25
arr[store] = 64
```

Since:

```text
25 < 64
```

update:

```text
store = 1
```

---

### Compare 12

```text
arr[2] = 12
arr[store] = 25
```

Since:

```text
12 < 25
```

update:

```text
store = 2
```

---

### Compare 22

```text
arr[3] = 22
arr[store] = 12
```

Since:

```text
22 < 12
```

is false, `store` remains:

```text
2
```

---

### Compare 11

```text
arr[4] = 11
arr[store] = 12
```

Since:

```text
11 < 12
```

update:

```text
store = 4
```

The smallest element is:

```text
11
```

at index `4`.

Now swap:

```text
arr[0] ↔ arr[4]
```

Array becomes:

```text
[11, 25, 12, 22, 64]
```

The first position is now correctly sorted.

---

# Iteration 2

Now:

```text
i = 1
```

The sorted portion is:

```text
[11]
```

The unsorted portion is:

```text
[25, 12, 22, 64]
```

Initially:

```text
store = 1
```

So we assume:

```text
25
```

is the smallest.

Compare with `12`:

```text
12 < 25
```

Therefore:

```text
store = 2
```

Compare `22`:

```text
22 < 12
```

false.

Compare `64`:

```text
64 < 12
```

false.

The smallest element is `12`.

Swap:

```text
arr[1] ↔ arr[2]
```

Array becomes:

```text
[11, 12, 25, 22, 64]
```

Now the first two positions are sorted.

---

# Iteration 3

Now:

```text
i = 2
```

Current array:

```text
[11, 12, 25, 22, 64]
```

Initially:

```text
store = 2
```

So:

```text
arr[store] = 25
```

Compare `22`:

```text
22 < 25
```

Therefore:

```text
store = 3
```

Compare `64`:

```text
64 < 22
```

false.

The smallest element is `22`.

Swap:

```text
arr[2] ↔ arr[3]
```

Array becomes:

```text
[11, 12, 22, 25, 64]
```

---

# Iteration 4

Now:

```text
i = 3
```

Current array:

```text
[11, 12, 22, 25, 64]
```

Initially:

```text
store = 3
```

Compare:

```text
64 < 25
```

false.

Therefore, `store` remains `3`.

Swapping `arr[3]` with itself does not change the array.

Final array:

```text
[11, 12, 22, 25, 64]
```

The array is sorted.

---

# Code Flow (Step-by-Step Execution)

### Input

```text
arr = [64, 25, 12, 22, 11]
```

---

### Iteration 1

Find the minimum from:

```text
[64, 25, 12, 22, 11]
```

Minimum:

```text
11
```

Swap with the first element:

```text
[11, 25, 12, 22, 64]
```

---

### Iteration 2

Find the minimum from:

```text
[25, 12, 22, 64]
```

Minimum:

```text
12
```

Swap with the second element:

```text
[11, 12, 25, 22, 64]
```

---

### Iteration 3

Find the minimum from:

```text
[25, 22, 64]
```

Minimum:

```text
22
```

Swap:

```text
[11, 12, 22, 25, 64]
```

---

### Iteration 4

Find the minimum from:

```text
[25, 64]
```

Minimum:

```text
25
```

No meaningful swap is required.

Final result:

```text
[11, 12, 22, 25, 64]
```

---

# Dry Run

| Iteration | `i` | Minimum Found | `store` | Array After Swap |
|----------:|----:|--------------:|--------:|------------------|
| 1 | 0 | 11 | 4 | `[11, 25, 12, 22, 64]` |
| 2 | 1 | 12 | 2 | `[11, 12, 25, 22, 64]` |
| 3 | 2 | 22 | 3 | `[11, 12, 22, 25, 64]` |
| 4 | 3 | 25 | 3 | `[11, 12, 22, 25, 64]` |

Final output:

```text
[11, 12, 22, 25, 64]
```

---

# Understanding `store`

The variable:

```java
int store = i;
```

stores the **index of the smallest element found so far**.

For example:

```text
arr = [64, 25, 12, 22, 11]
```

At the beginning:

```text
store = 0
```

because we initially assume `64` is the smallest.

After comparing with `25`:

```text
store = 1
```

After comparing with `12`:

```text
store = 2
```

After comparing with `11`:

```text
store = 4
```

So:

```text
store = 4
```

means the smallest element is located at index `4`.

Then:

```text
arr[i]
```

is swapped with:

```text
arr[store]
```

---

# Why This Solution Works

At every iteration, the algorithm searches the entire unsorted portion for the smallest element.

Once the smallest element is found, it is swapped into the first position of that unsorted portion.

For example:

```text
[64, 25, 12, 22, 11]
 ↑
sorted position
```

The minimum is `11`, so it is placed at the first position:

```text
[11 | 25, 12, 22, 64]
```

Then the next minimum is found from:

```text
[25, 12, 22, 64]
```

and placed at the second position:

```text
[11, 12 | 25, 22, 64]
```

This continues until every element is in its correct position.

Therefore, after each outer-loop iteration, the sorted portion grows by one element.

---

# Important Selection Sort Concept

Selection Sort does not immediately swap every time it finds a smaller element.

Instead, it only updates the index:

```text
store
```

when a smaller element is found.

After searching the complete unsorted portion, it performs **one swap**.

The process is:

```text
Assume minimum
      ↓
Search remaining elements
      ↓
Update minimum index
      ↓
Finish search
      ↓
Swap minimum into position
```

This is the main idea behind Selection Sort.

---

# Time Complexity

The inner loop searches the remaining portion of the array for every position.

The number of comparisons is approximately:

```text
(n - 1) + (n - 2) + ... + 1
```

This results in:

**Time Complexity: O(n²)**

This applies to the best, average, and worst cases because Selection Sort still searches the remaining elements even when the array is already sorted.

---

# Space Complexity

The algorithm sorts the array in-place.

It uses only a few variables:

```text
store
temp
i
j
```

No additional array is created.

Therefore:

**Space Complexity: O(1)**

---

# Key Takeaways

- Selection Sort maintains a sorted portion on the left.
- `store` keeps track of the index of the smallest element.
- The inner loop searches the complete unsorted portion.
- Only after finding the minimum does the algorithm perform a swap.
- After every iteration, one element reaches its correct position.
- The algorithm sorts the array in-place.
- Time Complexity is `O(n²)`.
- Space Complexity is `O(1)`.
- The core idea is **find the minimum, then swap it into position**.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Selection Sort](https://www.geeksforgeeks.org/problems/selection-sort/1)
