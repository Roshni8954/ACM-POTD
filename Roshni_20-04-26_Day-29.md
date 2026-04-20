### Day 29 – ACM POTD

**LeetCode Problem 231: Power of Two**

### Problem

Given an integer `n`, return true if it is a power of two. Otherwise return false.

### Intuition

A power of two has only one set bit in its binary form.

### Core Logic

Use bit manipulation
Check if only one bit is set

### Why This Works

For any power of two, `n & (n - 1)` becomes 0 because it removes the only set bit.

### Approach

Check if n > 0
Apply `(n & (n - 1)) == 0`

### Interview Answer

Use bit manipulation to check if number has exactly one set bit.

### Code (Java)

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        return (n > 0 && (n & (n - 1)) == 0);
    }
}
```

### Line-by-Line Explanation

Check n is positive
Apply bitwise AND with n-1
If result is 0 then only one set bit exists

### Complexity Analysis

Time Complexity O(1)
Space Complexity O(1)

### Dry Run

n = 1
Binary 0001
n-1 = 0 → 0000
AND → 0000
Result true

### Edge Cases

n = 0
Negative numbers
n = 1

### Key Takeaways

Bit manipulation trick
Single set bit property
Constant time solution
