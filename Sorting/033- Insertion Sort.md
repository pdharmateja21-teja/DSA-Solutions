# Insertion Sort

## Problem Statement

Given an array of integers, sort the array in ascending order using the **Insertion Sort** technique.

Insertion Sort works by dividing the array into two parts:

- A sorted portion on the left.
- An unsorted portion on the right.

At each step, take one element from the unsorted portion and insert it into its correct position in the sorted portion.

### Example

**Input**
```text
arr = [5, 3, 4, 1, 2]
```

**Output**
```text
[1, 2, 3, 4, 5]
```

---

# Approach

We use **Insertion Sort** to sort the array in-place.

The steps are:

1. Start from the first element.
2. Consider the current element as the `key`.
3. Compare the `key` with the elements before it.
4. If an element is greater than the `key`, shift it one position to the right.
5. Continue shifting until the correct position for the `key` is found.
6. Place the `key` at that position.
7. Repeat the process for all elements.

The important idea is:

```text
Take → Compare → Shift → Insert
```

---

# Code

```java
class Solution {
    public void insertionSort(int arr[]) {
        int n = arr.length;

        for (int i = 1; i < n; i++) {
            int key = arr[i];
            int j = i - 1;

            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j--;
            }

            arr[j + 1] = key;
        }
    }
}
```

---

# Understanding the Code

Suppose:

```text
arr = [5, 3, 4, 1, 2]
```

Initially, the first element:

```text
5
```

is considered sorted.

So we start from:

```text
i = 1
```

The current element becomes the `key`.

The goal is to insert the `key` into the correct position among the elements before it.

---

# Iteration 1

```text
i = 1
key = arr[1] = 3
j = 0
```

Current array:

```text
[5, 3, 4, 1, 2]
```

Compare:

```text
arr[0] = 5
key = 3
```

Since:

```text
5 > 3
```

shift `5` one position to the right:

```text
[5, 5, 4, 1, 2]
```

Then:

```text
j--
```

So:

```text
j = -1
```

Now place the key at:

```text
arr[j + 1]
= arr[0]
= 3
```

Array becomes:

```text
[3, 5, 4, 1, 2]
```

The first two elements are now sorted.

---

# Iteration 2

```text
i = 2
key = arr[2] = 4
j = 1
```

Current array:

```text
[3, 5, 4, 1, 2]
```

Compare:

```text
arr[1] = 5
key = 4
```

Since:

```text
5 > 4
```

shift `5`:

```text
[3, 5, 5, 1, 2]
```

Move `j` backward:

```text
j = 0
```

Now compare:

```text
arr[0] = 3
key = 4
```

Since:

```text
3 > 4
```

is false, stop shifting.

Place the key at:

```text
arr[j + 1]
= arr[1]
= 4
```

Array becomes:

```text
[3, 4, 5, 1, 2]
```

The first three elements are now sorted.

---

# Iteration 3

```text
i = 3
key = arr[3] = 1
j = 2
```

Current array:

```text
[3, 4, 5, 1, 2]
```

Compare `5` with `1`:

```text
5 > 1
```

Shift:

```text
[3, 4, 5, 5, 2]
```

Then:

```text
j = 1
```

Compare `4` with `1`:

```text
4 > 1
```

Shift:

```text
[3, 4, 4, 5, 2]
```

Then:

```text
j = 0
```

Compare `3` with `1`:

```text
3 > 1
```

Shift:

```text
[3, 3, 4, 5, 2]
```

Then:

```text
j = -1
```

Place the key at:

```text
arr[0] = 1
```

Array becomes:

```text
[1, 3, 4, 5, 2]
```

---

# Iteration 4

```text
i = 4
key = arr[4] = 2
j = 3
```

Current array:

```text
[1, 3, 4, 5, 2]
```

Compare `5` with `2`:

```text
5 > 2
```

Shift:

```text
[1, 3, 4, 5, 5]
```

Then:

```text
j = 2
```

Compare `4` with `2`:

```text
4 > 2
```

Shift:

```text
[1, 3, 4, 4, 5]
```

Then:

```text
j = 1
```

Compare `3` with `2`:

```text
3 > 2
```

Shift:

```text
[1, 3, 3, 4, 5]
```

Then:

```text
j = 0
```

Compare:

```text
1 > 2
```

is false.

Place the key at:

```text
arr[1] = 2
```

Final array:

```text
[1, 2, 3, 4, 5]
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
arr = [5, 3, 4, 1, 2]
```

