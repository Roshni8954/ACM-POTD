# Day 4 - ACM POTD

## Problem
Find the missing number from an array containing numbers from 0 to n.

## Approach
I used the mathematical formula for sum of first n natural numbers and subtracted the actual sum of array to find the missing number.

## Complexity
Time - O(n)
space - O(1)

## Code
```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int actualSum = 0;
        int sum = n*(n+1)/2;      //O(n)
        for(int i=0;i<nums.length;i++){
            actualSum += nums[i];
        }
        return (sum-actualSum);
    }
}