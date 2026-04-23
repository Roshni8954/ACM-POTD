### Day 32 – ACM POTD

**LeetCode Problem 746: Min Cost Climbing Stairs**

### Problem

You are given an integer array `cost` where `cost[i]` is the cost of step i.
You can climb either 1 or 2 steps.
You can start from step 0 or step 1.
Return the minimum cost to reach the top.

### Intuition

To reach step `i`, you can come from:

* step `i-1`
* step `i-2`

So:
`dp[i] = cost[i] + min(dp[i-1], dp[i-2])`

---

### Core Logic

Use DP to store minimum cost
Use only two variables to optimize space

---

### Why This Works

Each step depends only on previous two steps → optimal substructure.

---

### Approach

Initialize two variables for step 0 and step 1
Loop from step 2
Compute current cost
Return min of last two

---

### Interview Answer

Use dynamic programming to compute minimum cost using previous two states.

---

### Code (Java)

```java id="v3k9lm"
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int a = cost[0], b = cost[1];

        for (int i = 2; i < cost.length; i++) {
            int curr = cost[i] + Math.min(a, b);
            a = b;
            b = curr;
        }

        return Math.min(a, b);
    }
}
```

---

### Line-by-Line Explanation

a stores cost to reach step i-2
b stores cost to reach step i-1
Loop computes current cost
curr = cost[i] + min(a, b)
Shift values
Return min of last two

---

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(1)

---

### Dry Run

cost = [10,15,20]

Step 0 → 10
Step 1 → 15
Step 2 → 20 + min(10,15) = 30

Return min(15,30) = 15

---

### Edge Cases

Minimum size array
Large values
All same cost

---

### Key Takeaways

DP with space optimization
Fibonacci-like pattern
Choose minimum path
