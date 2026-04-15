### Day 24 – ACM POTD

**LeetCode Problem 104: Maximum Depth of Binary Tree**

### Problem

Given the root of a binary tree, return its maximum depth.
The maximum depth is the number of nodes along the longest path from root to leaf.

### Intuition

At every node, depth = 1 + max(depth of left, depth of right).
We use recursion to compute this.

### Core Logic

Recursively find depth of left and right subtree
Return 1 + maximum of both

### Why This Works

Tree depth depends on the longest path, so we take max at each step.

### Approach

If root is null return 0
Call recursion for left and right
Return 1 + max(left, right)

### Interview Answer

Use recursion to compute depth by taking the maximum depth of left and right subtree at each node.

### Code (Java)

```java 
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int maxDepth(TreeNode root) {
        if (root == null) return 0;
        return 1+ Math.max(maxDepth(root.left),maxDepth(root.right));
    }
}
```

### Line-by-Line Explanation

If root is null return 0
Recursively compute left depth
Recursively compute right depth
Return 1 + max of both

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(h)

### Dry Run

Tree:

```text
    1
   / \
  2   3
 /
4
```

Depth = 3

### Edge Cases

Empty tree
Single node
Skewed tree

### Key Takeaways

Classic recursion problem
Use max of left and right
Tree height concept
