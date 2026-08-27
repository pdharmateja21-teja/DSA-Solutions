# Reverse String

## Problem Statement

Given an array of characters `s`, reverse the array in-place.

The original array must be modified directly without creating another array.

### Example

**Input**
```text
s = ['h', 'e', 'l', 'l', 'o']
```

**Output**
```text
['o', 'l', 'l', 'e', 'h']
```

---

# Approach

We use the **Two Pointer** technique.

Two pointers are used:

- `left` starts from the first character.
- `right` starts from the last character.

At every step:

1. Swap the characters at `left` and `right`.
2. Move `left` one position forward.
3. Move `right` one position backward.
4. Continue until `left` and `right` meet or cross.

The main idea is:

```text
First ↔ Last
Second ↔ Second-Last
Third ↔ Third-Last
...
```

This reverses the array without creating another array. LeetCode specifically requires the input array to be modified in-place with `O(1)` extra memory. :contentReference[oaicite:0]{index=0}

---

# Code

```java
class Solution {
    public void reverseString(char[] s) {
        int left = 0;
        int right = s.length - 1;

        while (left < right) {
            char temp = s[left];

            s[left] = s[right];
            s[right] = temp;

            left++;
            right--;
        }
    }
}
```

---

# Understanding the Code

Suppose:

```text
s = ['h', 'e', 'l', 'l', 'o']
```

The indexes are:

```text
Index:  0    1    2    3    4
        h    e    l    l    o
        ↑              ↑
      left           right
```

Initially:

```text
left = 0
right = 4
```

The characters at these positions are:

```text
s[left]  = 'h'
s[right] = 'o'
```

They are swapped.

The array becomes:

```text
['o', 'e', 'l', 'l', 'h']
```

Then both pointers move toward the center:

```text
left++
right--
```

So:

```text
left = 1
right = 3
```

The process continues until the pointers meet.

---

# Iteration 1

```text
left = 0
right = 4
```

Characters:

```text
s[0] = 'h'
s[4] = 'o'
```

Swap:

```text
'h' ↔ 'o'
```

Array becomes:

```text
['o', 'e', 'l', 'l', 'h']
```

Move pointers:

```text
left = 1
right = 3
```

---

# Iteration 2

```text
left = 1
right = 3
```

Characters:

```text
s[1] = 'e'
s[3] = 'l'
```

Swap:

```text
'e' ↔ 'l'
```

Array becomes:

```text
['o', 'l', 'l', 'e', 'h']
```

Move pointers:

```text
left = 2
right = 2
```

---

# Iteration 3

Now:

```text
left = 2
right = 2
```

Check:

```text
left < right
2 < 2
```

This is false.

Therefore, the loop stops.

The middle character does not need to be moved.

Final array:

```text
['o', 'l', 'l', 'e', 'h']
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
s = ['h', 'e', 'l', 'l', 'o']
```

### Initial State

```text
left = 0
right = 4
```

Array:

```text
['h', 'e', 'l', 'l', 'o']
```

---

### Step 1

Swap:

```text
s[0] ↔ s[4]
```

```text
'h' ↔ 'o'
```

Array:

```text
['o', 'e', 'l', 'l', 'h']
```

Move:

```text
left = 1
right = 3
```

---

### Step 2

Swap:

```text
s[1] ↔ s[3]
```

```text
'e' ↔ 'l'
```

Array:

```text
['o', 'l', 'l', 'e', 'h']
```

Move:

```text
left = 2
right = 2
```

---

### Step 3

Check:

```text
left < right
2 < 2
```

False.

Loop ends.

Final result:

```text
['o', 'l', 'l', 'e', 'h']
```

---

# Dry Run

| Iteration | `left` | `right` | Characters Swapped | Current Array |
|----------:|-------:|--------:|--------------------|---------------|
| 1 | 0 | 4 | `h ↔ o` | `['o', 'e', 'l', 'l', 'h']` |
| 2 | 1 | 3 | `e ↔ l` | `['o', 'l', 'l', 'e', 'h']` |
| 3 | 2 | 2 | No swap | `['o', 'l', 'l', 'e', 'h']` |

Final output:

```text
['o', 'l', 'l', 'e', 'h']
```

---

# Understanding the Two Pointers

The two pointers start from opposite ends:

```text
['h', 'e', 'l', 'l', 'o']
   ↑                 ↑
 left              right
```

After the first swap:

```text
['o', 'e', 'l', 'l', 'h']
        ↑       ↑
      left    right
```

After the second swap:

```text
['o', 'l', 'l', 'e', 'h']
             ↑
           middle
```

The pointers move toward each other after every swap.

This is a common **opposite-direction two-pointer pattern**. :contentReference[oaicite:1]{index=1}

---

# Understanding the Swap

The following code:

```java
char temp = s[left];

s[left] = s[right];
s[right] = temp;
```

swaps the two characters.

For example:

```text
left character  = 'h'
right character = 'o'
```

First:

```text
temp = 'h'
```

Then:

```text
s[left] = 'o'
```

Finally:

```text
s[right] = 'h'
```

So:

```text
['h', ..., 'o']
```

becomes:

```text
['o', ..., 'h']
```

The temporary variable prevents the original value from being lost.

---

# Why This Solution Works

To reverse an array, every character needs to move to its opposite position.

For example:

```text
h e l l o
```

The required positions are:

```text
h → last
o → first

e → second-last
l → second
```

The two-pointer approach performs exactly these swaps:

```text
h ↔ o
e ↔ l
```

The middle character does not need to move.

Therefore:

```text
['h', 'e', 'l', 'l', 'o']
```

becomes:

```text
['o', 'l', 'l', 'e', 'h']
```

---

# Why `while(left < right)` Is Used

The condition is:

```java
while (left < right)
```

We only need to swap while the pointers are on different sides.

When:

```text
left == right
```

both pointers point to the same middle character, so there is nothing to swap.

If:

```text
left > right
```

the pointers have already crossed, meaning all required swaps are complete.

Therefore:

```text
left < right
```

is enough to process every required pair exactly once.

---

# In-Place Modification

The problem requires the input array to be modified directly rather than creating another array. :contentReference[oaicite:2]{index=2}

This solution uses:

```text
char temp
```

only for swapping two characters.

It does not create another array.

Therefore, the reversal is performed **in-place**.

---

# Time Complexity

For every pair of characters, one swap is performed.

Approximately half of the characters are processed:

```text
n / 2
```

Ignoring the constant factor:

**Time Complexity: O(n)**

---

# Space Complexity

Only a few variables are used:

```text
left
right
temp
```

No additional array or data structure is created.

Therefore:

**Space Complexity: O(1)**

This satisfies the problem's `O(1)` extra-memory requirement. :contentReference[oaicite:3]{index=3}

---

# Approach Evaluation

The provided approach is **correct and optimal**.

It uses:

- Two pointers.
- In-place swapping.
- A single traversal from both ends.
- `O(n)` time.
- `O(1)` extra space.

This is the standard optimal approach for this problem. :contentReference[oaicite:4]{index=4}

---

# Key Takeaways

- Use two pointers moving from opposite directions.
- `left` starts at `0`.
- `right` starts at `s.length - 1`.
- Swap the characters at both pointers.
- Move `left` forward and `right` backward.
- Stop when `left >= right`.
- The array is modified in-place.
- No additional array is required.
- Time Complexity is `O(n)`.
- Space Complexity is `O(1)`.
- This is a fundamental example of the **two-pointer technique**.

---

## 🔗 Problem Source

**Platform:** LeetCode

**Problem:** [Reverse String](https://leetcode.com/problems/reverse-string/)
