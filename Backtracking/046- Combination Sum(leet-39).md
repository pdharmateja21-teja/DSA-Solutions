# Combination Sum

## Problem Statement

Given an array `candidates` containing distinct positive integers and a target integer `target`, return all unique combinations of numbers whose sum is equal to the target.

A candidate number can be used **any number of times**.

For example:

```text
Input:
candidates = [2, 3, 6, 7]
target = 7
```

Output:

```text
[[2, 2, 3], [7]]
```

Explanation:

```text
2 + 2 + 3 = 7
7 = 7
```

The same number can be selected multiple times.

---

# Approach

This solution uses **recursion and backtracking**.

At every index, there are two choices:

1. **Take** the current element.
2. **Don't take** the current element.

The important difference from the normal Subsets problem is that an element can be used **multiple times**.

Therefore, when we take an element, we call the recursive function with the **same index**:

```text
solve(arr, index, sum + arr[index], target, current, result)
```

Instead of:

```text
index + 1
```

This allows the same candidate to be selected again.

When we don't take the element, we move to the next index:

```text
solve(arr, index + 1, sum, target, current, result)
```

The recursion stops when:

* `sum == target` → a valid combination is found.
* `index == arr.length` → no candidates are left.
* `sum > target` → the current combination has exceeded the target.

---

# Code

```java id="x7m4qa"
class Solution {

    public List<List<Integer>> combinationSum(int[] candidates, int target) {

        List<List<Integer>> result = new ArrayList<>();

        solve(candidates, 0, 0, target, new ArrayList<>(), result);

        return result;
    }

    static void solve(
            int[] arr,
            int index,
            int sum,
            int target,
            ArrayList<Integer> current,
            List<List<Integer>> result) {

        if (sum == target) {
            result.add(new ArrayList<>(current));
            return;
        }

        if (index == arr.length || sum > target) {
            return;
        }

        current.add(arr[index]);

        solve(
            arr,
            index,
            sum + arr[index],
            target,
            current,
            result
        );

        current.remove(current.size() - 1);

        solve(
            arr,
            index + 1,
            sum,
            target,
            current,
            result
        );
    }
}
```

---

# Understanding the Code

## 1. Create the Result

```text id="r1v8kc"
List<List<Integer>> result = new ArrayList<>();
```

`result` stores every valid combination whose sum equals `target`.

---

## 2. Start the Recursion

```text id="x0k2pf"
solve(candidates, 0, 0, target, new ArrayList<>(), result);
```

Initially:

```text
index = 0
sum = 0
current = []
```

For:

```text
candidates = [2, 3, 6, 7]
target = 7
```

the recursion starts from:

```text
current = []
sum = 0
index = 0
```

---

# Understanding the Base Cases

There are three important stopping conditions.

## Case 1 — Target Reached

```text id="y5r2nf"
if (sum == target) {
    result.add(new ArrayList<>(current));
    return;
}
```

If:

```text
sum == target
```

we have found a valid combination.

For example:

```text
current = [2, 2, 3]
sum = 7
```

So:

```text
[2, 2, 3]
```

is added to the result.

A copy is created using:

```text
new ArrayList<>(current)
```

because `current` continues changing during backtracking.

---

## Case 2 — No Candidates Left

```text id="v8p5sc"
if (index == arr.length)
```

If we have reached the end of the array and the target has not been reached, this path cannot produce a valid combination.

So the recursion returns.

---

## Case 3 — Sum Exceeds Target

```text id="c5y2r7"
if (sum > target)
```

All candidates are positive integers, so once the sum becomes greater than the target, adding more numbers cannot bring it back down.

Therefore, the current branch can be stopped immediately.

---

# TAKE Choice

The first decision is:

```text id="c2z3rx"
current.add(arr[index]);
```

This means:

> Select the current candidate.

Suppose:

```text
index = 0
arr[index] = 2
current = []
```

