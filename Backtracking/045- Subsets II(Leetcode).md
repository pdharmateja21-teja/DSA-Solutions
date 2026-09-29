# Subsets II

## Problem Statement

Given an integer array `nums` that may contain duplicate elements, return all possible subsets while ensuring that the final result does **not contain duplicate subsets**.

For example:

```text
Input:
nums = [1, 2, 2]
```

The possible unique subsets are:

```text
[]
[1]
[2]
[1, 2]
[2, 2]
[1, 2, 2]
```

The subset `[2]` should appear only once even though there are two `2`s in the input.

---

# Approach

This solution uses **sorting, recursion, and backtracking**.

The main idea is to sort the array first:

```text
Arrays.sort(nums);
```

Sorting places duplicate values next to each other.

For example:

```text
[2, 1, 2]
```

becomes:

```text
[1, 2, 2]
```

This makes it possible to identify duplicate choices during backtracking.

The important condition is:

```text
if (i > start && nums[i] == nums[i - 1]) {
    continue;
}
```

This skips a duplicate element **when it appears at the same recursion level**.

It does **not** prevent the same value from being selected at a deeper recursion level.

For example, with:

```text
[1, 2, 2]
```

the subset:

```text
[2, 2]
```

must still be allowed.

So the solution follows this process:

1. Sort the array.
2. Start backtracking from index `0`.
3. Add the current subset to the result.
4. Iterate through the available elements.
5. Skip duplicate values at the same recursion level.
6. Choose the current element.
7. Recursively process the remaining elements.
8. Remove the chosen element to backtrack.

---

# Code

```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);

        List<List<Integer>> result = new ArrayList<>();

        backtrack(nums, 0, new ArrayList<>(), result);

        return result;
    }

    public void backtrack(int[] nums, int start, List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current));

        for (int i = start; i < nums.length; i++) {
            if (i > start && nums[i] == nums[i - 1]) {
                continue;
            }

            current.add(nums[i]);

            backtrack(nums, i + 1, current, result);

            current.remove(current.size() - 1);
        }
    }
}
```

---

# Understanding the Code

## 1. Sort the Array

```text
Arrays.sort(nums);
```

This is the first important step.

Suppose:

```text
nums = [2, 1, 2]
```

After sorting:

```text
nums = [1, 2, 2]
```

Now the duplicate `2`s are next to each other.

This allows the backtracking loop to detect duplicates easily.

---

## 2. Create the Result List

```text
List<List<Integer>> result = new ArrayList<>();
```

This stores all unique subsets.

---

## 3. Start Backtracking

```text
backtrack(nums, 0, new ArrayList<>(), result);
```

The recursion starts with:

```text
start = 0
current = []
```

So initially:

```text
current = []
```

---

## 4. Add the Current Subset

At the beginning of every recursive call:

```text
result.add(new ArrayList<>(current));
```

The current subset is immediately added to the result.

This is important because **every state of `current` represents a valid subset**.

Initially:

```text
current = []
```

so:

```text
[]
```

is added.

Later:

```text
current = [1]
```

so `[1]` is added.

And so on.

---

# Understanding the For Loop

The main exploration happens here:

```text
for (int i = start; i < nums.length; i++)
```

The loop considers every available element from `start` onward.

For each element, the algorithm has the choice to:

```text
Take the element
```

and recursively explore all possibilities after taking it.

---

# Duplicate Handling

The most important line is:

```text
if (i > start && nums[i] == nums[i - 1]) {
    continue;
}
```

Let's understand it carefully.

Suppose:

```text
nums = [1, 2, 2]
```

At a particular recursion level, we may have:

```text
i = 1 → nums[i] = 2
i = 2 → nums[i] = 2
```

Both values are the same.

If we use both as starting choices at the **same recursion level**, they would generate duplicate subsets.

Therefore, when:

```text
i > start
```

and:

```text
nums[i] == nums[i - 1]
```

the second duplicate is skipped.

---

# Why `i > start` Is Important

This condition is extremely important:

```text
i > start
```

It means:

> Skip duplicates only when they occur at the same recursion level.

It does **not** mean that duplicate values can never be selected.

For example:

```text
nums = [1, 2, 2]
```

The subset:

```text
[2, 2]
```

is valid and must be generated.

When the first `2` is selected, recursion moves to the next index:

```text
start = 2
```

At that deeper level, the second `2` can be selected.

Therefore:

```text
[2, 2]
```

is correctly included.

---

# Recursion and Backtracking Flow

Consider:

```text
nums = [1, 2, 2]
```

The recursion begins with:

```text
[]
```

The decision tree can be visualized as:

```text
                         []
                    /     |     \
                  [1]    [2]    skip 2
                 /   \      \
            [1,2]  [1,2,2] [2,2]
              |
           [1,2,2]

```

The duplicate `2` at the same level is skipped, preventing duplicate branches.

The important distinction is:

```text
Same level:
2 → duplicate 2 → skip

Deeper level:
2 → another 2 → allowed
```

---

# Detailed Code Flow

Consider:

```text
nums = [1, 2, 2]
```

After sorting:

```text
[1, 2, 2]
```

Initially:

```text
start = 0
current = []
```

The empty subset is added:

```text
[]
```

---

## Step 1 — Choose `1`

The loop starts with:

```text
i = 0
nums[i] = 1
```

Add `1`:

```text
current = [1]
```

Then:

```text
backtrack(nums, 1, current, result);
```

