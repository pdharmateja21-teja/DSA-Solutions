# Palindrome String

## Problem Statement

Given a string `s`, determine whether the string is a palindrome.

A palindrome is a string that reads the same from left to right and right to left.

This solution uses **recursion** with two pointers to compare characters from both ends of the string.

### Example

**Input**
```text
s = "madam"
```

**Output**
```text
true
```

Because:

```text
madam
```

reads the same in both directions.

---

# Approach

We use two pointers:

- `left` starts from the beginning of the string.
- `right` starts from the end of the string.

At every recursive call:

1. Check whether `left >= right`.
2. If yes, all required characters have matched, so return `true`.
3. Compare the characters at `left` and `right`.
4. If they are different, the string is not a palindrome, so return `false`.
5. If they are equal, move both pointers toward the center.
6. Continue recursively until the pointers meet or cross.

The main idea is:

```text
Compare first and last
        ↓
Move inward
        ↓
Compare second and second-last
        ↓
Move inward
        ↓
Continue until the middle
```

---

# Code

```java
class Solution {
    static boolean palindrome(String s, int left, int right) {
        if (left >= right) {
            return true;
        }

        if (s.charAt(left) != s.charAt(right)) {
            return false;
        }

        return palindrome(s, left + 1, right - 1);
    }

    boolean isPalindrome(String s) {
        return palindrome(s, 0, s.length() - 1);
    }
}
```

---

# Understanding the Code

Suppose:

```text
s = "madam"
```

The string has 5 characters:

```text
Index:  0 1 2 3 4
String: m a d a m
```

The first call is:

```text
palindrome(s, 0, 4)
```

So:

```text
left = 0
right = 4
```

The function compares:

```text
s.charAt(0) = 'm'
s.charAt(4) = 'm'
```

They are equal, so the recursion moves inward:

```text
left = 1
right = 3
```

It then compares:

```text
'a' and 'a'
```

They are equal again.

Finally:

```text
left = 2
right = 2
```

The base case is reached, so the function returns `true`.

---

# Recursive Call 1

```text
left = 0
right = 4
```

Characters:

```text
s.charAt(0) = 'm'
s.charAt(4) = 'm'
```

Comparison:

```text
'm' == 'm'
```

They match.

Next recursive call:

```text
palindrome(s, 1, 3)
```

---

# Recursive Call 2

```text
left = 1
right = 3
```

Characters:

```text
s.charAt(1) = 'a'
s.charAt(3) = 'a'
```

Comparison:

```text
'a' == 'a'
```

They match.

Next recursive call:

```text
palindrome(s, 2, 2)
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
```

is true.

Therefore:

```text
return true;
```

All required character pairs matched, so the string is a palindrome.

Final result:

```text
true
```

---

# Code Flow (Step-by-Step Execution)

### Input

```text
s = "madam"
```

Initial call:

```text
palindrome(s, 0, 4)
```

---

### Step 1

Compare:

```text
s[0] = 'm'
s[4] = 'm'
```

They match.

Move inward:

```text
left = 1
right = 3
```

---

### Step 2

Compare:

```text
s[1] = 'a'
s[3] = 'a'
```

They match.

Move inward:

```text
left = 2
right = 2
```

---

### Step 3

Now:

```text
left >= right
```

So the base case returns:

```text
true
```

Final result:

```text
true
```

---

# Dry Run

| Call | `left` | `right` | Characters Compared | Result |
|-----:|-------:|--------:|---------------------|--------|
| 1 | 0 | 4 | `'m'` and `'m'` | Match |
| 2 | 1 | 3 | `'a'` and `'a'` | Match |
| 3 | 2 | 2 | No comparison | Base case |

Final result:

```text
true
```

---

# Example Where the String Is Not a Palindrome

Suppose:

```text
s = "hello"
```

Index positions:

```text
Index:  0 1 2 3 4
String: h e l l o
```

First comparison:

```text
s[0] = 'h'
s[4] = 'o'
```

Since:

```text
'h' != 'o'
```

the condition becomes true:

```java
if (s.charAt(left) != s.charAt(right))
```

Therefore:

```text
return false;
```

The recursion stops immediately.

Final result:

```text
false
```

---

# Understanding the Base Case

The base condition is:

```java
if (left >= right) {
    return true;
}
```

This means all necessary character comparisons have already been completed.

There are two possible situations.

### When `left == right`

There is one character remaining in the middle.

For example:

```text
m a d a m
    ↑
```

The middle character does not need to be compared with itself.

So the string can still be a palindrome.

### When `left > right`

The pointers have crossed each other.

This means every required pair has already matched.

Therefore:

```text
return true;
```

---

# Why This Solution Works

A palindrome has matching characters at equal distances from both ends.

For example:

```text
m a d a m
↑       ↑
m       m

  ↑   ↑
  a   a

    ↑
    d
```

The algorithm checks exactly these pairs.

If any pair is different:

```text
s[left] != s[right]
```

the string cannot be a palindrome, so it immediately returns `false`.

If every pair matches until the pointers meet, the string is a palindrome and the function returns `true`.

---

# Recursion Flow

For:

```text
s = "madam"
```

the recursive calls are:

```text
palindrome(0, 4)
        ↓
palindrome(1, 3)
        ↓
palindrome(2, 2)
        ↓
return true
```

Each call reduces the problem by removing one character from both ends.

The problem becomes smaller as:

```text
(0, 4)
   ↓
(1, 3)
   ↓
(2, 2)
```

This is a common recursion pattern where the problem is reduced from both sides.

---

# Why the Function Returns `palindrome(...)`

The line:

```java
return palindrome(s, left + 1, right - 1);
```

passes the result of the next recursive call back to the previous call.

For example:

```text
palindrome(2, 2)
    ↓
true
```

Therefore:

```text
palindrome(1, 3)
    ↓
true
```

And finally:

```text
palindrome(0, 4)
    ↓
true
```

So the final result reaches:

```text
isPalindrome(s)
```

and returns:

```text
true
```

---

# Time Complexity

Each character is involved in at most one comparison from each side.

The recursion processes approximately half of the string.

Therefore:

**Time Complexity: O(n)**

---

# Space Complexity

The solution does not create another string or array.

However, recursive calls are stored in the call stack.

There are approximately `n / 2` recursive calls.

Ignoring constant factors:

**Space Complexity: O(n)**

---

# Key Takeaways

- A palindrome reads the same from both directions.
- Two pointers are used: `left` and `right`.
- Characters from both ends are compared.
- If any pair is different, return `false`.
- If all pairs match, return `true`.
- `left >= right` is the base case.
- Both pointers move toward the center after every successful comparison.
- The solution demonstrates recursion combined with the two-pointer technique.
- Time Complexity is `O(n)`.
- Space Complexity is `O(n)` because of the recursion call stack.

---

## 🔗 Problem Source

**Platform:** GeeksforGeeks

**Problem:** [Palindrome String](https://www.geeksforgeeks.org/problems/palindrome-string0817/1)
