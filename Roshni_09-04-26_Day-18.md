### Day 18 – ACM POTD
**LeetCode Problem 844: Backspace String Compare**

---

### Problem

Given two strings `s` and `t`, return true if they are equal when both are typed into empty text editors.
`#` means a backspace character.

---

### Intuition

Instead of building from left, we traverse from right and skip characters using a counter.

---

### Core Logic

Traverse from end
Count backspaces
Skip characters accordingly
Build valid string

---

### Why This Works

Each `#` cancels one previous character, so counting skips helps simulate deletion without extra space.

---

### Approach

Traverse string from right to left
Maintain a counter for `#`
If `#` found increase count
If normal character and count > 0 skip it
Else include character

---

### Interview Answer

Traverse from right and use a counter to skip characters affected by backspace. This avoids using extra stack space.

---

### Code (Java)

```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        return getActual(s).equals(getActual(t));
    }

    private String getActual(String input){
        StringBuilder actualStr = new StringBuilder();
        int count = 0;

        for(int i = input.length()-1; i>=0; i--){
            if(input.charAt(i) == '#'){
                count++;
                continue;
            }

            if(count > 0)
                count--;
            else
                actualStr.insert(0,input.charAt(i));
        }
        return actualStr.toString();
    }
}
```

---

### Line-by-Line Explanation

Function backspaceCompare compares processed strings of s and t

Function getActual processes string

StringBuilder actualStr stores final string

int count tracks number of backspaces

Loop runs from end to start

If character is # then increase count

Continue skips further processing

If count > 0 then skip character and decrease count

Else insert character at beginning

Return final string

---

### Complexity Analysis

Time Complexity O(n + m)
Space Complexity O(n + m)

---

### Dry Run

Input s = ab#c
Process from right
c kept

# increases count

b skipped
a kept
Result ac

Input t = ad#c
Result ac

---

### Edge Cases

More # than characters
Empty string
All characters removed

---

### Key Takeaways

Reverse traversal avoids extra stack
Counter technique is efficient
Useful optimization pattern