The subset `[1]` is added.

---

## Step 2 — Choose the First `2`

Inside the recursive call:

```text
start = 1
```

The first available `2` is at:

```text
i = 1
```

Since:

```text
i == start
```

the duplicate condition is false.

So `2` is selected:

```text
current = [1, 2]
```

The recursion continues.

---

## Step 3 — Choose the Second `2`

Now:

```text
start = 2
```

The second `2` is available.

It is selected:

```text
current = [1, 2, 2]
```

The result contains:

```text
[1, 2, 2]
```

After returning, the last `2` is removed:

```text
current = [1, 2]
```

This is the backtracking step.

---

## Step 4 — Backtrack From the First `2`

After completing all possibilities starting with the first `2`, it is removed:

```text
current = [1]
```

Now the loop at this recursion level reaches the second `2`.

Here:

```text
i > start
```

and:

```text
nums[i] == nums[i - 1]
```

are both true.

Therefore:

```text
continue;
```

is executed.

The second `2` is skipped at this level.

This prevents duplicate subsets such as another `[1, 2]`.

---

## Step 5 — Backtrack From `1`

After all subsets beginning with `1` are generated:

```text
current = []
```

The recursion returns to the root level.

Now the first `2` is selected:

```text
current = [2]
```

The subset `[2]` is added.

From here, the second `2` is allowed because the recursion has moved deeper:

```text
start = 2
```

Therefore:

```text
current = [2, 2]
```

is generated.

---

# Complete Result

For:

```text
nums = [1, 2, 2]
```

the algorithm generates:

```text
[]
[1]
[1, 2]
[1, 2, 2]
[2]
[2, 2]
```

Every subset is unique.

---

# Dry Run

For:

```text
nums = [1, 2, 2]
```

| Step | `start` | `i` | `current`   | Action             |
| ---: | ------: | --: | ----------- | ------------------ |
|    1 |       0 |   — | `[]`        | Add subset         |
|    2 |       0 |   0 | `[1]`       | Choose `1`         |
|    3 |       1 |   1 | `[1, 2]`    | Choose first `2`   |
|    4 |       2 |   2 | `[1, 2, 2]` | Choose second `2`  |
|    5 |       3 |   — | `[1, 2, 2]` | Add subset         |
|    6 |       2 |   — | `[1, 2]`    | Backtrack          |
|    7 |       1 |   2 | `[1]`       | Skip duplicate `2` |
|    8 |       0 |   1 | `[2]`       | Choose first `2`   |
|    9 |       2 |   2 | `[2, 2]`    | Choose second `2`  |
|   10 |       3 |   — | `[2, 2]`    | Add subset         |
|   11 |       1 |   — | `[]`        | Backtrack          |

Final result:

```text
[
    [],
    [1],
    [1, 2],
    [1, 2, 2],
    [2],
    [2, 2]
]
```

---

# Why This Solution Works

Sorting places equal values next to each other.

The condition:

```text
i > start && nums[i] == nums[i - 1]
```

then detects when the same value would be chosen again at the same recursion level.

That duplicate choice is skipped.

However, once the first occurrence has been selected and recursion moves to a deeper level, another equal value can still be selected.

This is why:

```text
[2, 2]
```

is allowed while duplicate copies of:

```text
[2]
```

are avoided.

The combination of **sorting + same-level duplicate skipping + backtracking** generates every unique subset exactly once.

---

# Approach Evaluation

**Approach Type:** Sorting + Recursion + Backtracking

This is a correct backtracking approach for the Subsets II problem.

The key improvement over the basic Subsets approach is the duplicate-handling condition:

```text
if (i > start && nums[i] == nums[i - 1])
```

Sorting is necessary for this particular duplicate-skipping strategy because equal elements need to be adjacent.

The solution preserves duplicate values when they form a genuinely different subset, such as `[2, 2]`, while avoiding duplicate branches at the same recursion level.

---

# Time Complexity

There can be up to:

```text
2^N
```

possible subsets in the worst case when all elements are distinct.

Each generated subset can contain up to `N` elements, and a copy is created when adding it to `result`.

Therefore:

**Time Complexity: O(N × 2^N)**

Additionally, sorting takes:

```text
O(N log N)
```

So the overall complexity is dominated by subset generation:

**Overall Time Complexity: O(N × 2^N)**

---

# Space Complexity

The output can contain up to `2^N` subsets, with each subset containing up to `N` elements:

```text
O(N × 2^N)
```

The recursion depth and current subset require:

```text
O(N)
```

Therefore:

**Output Space: O(N × 2^N)**

**Auxiliary Space: O(N)**

---

# Key Takeaways

* Sort the array first so duplicate values become adjacent.
* Use recursion and backtracking to generate subsets.
* Add the current subset at every recursive call.
* `current.add()` chooses an element.
* Recursive call explores all possibilities after that choice.
* `current.remove()` performs the backtracking step.
* `i > start` ensures duplicate skipping happens only at the same recursion level.
* `nums[i] == nums[i - 1]` detects adjacent duplicate values.
* Duplicate branches are skipped, but valid subsets such as `[2, 2]` are still allowed.
* Time Complexity: **O(N × 2^N)** in the worst case.
* Output Space: **O(N × 2^N)**
* Auxiliary Space: **O(N)**

---

## 🔗 Problem Source

**Platform:** LeetCode

**Problem:** [Subsets II](https://leetcode.com/problems/subsets-ii/)
