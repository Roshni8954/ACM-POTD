# Day 5 - ACM POTD

## Problem
Move all zeros in the array to the end while maintaining the relative order of non-zero elements.

## Approach
I used an auxiliary array to first store all non-zero elements. Then I filled the remaining positions with zeros. Finally, I copied the result back into the original array.

## Complexity

Time Complexity: O(n)
Space Complexity: O(n)

## Code

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int n = nums.length;
        int []temp = new int[n]; int count = 0;

        for(int i=0;i<n;i++){
            if(nums[i] != 0){
                temp[count++] = nums[i];
            }
        }
        while(count<n){
            temp[count++] = 0;
        }
        for(int i=0;i<n;i++){
            nums[i] = temp[i];
        }
    }
}
```