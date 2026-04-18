### Day 27 – ACM POTD

**LeetCode Problem 572: Subtree of Another Tree**

### Problem

Given two binary trees `root` and `subRoot`, return true if `subRoot` is a subtree of `root`.

### Intuition

Instead of comparing trees node by node, we convert both trees into strings using preorder traversal and check if one string is a substring of another.

### Core Logic

Convert both trees to strings using preorder traversal
Check if subtree string exists in main tree string

### Why This Works

If `subRoot` exists inside `root`, its traversal pattern will appear as a substring in the main tree traversal.

### Approach

Use preorder traversal
Include null markers to avoid false matches
Convert both trees into strings
Check if main string contains subtree string

### Interview Answer

Serialize both trees using preorder traversal and check substring match.

### Code (Java)

```java
class Solution {

    public boolean isSubtree(TreeNode root, TreeNode subRoot) {

        String fullTree = preOrderTraversal(root);
        String subTree = preOrderTraversal(subRoot);
        
        return fullTree.contains(subTree);
    }

    String preOrderTraversal(TreeNode node) {
        if (node == null) {
            return "null";
        }

        StringBuilder sb = new StringBuilder("^");
        sb.append(node.val);
        sb.append(preOrderTraversal(node.left));
        sb.append(preOrderTraversal(node.right));

        return sb.toString();
    }
}
```

### Line-by-Line Explanation

preOrderTraversal converts tree into string
if node is null return "null"
StringBuilder used to build string
"^" added to avoid wrong matches
append current node value
append left subtree
append right subtree
return final string

isSubtree converts both trees
checks if subtree string exists in full tree

### Complexity Analysis

Time Complexity O(n + m)
Space Complexity O(n + m)

### Dry Run

root:

```text
    3
   / \
  4   5
 / \
1   2
```

subRoot:

```text
  4
 / \
1   2
```

Serialized root → ^3^4^1nullnull^2nullnull^5nullnull
Serialized subRoot → ^4^1nullnull^2nullnull

Check contains → true

### Edge Cases

Duplicate values
Null nodes important
Subtree not present

### Key Takeaways

Tree to string conversion
Use null markers
Substring matching trick
Optimized approach
