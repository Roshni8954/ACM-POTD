### Day 25 – ACM POTD

**LeetCode Problem 226: Invert Binary Tree**

### Problem

Given the root of a binary tree, invert the tree and return its root.
Inverting means swapping left and right child of every node.

### Intuition

For every node, swap its left and right subtree.
Do this recursively for the whole tree.

### Core Logic

Swap left and right
Recursively apply same operation on children

### Why This Works

By swapping at every node, the entire tree gets mirrored.

### Approach

If root is null return null
Swap left and right child
Call recursion on left and right
Return root

### Interview Answer

Use recursion to swap left and right child at each node to invert the tree.

### Code (Java)

```java id="u8f3kd"
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) return null;

        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;

        invertTree(root.left);
        invertTree(root.right);

        return root;
    }
}
```

### Line-by-Line Explanation

If root is null return null
Store left child in temp
Assign right child to left
Assign temp to right
Recursively invert left subtree
Recursively invert right subtree
Return root

### Complexity Analysis

Time Complexity O(n)
Space Complexity O(h)

### Dry Run

Original:

```text
    4
   / \
  2   7
 / \ / \
1  3 6  9
```

Inverted:

```text
    4
   / \
  7   2
 / \ / \
9  6 3  1
```

### Edge Cases

Empty tree
Single node
Skewed tree

### Key Takeaways

Swap at every node
Recursive traversal
Tree mirroring concept
