# Day 6 - ACM POTD

## Problem
Check if there exist two indices such that one element is double of another.

## Approach
I used a HashSet to store elements. For each element, I checked if its double or half already exists in the set.

## Complexity
Time Complexity: O(n)
Space Complexity: O(n)

## Code
```java
import java.util.*;

class Solution {
    public boolean checkIfExist(int[] arr) {
        HashSet<Integer> set = new HashSet<>();

        for (int num : arr) {
            if (set.contains(2 * num) || 
                (num % 2 == 0 && set.contains(num / 2))) {
                return true;
            }
            set.add(num);
        }

        return false;
    }
}