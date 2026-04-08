### Day 17 – ACM POTD
**LeetCode Problem 1047: Remove All Adjacent Duplicates In String**

### Problem

Given a string `s`, repeatedly remove adjacent duplicate characters until no duplicates remain.

Return the final string.


### Intuition

If two adjacent characters are same → remove them.
This is similar to matching pairs → stack is perfect.


### Core Logic

* Traverse string
* If current char = top of stack → pop
* Else → push

### Why This Works

Stack keeps track of valid characters.
Whenever duplicate appears, we remove previous occurrence.


### Approach

1. Create a stack (or StringBuilder)
2. Traverse characters
3. If top == current → pop
4. Else → push
5. Build final string


### Interview Answer

Use a stack to remove adjacent duplicates by comparing current character with the top. This ensures O(n) time.


### Code (Java)

```java
class Solution {
    public String removeDuplicates(String s) {
        StringBuilder sb = new StringBuilder();

        for (char ch : s.toCharArray()) {
            int len = sb.length();

            if (len > 0 && sb.charAt(len - 1) == ch) {
                sb.deleteCharAt(len - 1);
            } else {
                sb.append(ch);
            }
        }
        return sb.toString();
    }
}
```

### Line-by-Line Explanation

#### Initialization
* `StringBuilder sb = new StringBuilder();`
   Acts like a stack

#### Loop
* `for (char ch : s.toCharArray())`
  Traverse string

#### Length
* `int len = sb.length();`
   Current size

#### Duplicate Check
* `if (len > 0 && sb.charAt(len - 1) == ch)`
   Compare with last character

#### Remove
* `sb.deleteCharAt(len - 1);`
   Remove duplicate

#### Add
* `sb.append(ch);`
  Add new character

#### Return
* `return sb.toString();`


### Complexity Analysis

* Time Complexity: O(n)
* Space Complexity: O(n)


### Edge Cases

* Empty string
* No duplicates
* All characters same


### Key Takeaways

* Stack pattern problem
* StringBuilder used as stack
* Remove on match, add otherwise
