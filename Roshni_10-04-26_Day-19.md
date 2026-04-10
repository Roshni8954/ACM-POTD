### Day 19 – ACM POTD

**LeetCode Problem 1021: Remove Outermost Parentheses**

---

### Problem

Given a valid parentheses string, remove the outermost parentheses of every primitive string.

---

### Intuition

We track depth of parentheses.
Outermost brackets occur when depth is 0 → 1 and 1 → 0.
We skip those and keep inner ones.

---

### Core Logic

Use a counter `count`
Add character only when `count > 0`

---

### Why This Works

Outermost brackets are excluded because they occur at boundary depth.

---

### Approach

Traverse string
If `(`
 if count > 0 add
 increase count
If `)`
 decrease count
 if count > 0 add

---

### Interview Answer

Use a depth counter and append characters only when inside nested levels.

---

### Code (Java)

```java
class Solution {
    public String removeOuterParentheses(String s) {
        String ans = "";
        int count = 0;

        for(int i = 0; i < s.length(); i++) {
            if(s.charAt(i) == '(') {
                if(count > 0) ans += s.charAt(i);
                count++;
            } else {
                count--;
                if(count > 0) ans += s.charAt(i);
            }
        }
        return ans;
    }
}
```

---

### Line-by-Line Explanation

String ans stores result

int count tracks nesting level

Loop through string

If `(` and count > 0 then add to ans

Increase count

If `)` decrease count

If count > 0 then add to ans

Return ans

---

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(n)

---

### Dry Run

Input (()())(())

Output ()()()

---

### Edge Cases

Single pair
Nested groups
Multiple primitives

---

### Key Takeaways

Depth tracking is key
Skip outermost parentheses
Single pass solution
