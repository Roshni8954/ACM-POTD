# Day 8 - ACM POTD
# Reverse Linked List (LeetCode 206)

## Problem
Reverse a singly linked list and return the new head.

## Intuition
Each node points to the next node. To reverse the list, we need to change each node’s direction so it points to the previous node instead.

## Approach
1. Initialize two pointers:
   * prev = null
   * curr = head

2. Traverse the list:
   * Store next node
   * Reverse the link
   * Move prev forward
   * Move curr forward

3. At the end:
   * prev becomes the new head

## Code

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null, curr = head, temp;

        while(curr != null){
            temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        return prev;
    }
}
```

## Dry Run
Input:
1 → 2 → 3 → null

Step 1:
1 → null

Step 2:
2 → 1 → null

Step 3:
3 → 2 → 1 → null

## Complexity
Time Complexity: O(n)
Space Complexity: O(1)

## Edge Cases
* Empty list → return null
* Single node → no change

## Key Takeaways
* Always store next before breaking link
* Use three pointers (prev, curr, next)
* prev becomes new head

## One-Line Summary
Reverse links one by one using three pointers.
