### Day 30 – ACM POTD

**LeetCode Problem 70: Climbing Stairs**

### Problem

You are climbing a staircase. It takes `n` steps to reach the top.
Each time you can climb either 1 or 2 steps.
Return the number of distinct ways to reach the top.

### Intuition

To reach step `n`, you can come from:

* step `n-1` (1 step)
* step `n-2` (2 steps)

So:
`ways(n) = ways(n-1) + ways(n-2)`
This is Fibonacci pattern.

### Core Logic

Use two variables to store previous results
Build answer iteratively

### Why This Works

Each step depends only on last two steps → dynamic programming optimization.

### Approach

If n ≤ 2 return n
Initialize a = 1, b = 2
Loop from 3 to n
Compute sum = a + b
Shift values

### Interview Answer

Use iterative DP (Fibonacci pattern) to compute number of ways efficiently.

### Code (Java)

```java id="y9gk3m"
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) return n;

        int a = 1, b = 2;

        for (int i = 3; i <= n; i++) {
            int sum = a + b;
            a = b;
            b = sum;
        }

        return b;
    }
}
```

### Line-by-Line Explanation

If n is 1 or 2 return n
a stores ways to reach step n-2
b stores ways to reach step n-1
Loop calculates next value
sum = a + b
Shift values
Return final answer

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(1)

### Dry Run

n = 5
Ways → 1, 2, 3, 5, 8
Output = 8

### Edge Cases

n = 1
n = 2
Large n

### Key Takeaways

Fibonacci pattern
DP optimization
Constant space solution
