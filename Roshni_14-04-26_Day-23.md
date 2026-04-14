### Day 23 – ACM POTD

**LeetCode Problem 1791: Find Center of Star Graph**

### Problem

You are given a star graph with `n` nodes labeled from 1 to n.
A star graph has one center node connected to all other nodes.
Given edges, return the center node.

### Intuition

In a star graph, the center node appears in every edge.
So the common node between first two edges is the answer.

### Core Logic

Compare first two edges
The common element is the center

### Why This Works

Center node is connected to all nodes, so it must appear in every edge.

### Approach

Take first two edges
Check which node is common
Return that node

### Interview Answer

The center node must appear in both first and second edges, so compare and return the common node.

### Code (Java)

```java id="8m9wq2"
class Solution {
     public int findCenter(int[][] edges) {
        return  (edges[0][0] == edges[1][0] || edges[0][0] == edges[1][1]) ? edges[0][0] : edges[0][1];
    }
 }
```

### Line-by-Line Explanation

compare first element of first edge with second edge
if match return it
otherwise return second element

### Complexity Analysis

Time Complexity O(1)
Space Complexity O(1)

### Dry Run

Input: [[1,2],[2,3],[4,2]]
Common in first two edges → 2
Output → 2

### Edge Cases

Minimum edges
Different order of nodes

### Key Takeaways

Star graph property
Common node logic
Constant time solution
