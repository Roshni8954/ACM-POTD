### Day 20 – ACM POTD
**LeetCode Problem 1544: Make The String Great**

---

### Problem

Given a string `s` of lowercase and uppercase letters, remove adjacent pairs where the same letter appears in different cases (like `aA` or `Bb`).

Repeat until no such pairs exist and return the final string.

---

### Intuition

If two adjacent characters are same letter but different case → remove them.
This is similar to canceling pairs → stack approach works.

---

### Core Logic

* Traverse string
* Compare current char with last added char
* If they differ only by case → remove
* Else → add

---

### Why This Works

ASCII difference between lowercase and uppercase of same letter is 32.
So if `abs(a - b) == 32`, they cancel each other.

---

### Approach

1. Use StringBuilder as stack
2. Traverse string
3. If top exists and `abs(diff) == 32` → remove
4. Else → add
5. Return final string

---

### Interview Answer

Use a stack-like structure and remove adjacent characters if their ASCII difference is 32.

---

### Code (Java)

```java
class Solution {
    public String makeGood(String s) {
        StringBuilder sb = new StringBuilder();

        for (char ch : s.toCharArray()) {
            int len = sb.length();
            if (len > 0 && Math.abs(sb.charAt(len - 1) - ch) == 32) {
                sb.deleteCharAt(len - 1);
            } else {
                sb.append(ch);
            }
        }
        return sb.toString();
    }
}
```

---

### Line-by-Line Explanation

StringBuilder sb stores result

Loop through characters

Get current length

If stack not empty and ASCII difference is 32 → remove last char

Else append current char

Return final string

---

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(n)

---

### Dry Run

Input: "leEeetcode"

Steps
l → l
e → le
E → l (removed eE)
e → le
e → lee
t → leet

Output → "leetcode"

---

### Edge Cases

Empty string
No removable pairs
All characters removed

---

### Key Takeaways

Stack pattern problem
ASCII trick important
Remove adjacent opposite cases
