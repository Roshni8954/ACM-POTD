### Day 33 – ACM POTD

**LeetCode Problem 198: House Robber**

### Problem

You are a robber planning to rob houses along a street.
Each house has some money, but adjacent houses cannot be robbed.
Return the maximum amount you can rob.

### Intuition

At each house, you have two choices
Rob it or skip it

So:
`dp[i] = max(dp[i-1], nums[i] + dp[i-2])`

---

### Core Logic

Use DP
Keep track of previous two states

---

### Why This Works

Each decision depends on previous non-adjacent house.

---

### Approach

Initialize two variables
Loop through array
Update max profit

---

### Interview Answer

Use dynamic programming to choose between robbing current house or skipping it.

---

### Code (Java)

```java id="p8z1kl"
class Solution {
    public int rob(int[] nums) {
        int prev1 = 0, prev2 = 0;

        for (int num : nums) {
            int curr = Math.max(prev1, prev2 + num);
            prev2 = prev1;
            prev1 = curr;
        }

        return prev1;
    }
}
```

---

### Line-by-Line Explanation

prev1 stores max till previous house
prev2 stores max till house before previous
Loop through houses
Choose max between skipping or robbing
Update variables
Return final result

---

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(1)

---

### Dry Run

nums = [2,7,9,3,1]

Step1 → 2
Step2 → max(2,7) = 7
Step3 → max(7,2+9=11) = 11
Step4 → max(11,7+3=10) = 11
Step5 → max(11,11+1=12) = 12

Output = 12

---

### Edge Cases

Empty array
Single house
All values same

---

### Key Takeaways

DP pattern
Choose or skip
Optimized space
