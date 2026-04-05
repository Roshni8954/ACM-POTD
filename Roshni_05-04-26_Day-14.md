### Day 14 – ACM POTD
**LeetCode Problem 20: Valid Parentheses**

### Problem
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['`, `']'`, determine if the input string is valid.

A string is valid if:

* Open brackets are closed by the same type
* Open brackets are closed in the correct order

### Intuition
Whenever we see an opening bracket, we expect a matching closing bracket later.
So we use a stack to track what needs to be closed.

### Core Logic
* Push opening brackets
* On closing bracket → check top of stack
* If mismatch → invalid

### Why This Works
Stack follows LIFO → last opened must be first closed.

### Approach
1. Create a stack
2. Traverse string
3. If opening → push
4. If closing → check top
5. If mismatch or empty → false
6. At end, stack should be empty

### Interview Answer
Use a stack to track opening brackets and match them with closing brackets. If at any point mismatch occurs or stack is not empty at end, return false.

### Code (Java)

```java
import java.util.Stack;

class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();

        for (char ch : s.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                stack.push(ch);
            } else {
                if (stack.isEmpty()) return false;
                char top = stack.pop();

                if (ch == ')' && top != '(') return false;
                if (ch == '}' && top != '{') return false;
                if (ch == ']' && top != '[') return false;
            }
        }
        return stack.isEmpty();
    }
}
```

### Line-by-Line Explanation
* `Stack<Character> stack = new Stack<>();` → Store opening brackets
* `for (char ch : s.toCharArray())` → Traverse string
* `if opening bracket` → push to stack
* `if stack.isEmpty()` → no matching opening
* `char top = stack.pop();` → get last opened bracket
* Compare types → mismatch → false
* `return stack.isEmpty();` → all brackets matched

### Complexity Analysis
* Time Complexity: O(n)
* Space Complexity: O(n)

### Dry Run

Input: `"({[]})"`

Steps:
Push → (
Push → {
Push → [
Match ]
Match }
Match )

Stack empty → valid

### Edge Cases
* Empty string
* Only opening brackets
* Only closing brackets
* Mismatched order

### Key Takeaways
* Stack is perfect for matching problems
* Always check empty before pop
* LIFO concept is key
