### Day 26 – ACM POTD

**LeetCode Problem 543: Diameter of Binary Tree**

### Problem

Given the root of a binary tree, return the length of the diameter of the tree.
The diameter is the length of the longest path between any two nodes.

### Intuition

At each node, the longest path passing through it = left height + right height.
We compute height while updating maximum diameter.

### Core Logic

Use DFS
At each node compute left and right height
Update diameter = max(diameter, left + right)

### Why This Works

The longest path can pass through any node, so we check all nodes while computing height.

### Approach

Initialize diameter = 0
Use recursion to compute height
At each node update diameter
Return height to parent

### Interview Answer

Use DFS to compute height of subtrees and update diameter using left + right at each node.

### Code (Java)

```java id="9zv3xk"
class Solution {
    int diameter = 0;
    public int diameterOfBinaryTree(TreeNode root) {
        dfs(root);
        return diameter;
    }

    private int dfs(TreeNode root){
        if(root == null) return 0;
        
        int left = dfs(root.left);
        int right = dfs(root.right);
        diameter = Math.max(diameter,left+right);

        return Math.max(left,right) + 1;
    }
}
```

### Line-by-Line Explanation

diameter stores maximum path
dfs returns height of subtree
if node null return 0
compute left and right height
update diameter using left + right
return height to parent

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(h)

### Dry Run

Tree:

```text id="k7h1qv"
    1
   / \
  2   3
 / \
4   5
```

Longest path: 4 → 2 → 1 → 3
Diameter = 3

### Edge Cases

Empty tree
Single node
Skewed tree

### Key Takeaways

Combine height and diameter
DFS traversal
Check all nodes
