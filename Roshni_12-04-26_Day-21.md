### Day 21 – ACM POTD
**LeetCode Problem 733: Flood Fill**

### Problem

Given a 2D image, a starting pixel `(sr, sc)` and a new color, fill all connected pixels having the same original color with the new color.

### Intuition

We start from the given cell and spread in 4 directions only to cells having the same original color.

### Core Logic

Use DFS and change color only if the current cell matches the original color.

### Why This Works

We ensure traversal only happens on connected components of the same color.

### Approach

Store original color
If original equals new color return image
Call DFS
Check boundaries
Check if cell matches original color
Color the cell
Move in 4 directions

### Interview Answer

Use DFS to traverse and recolor all connected cells matching the original color.

### Code (Java)

```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        int original = image[sr][sc];

        if(original == color) return image;
        dfs(image, sr, sc, original, color);
        return image;
    }

    private void dfs(int[][] image,int r, int c, int original,int color){
        if(r<0 || r>=image.length || c<0 || c>=image[0].length) return;

        if(image[r][c] != original) return;

        image[r][c] = color;

        dfs(image, r+1, c, original, color);
        dfs(image, r-1, c, original, color);
        dfs(image, r, c+1, original, color);
        dfs(image, r, c-1, original, color);
    }
}
```

### Line-by-Line Explanation

original stores starting color
if original equals new color no change needed
dfs called to start traversal
boundary check prevents invalid access
condition ensures only same color cells are processed
current cell is recolored
recursive calls spread in four directions

### Complexity Analysis

Time Complexity O(m*n)
Space Complexity O(m*n)

### Key Takeaways

Always compare with original color
Boundary check is important
DFS spreads in four directions