### Initial State

```text
[5, 3, 4, 1, 2]
```

---

### Iteration 1

```text
key = 3
```

Shift `5`:

```text
[3, 5, 4, 1, 2]
```

---

### Iteration 2

```text
key = 4
```

Shift `5`:

```text
[3, 4, 5, 1, 2]
```

---

### Iteration 3

```text
key = 1
```

Shift:

```text
5 → 4 → 3
```

Result:

```text
[1, 3, 4, 5, 2]
```

---

### Iteration 4

```text
key = 2
```

Shift:

```text
5 → 4 → 3
```

Result:

```text
[1, 2, 3, 4, 5]
```

Final result:

```text
[1, 2, 3, 4, 5]
```

---

# Dry Run

| Iteration | `key` | Elements Shifted | Array After Insertion |
|----------:|------:|------------------|-----------------------|
| 1 | 3 | `5` | `[3, 5, 4, 1, 2]` |
| 2 | 4 | `5` | `[3, 4, 5, 1, 2]` |
| 3 | 1 | `5, 4, 3` | `[1, 3, 4, 5, 2]` |
| 4 | 2 | `5, 4, 3` | `[1, 2, 3, 4, 5]` |

Final output:

```text
[1, 2, 3, 4, 5]
```

---

# Understanding `key`

The variable:

```java
int key = arr[i];
```

stores the element that we currently want to place in its correct position.

For example:

```text
arr = [3, 5, 4, 1, 2]
```

When:

```text
i = 2
```

we have:

```text
key = 4
```

The elements before it are:

```text
3, 5
```

We compare `4` with `5`.

Since:

```text
5 > 4
```

we shift `5` to the right.

Then `4` is inserted between `3` and `5`:

```text
[3, 4, 5, 1, 2]
```

---

# Understanding `j`

The variable:

```java
int j = i - 1;
```

starts from the element immediately before the `key`.

The loop:

```java
while (j >= 0 && arr[j] > key)
```

moves backward through the sorted portion.

Whenever:

```text
arr[j] > key
```

the larger element is shifted one position to the right:

```text
arr[j + 1] = arr[j]
```

After finding the correct position, the key is inserted using:

```text
arr[j + 1] = key
```

---

# Why This Solution Works

At every iteration, all elements before `i` are already sorted.

The current element is stored as `key`.

Any element greater than `key` is shifted one position to the right.

This creates an empty position where the `key` can be inserted.

Therefore, after every iteration, the sorted portion becomes one element larger.

Eventually, the entire array becomes sorted.

The main idea is:

```text
Sorted portion | Unsorted portion
```

For example:

```text
[3, 4, 5 | 1, 2]
```

Take:

```text
key = 1
```

Insert it into the sorted portion:

```text
[1, 3, 4, 5 | 2]
```

Then take:

```text
key = 2
```

and insert it:

```text
[1, 2, 3, 4, 5]
```

---

# Important Insertion Sort Concept

Insertion Sort does not repeatedly swap the key with every element.

Instead, it:

```text
1. Stores the key.
2. Shifts larger elements to the right.
3. Inserts the key into the empty position.
```

For example:

```text
[3, 5, 4]
```

Take:

```text
key = 4
```

Shift:

```text
[3, 5, 5]
```

Then insert:

```text
[3, 4, 5]
```

This shifting process is the main idea behind Insertion Sort.

---

# Time Complexity

In the worst case, every element may need to be compared with and shifted past many previous elements.

For example, a reverse-sorted array:

```text
[5, 4, 3, 2, 1]
```

requires many shifts.

**Worst-case Time Complexity: O(n²)**

For an already sorted array, the inner `while` condition fails immediately for each element.

**Best-case Time Complexity: O(n)**

---

# Space Complexity

The algorithm sorts the array in-place and uses only a few variables such as:

```text
key
j
n
```

No additional array is created.

Therefore:

**Space Complexity: O(1)**

---

# Key Takeaways

- Insertion Sort maintains a sorted portion on the left.
- The current element is stored in `key`.
- Larger elements are shifted to the right.
- The `key` is then inserted into its correct position.
- `j` moves backward through the sorted portion.
- The algorithm sorts the array in-place.
- Best-case time complexity is `O(n)`.
- Worst-case time complexity is `O(n²)`.
- Space complexity is `O(1)`.
- The core idea is **take, shift, and insert**.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Insertion Sort](https://www.geeksforgeeks.org/problems/insertion-sort/1)
