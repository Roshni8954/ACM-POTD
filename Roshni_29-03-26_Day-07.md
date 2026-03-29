# Day 7 - ACM POTD

## Problem

Rotate the array to the right by k steps, where k is non-negative.

## Approach

I used the reversal algorithm. First, I reversed the entire array. Then I reversed the first k elements, and finally reversed the remaining elements. This results in the array being rotated efficiently.

## Code

```java
class Solution {
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k = k % n;

        reverse(nums, 0, n-1);
        reverse(nums, 0, k-1);
        reverse(nums, k, n-1);
    }

        private void reverse(int [] nums, int start, int end){
            while(start<end){
                int temp = nums[start];
                nums[start++] = nums[end];
                nums[end--] = temp;
                // start++;
                // end--;
            }
    }
}
```

## Complexity

Time Complexity: O(n)
Space Complexity: O(1)