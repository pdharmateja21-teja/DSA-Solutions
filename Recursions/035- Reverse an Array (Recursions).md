# Reverse an Array

## Problem Statement

Given an array of integers, reverse the elements of the array.

The reversal should be performed **in-place**, meaning the original array should be modified without creating another array.

This solution uses **recursion** to understand how recursive calls can be used to reverse an array.

### Example

**Input**
```text
arr = [1, 2, 3, 4, 5]
```

**Output**
```text
[5, 4, 3, 2, 1]
```

---

# Approach

We use two pointers:

- `left` starts from the beginning of the array.
- `right` starts from the end of the array.

At every recursive call:

1. Compare `left` and `right`.
2. If `left >= right`, stop the recursion.
3. Swap the elements at `left` and `right`.
4. Move `left` one position forward.
5. Move `right` one position backward.
6. Repeat until the pointers meet or cross.

The main idea is:

```text
Swap first and last
        ↓
Move inward
        ↓
Swap second and second-last
        ↓
Move inward
        ↓
Continue until the middle
```

---

# Code

```java
class Solution {
    static void reverse(int[] arr, int left, int right) {
        if (left >= right) {
            return;
        }

        int temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;

        reverse(arr, left + 1, right - 1);
    }

    public void reverseArray(int arr[]) {
        reverse(arr, 0, arr.length - 1);
    }
}
```

---

# Understanding the Code

Suppose:

```text
arr = [1, 2, 3, 4, 5]
```

The `reverseArray()` method starts the recursion with:

```text
left = 0
right = 4
```

So the first recursive call is:

```text
reverse(arr, 0, 4)
```

The elements at these positions are:

```text
arr[0] = 1
arr[4] = 5
```

They are swapped.

Array becomes:

```text
[5, 2, 3, 4, 1]
```

Then the recursive call becomes:

```text
reverse(arr, 1, 3)
```

The process continues toward the center.

---

# Recursive Call 1

```text
left = 0
right = 4
```

Compare:

```text
left >= right
0 >= 4
```

False.

Swap:

```text
arr[0] = 1
arr[4] = 5
```

After swapping:

```text
[5, 2, 3, 4, 1]
```

Next call:

```text
reverse(arr, 1, 3)
```

---

# Recursive Call 2

```text
left = 1
right = 3
```

Compare:

```text
1 >= 3
```

False.

Swap:

```text
arr[1] = 2
arr[3] = 4
```

After swapping:

```text
[5, 4, 3, 2, 1]
```

Next call:

```text
reverse(arr, 2, 2)
```

---

# Recursive Call 3

```text
left = 2
right = 2
```

Now:

```text
left >= right
2 >= 2
```

is true.

Therefore:

```text
return;
```

The recursion stops.

The middle element does not need to be swapped because it is already in its correct position.

Final array:

```text
[5, 4, 3, 2, 1]
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
arr = [1, 2, 3, 4, 5]
```

Initial call:

```text
reverse(arr, 0, 4)
```

---

### Step 1

```text
left = 0
right = 4
```

Swap:

```text
1 ↔ 5
```

Array:

```text
[5, 2, 3, 4, 1]
```

Next:

```text
left = 1
right = 3
```

---

### Step 2

```text
left = 1
right = 3
```

Swap:

```text
2 ↔ 4
```

Array:

```text
[5, 4, 3, 2, 1]
```

Next:

```text
left = 2
right = 2
```

---

### Step 3

```text
left = 2
right = 2
```

Since:

```text
left >= right
```

the recursion stops.

Final result:

```text
[5, 4, 3, 2, 1]
```

---

# Dry Run

| Call | `left` | `right` | Elements Swapped | Array |
|-----:|-------:|--------:|------------------|-------|
| 1 | 0 | 4 | `1 ↔ 5` | `[5, 2, 3, 4, 1]` |
| 2 | 1 | 3 | `2 ↔ 4` | `[5, 4, 3, 2, 1]` |
| 3 | 2 | 2 | No swap | `[5, 4, 3, 2, 1]` |

Final output:

```text
[5, 4, 3, 2, 1]
```

---

# Understanding `left` and `right`

The two variables control which elements need to be swapped.

Initially:

```text
left = 0
right = arr.length - 1
```

For:

```text
[1, 2, 3, 4, 5]
```

we have:

```text
left → 1  2  3  4  5 ← right
```

After the first swap:

```text
5  2  3  4  1
   ↑        ↑
 left      right
```

Then the pointers move inward:

```text
5  2  3  4  1
   ↑     ↑
 left   right
```

After the second swap:

```text
5  4  3  2  1
      ↑
    middle
```

The pointers meet at the middle, so the recursion stops.

---

# Understanding the Base Case

The base condition is:

```java
if (left >= right) {
    return;
}
```

This condition handles two situations.

### When `left == right`

There is only one element remaining in the middle.

Example:

```text
left = 2
right = 2
```

No swap is required.

### When `left > right`

The pointers have crossed each other.

This means every required pair has already been swapped.

Therefore, the recursion must stop.

---

# Why This Solution Works

To reverse an array, the first element must move to the last position, and the last element must move to the first position.

The solution performs exactly this operation:

```text
arr[left] ↔ arr[right]
```

Then it moves both pointers toward the center:

```text
left + 1
right - 1
```

For:

```text
[1, 2, 3, 4, 5]
```

the swaps are:

```text
1 ↔ 5
2 ↔ 4
```

The middle element `3` remains unchanged.

Therefore:

```text
[1, 2, 3, 4, 5]
```

becomes:

```text
[5, 4, 3, 2, 1]
```

---

# Recursion Flow

The recursive calls move toward the center:

```text
reverse(0, 4)
      ↓
reverse(1, 3)
      ↓
reverse(2, 2)
      ↓
return
```

Each call handles one pair of elements.

This demonstrates an important recursion pattern:

```text
Solve the outer part
        ↓
Move toward the smaller problem
        ↓
Repeat
        ↓
Stop at the base case
```

---

# Why No Extra Array Is Required

The solution modifies the original array directly.

For example:

```text
arr[left] = arr[right]
arr[right] = arr[left]
```

using a temporary variable for the swap.

No second array is created.

Therefore, the reversal is performed **in-place**.

---

# Time Complexity

Each element is involved in at most one swap.

The recursion processes approximately half of the array.

Therefore:

**Time Complexity: O(n)**

---

# Space Complexity

The array itself does not require additional space.

However, recursive calls are stored in the call stack.

There are approximately `n / 2` recursive calls.

Ignoring constant factors:

**Space Complexity: O(n)**

---

# Key Takeaways

- Two pointers are used: `left` and `right`.
- `left` starts from the beginning.
- `right` starts from the end.
- The elements at both pointers are swapped.
- Both pointers move toward the center after every swap.
- `left >= right` is the base case.
- The array is reversed in-place.
- The solution demonstrates how recursion can be used with the two-pointer technique.
- Time Complexity is `O(n)`.
- Space Complexity is `O(n)` because of the recursion call stack.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Reverse an Array](https://www.geeksforgeeks.org/problems/reverse-an-array/1)
