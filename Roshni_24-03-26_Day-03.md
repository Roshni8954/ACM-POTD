# Day 3 - ACM POTD

## Problem
Find the maximum profit from buying and selling a stock given daily prices.

## Approach
I tracked the minimum price so far and calculated profit at each step. The maximum profit is updated whenever a better selling price is found.

## Complexity
Time: O(n)
Space: O(1)


## Code
```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = prices[0];
        int maxProfit = 0;

        for (int i = 1; i < prices.length; i++) {
            if (prices[i] < minPrice) {
                minPrice = prices[i];
            } else {
                int profit = prices[i] - minPrice;
                maxProfit = Math.max(maxProfit, profit);
            }
        }
        return maxProfit;
    }
}