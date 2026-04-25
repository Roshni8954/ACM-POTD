
### Day 34 – ACM POTD

**LeetCode Problem 22: Generate Parentheses**

### Problem

Given `n` pairs of parentheses, generate all combinations of well-formed parentheses.

### Intuition

We build strings step by step while ensuring validity.
At any point:

* We can add `(` if we still have some left
* We can add `)` only if it won’t break validity

---

### Core Logic

Use backtracking
Track count of open and close brackets
Ensure `close ≤ open`

---

### Why This Works

Valid parentheses must always have more or equal `(` than `)` at any point.

---

### Approach

Start with empty string
Add `(` if open < n
Add `)` if close < open
When length = 2*n → add to result

---

### Interview Answer

Use backtracking to generate valid combinations by maintaining counts of open and close brackets.

---

### Code (Java)

```java
import java.util.*;

class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> res = new ArrayList<>();
        backtrack(res, "", 0, 0, n);
        return res;
    }

    private void backtrack(List<String> res, String curr, int open, int close, int n) {
        if (curr.length() == 2 * n) {
            res.add(curr);
            return;
        }

        if (open < n) {
            backtrack(res, curr + "(", open + 1, close, n);
        }

        if (close < open) {
            backtrack(res, curr + ")", open, close + 1, n);
        }
    }
}
```

---

### Line-by-Line Explanation

res stores all valid combinations
backtrack builds strings recursively
curr stores current string
open tracks number of `(` used
close tracks number of `)` used
if length equals 2*n → valid string
add `(` if open < n
add `)` if close < open

---

### Complexity Analysis

Time Complexity O(4ⁿ / √n)
Space Complexity O(n)

---

### Dry Run

n = 3

Output:

```text id="9v6yqf"
((()))  
(()())  
(())()  
()(())  
()()()
```

---

### Edge Cases

n = 1
n = 0

---

### Key Takeaways

Backtracking problem
Maintain validity condition
Generate all combinations
