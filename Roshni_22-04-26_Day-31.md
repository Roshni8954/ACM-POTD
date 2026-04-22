### Day 31 – ACM POTD

**LeetCode Problem 118: Pascal's Triangle**

### Problem

Given an integer `numRows`, return the first `numRows` of Pascal's Triangle.

Each number is the sum of the two numbers directly above it.

---

### Intuition

Each row starts and ends with 1.
Middle elements are sum of two elements from previous row.

---

### Core Logic

Use a list of lists
Build row by row
Use previous row to compute current row

---

### Why This Works

Each value depends only on previous row values.

---

### Approach

Initialize result list
Loop from 0 to numRows
Create new row
First and last element = 1
For middle elements use sum of previous row
Add row to result

---

### Interview Answer

Build Pascal's Triangle iteratively using previous row values.

---

### Code (Java)

```java 
import java.util.*;

class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<>();

        for (int i = 0; i < numRows; i++) {
            List<Integer> row = new ArrayList<>();

            for (int j = 0; j <= i; j++) {
                if (j == 0 || j == i) {
                    row.add(1);
                } else {
                    row.add(res.get(i - 1).get(j - 1) + res.get(i - 1).get(j));
                }
            }

            res.add(row);
        }

        return res;
    }
}
```

---

### Line-by-Line Explanation

Create result list
Loop for each row
Create new row list
If first or last index add 1
Else sum of two values from previous row
Add row to result
Return result

---

### Complexity Analysis

Time Complexity O(n²)
Space Complexity O(n²)

---

### Dry Run

numRows = 5

```text id="b6p2kw"
[1]  
[1,1]  
[1,2,1]  
[1,3,3,1]  
[1,4,6,4,1]
```

---

### Edge Cases

numRows = 1
numRows = 0

---

### Key Takeaways

Classic DP problem
Each row depends on previous
Triangle pattern logic
