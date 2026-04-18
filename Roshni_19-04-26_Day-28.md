### Day 28 – ACM POTD

**LeetCode Problem 509: Fibonacci Number**

### Problem

The Fibonacci sequence is defined as
F(0) = 0, F(1) = 1
F(n) = F(n-1) + F(n-2) for n > 1
Given n, return F(n).

### Intuition

Each number depends on the previous two numbers.
Instead of recursion, we can build it iteratively.

### Core Logic

Use two variables to store previous values
Update them in loop

### Why This Works

We avoid repeated calculations by storing previous results.

### Approach

If n ≤ 1 return n
Initialize a = 0, b = 1
Loop from 2 to n
Compute sum = a + b
Shift values

### Interview Answer

Use iterative DP to compute Fibonacci in O(n) time and O(1) space.

### Code (Java)

```java id="w6l2pq"
class Solution {
    public int fib(int n) {
        if (n <= 1) return n;

        int a = 0, b = 1;

        for (int i = 2; i <= n; i++) {
            int sum = a + b;
            a = b;
            b = sum;
        }

        return b;
    }
}
```

### Line-by-Line Explanation

If n is 0 or 1 return n
a stores F(n-2)
b stores F(n-1)
Loop calculates next value
sum = a + b
Shift a to b
Shift b to sum
Return final value

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(1)

### Dry Run

n = 5
Sequence → 0,1,1,2,3,5
Output = 5

### Edge Cases

n = 0
n = 1
Large n

### Key Takeaways

DP optimization
Avoid recursion overhead
Use variables instead of array