After taking `2`:

```text
current = [2]
sum = 2
```

---

# Why the Same Index Is Used

After taking the current element, the code calls:

```text id="7p8n3m"
solve(arr, index, sum + arr[index], target, current, result);
```

Notice:

```text
index
```

is used again.

It is **not**:

```text
index + 1
```

This is the key idea of Combination Sum.

Because the same number can be used unlimited times.

For example:

```text
[2]
```

can become:

```text
[2, 2]
```

then:

```text
[2, 2, 2]
```

and so on until the target is reached or exceeded.

---

# BACKTRACKING

After completely exploring the TAKE branch:

```text id="zq1t9b"
current.remove(current.size() - 1);
```

This removes the last selected number.

For example:

```text
current = [2, 2, 2]
```

After backtracking:

```text
current = [2, 2]
```

Now the algorithm can explore another possibility.

The basic pattern is:

```text
Choose
   ↓
Explore
   ↓
Undo choice
   ↓
Explore another choice
```

---

# DON'T TAKE Choice

After removing the selected element, the algorithm executes:

```text id="q6c4zv"
solve(arr, index + 1, sum, target, current, result);
```

This means:

> Do not use the current candidate and move to the next candidate.

For example, if:

```text
index = 0
arr[index] = 2
```

the DON'T TAKE branch moves to:

```text
index = 1
```

which represents candidate:

```text
3
```

---

# Detailed Example

Consider:

```text
candidates = [2, 3, 6, 7]
target = 7
```

The recursion begins with:

```text
index = 0
sum = 0
current = []
```

---

## Step 1 — Take `2`

```text
current = [2]
sum = 2
index = 0
```

Because the same number can be reused, the recursion stays at:

```text
index = 0
```

---

## Step 2 — Take `2` Again

```text
current = [2, 2]
sum = 4
index = 0
```

Again, the same `2` can be used.

---

## Step 3 — Take `2` Again

```text
current = [2, 2, 2]
sum = 6
index = 0
```

Taking another `2` would produce:

```text
sum = 8
```

which is greater than `7`.

Therefore, that branch stops.

---

## Step 4 — Don't Take More `2`s

After backtracking, the algorithm moves to the next candidate:

```text
index = 1
arr[index] = 3
```

The current combination is:

```text
current = [2, 2]
sum = 4
```

Take `3`:

```text
current = [2, 2, 3]
sum = 7
```

Now:

```text
sum == target
```

So:

```text
[2, 2, 3]
```

is added to the result.

---

## Step 5 — Backtrack

The `3` is removed:

```text
current = [2, 2]
```

The algorithm continues exploring other possibilities.

Eventually, it backtracks further and explores:

```text
[7]
```

When:

```text
current = [7]
sum = 7
```

that combination is also added.

---

# Recursion Flow

The important part of the recursion can be visualized as:

```text
                         []
                    /          \
                 TAKE          DON'T TAKE
                  2                |
                 [2]               [ ]
                  |
               TAKE 2
                  |
               [2,2]
              /      \
          TAKE 2    DON'T TAKE
            |           |
        [2,2,2]       [2,2]
                        |
                     TAKE 3
                        |
                    [2,2,3]
                        |
                       7 ✓
```

The TAKE branch stays at the same index:

```text
index
  ↓
take → same index
```

The DON'T TAKE branch moves forward:

```text
don't take → index + 1
```

This is the core of the solution.

---

# Dry Run

For:

```text
candidates = [2, 3, 6, 7]
target = 7
```

