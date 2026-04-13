### Day 22 – ACM POTD

**LeetCode Problem 997: Find the Town Judge**

### Problem

In a town of `n` people labeled from 1 to n, there is a rumor that one person is the judge.
The judge trusts nobody and everybody (except the judge) trusts the judge.
Given an array `trust`, return the label of the judge or -1 if no judge exists.

### Intuition

Judge has **in-degree = n-1** and **out-degree = 0**.
So we track trust balance for each person.

### Core Logic

If someone trusts another → decrease their score
If someone is trusted → increase their score
Judge will have score = n-1

### Why This Works

Judge is trusted by everyone and trusts no one, so net score becomes maximum.

### Approach

Create array `score[n+1]`
Traverse trust array
For `[a, b]`
 score[a]--
 score[b]++
Check for person with score = n-1

### Interview Answer

Use an array to track net trust score and find the person with score equal to n-1.

### Code (Java)

```java id="xkq3rt"
class Solution {
    public int findJudge(int n, int[][] trust) {
        int[] score = new int[n + 1];

        for (int[] t : trust) {
            score[t[0]]--;
            score[t[1]]++;
        }

        for (int i = 1; i <= n; i++) {
            if (score[i] == n - 1) return i;
        }

        return -1;
    }
}
```

### Line-by-Line Explanation

score array stores trust balance
loop reduces score for trusting person
increases score for trusted person
final loop finds person with score n-1

### Complexity Analysis

Time Complexity O(n + trust.length)
Space Complexity O(n)

### Dry Run

Input n = 3, trust = [[1,3],[2,3]]
score[1] = -1
score[2] = -1
score[3] = 2
Answer = 3

### Edge Cases

No trust array
Multiple candidates
Single person

### Key Takeaways

Use in-degree out-degree concept
Judge trusts nobody
Judge trusted by all