| Step | Action             | Index | Current     | Sum |
| ---: | ------------------ | ----: | ----------- | --: |
|    1 | Start              |     0 | `[]`        |   0 |
|    2 | Take `2`           |     0 | `[2]`       |   2 |
|    3 | Take `2`           |     0 | `[2,2]`     |   4 |
|    4 | Take `2`           |     0 | `[2,2,2]`   |   6 |
|    5 | Try `2`            |     0 | `[2,2,2,2]` |   8 |
|    6 | Stop: sum > target |     0 | `[2,2,2,2]` |   8 |
|    7 | Backtrack          |     0 | `[2,2,2]`   |   6 |
|    8 | Move to `3`        |     1 | `[2,2]`     |   4 |
|    9 | Take `3`           |     1 | `[2,2,3]`   |   7 |
|   10 | Target reached     |     1 | `[2,2,3]`   |   7 |
|   11 | Backtrack          |     1 | `[2,2]`     |   4 |
|   12 | Backtrack further  |     — | `[]`        |   0 |
|   13 | Take `7`           |     3 | `[7]`       |   7 |
|   14 | Target reached     |     3 | `[7]`       |   7 |

Final result:

```text
[[2,2,3], [7]]
```

---

# Difference Between `index` and `index + 1`

This is the most important concept in your code.

### TAKE

```text
solve(arr, index, ...)
```

The index remains the same.

Why?

Because the current element can be reused.

Example:

```text
2 → 2 → 2 → 2
```

### DON'T TAKE

```text
solve(arr, index + 1, ...)
```

The index moves forward.

Why?

Because we are choosing not to use the current candidate anymore and move to the next candidate.

So remember:

```text
TAKE       → same index
DON'T TAKE → index + 1
```

---

# Why This Solution Works

Every recursive state has two possibilities:

```text
1. Take the current number.
2. Skip the current number.
```

When the number is taken, keeping the same index allows it to be selected again.

When the number is skipped, moving to `index + 1` ensures that the algorithm progresses through the candidates.

The backtracking step restores the previous state so other combinations can be explored.

Because the algorithm stops when `sum == target`, every stored combination has exactly the required sum.

Because it stops when `sum > target`, unnecessary branches are avoided.

---

# Approach Evaluation

**Approach Type:** Recursion + Backtracking

Your approach is correct and well suited for this problem.

The most important part is the distinction between the two recursive calls:

```text
TAKE       → index stays the same
DON'T TAKE → index increases
```

This correctly handles the requirement that every candidate can be used an unlimited number of times.

The solution also uses:

```text
if (sum > target)
```

as an effective pruning condition because all candidate values are positive.

---

# Time Complexity

The number of possible combinations can grow exponentially with the target.

In the worst case, when the smallest candidate is `m`, the recursion depth can reach approximately:

```text
target / m
```

The exact number of explored states depends on the candidate values and target.

A common upper-bound description is:

**Time Complexity: O(N^(T/M))**

where:

* `N` = number of candidates
* `T` = target
* `M` = smallest candidate

This represents the exponential nature of the backtracking search.

---

# Space Complexity

The recursion depth can reach approximately:

```text
T / M
```

because the smallest candidate can repeatedly be selected.

The `current` combination can also contain approximately `T / M` elements.

Therefore, auxiliary recursion/backtracking space is:

**Space Complexity: O(T/M)**

The result list requires additional space for all generated combinations.

---

# Key Takeaways

* The solution uses **recursion + backtracking**.
* Every element has two choices: **TAKE** or **DON'T TAKE**.
* TAKE keeps the **same index** because an element can be reused.
* DON'T TAKE moves to **`index + 1`**.
* `current` stores the combination currently being constructed.
* `sum` keeps track of its current total.
* `sum == target` means a valid combination is found.
* `sum > target` stops an impossible branch.
* `current.remove()` performs the backtracking step.
* `new ArrayList<>(current)` stores an independent copy of the combination.
* The key difference from **Subsets** is that TAKE does not move to the next index.
* The key difference from **Subsets II** is that this problem's candidates are distinct, so duplicate-skipping logic is not required.

---

## 🔗 Problem Source

**Platform:** LeetCode

**Problem:** [Combination Sum](https://leetcode.com/problems/combination-sum/)
