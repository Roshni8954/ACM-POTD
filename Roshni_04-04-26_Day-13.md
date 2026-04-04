### Day 13 – ACM POTD
**LeetCode Problem 234: Palindrome Linked List**

### Problem
Given the head of a singly linked list, return `true` if it is a palindrome, otherwise return `false`.

### Intuition
To check palindrome, we need to compare first half with second half.
Since it’s a linked list (no backward traversal), we reverse the second half and compare.

### Core Logic
* Find middle of list (slow & fast pointer)
* Reverse second half
* Compare both halves

### Why This Works
Reversing the second half allows direct comparison with the first half in O(1) space.

### Approach
1. Find middle using slow & fast pointers
2. Reverse second half of list
3. Compare first half and reversed second half
4. If all values match → palindrome

### Interview Answer
Use slow-fast pointers to find the middle, reverse the second half, and compare both halves. This gives O(n) time and O(1) space.

### Code (Java)

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
    public boolean isPalindrome(ListNode head) {
        if (head == null || head.next == null) return true;
        ListNode slow = head, fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        ListNode prev = null;
        while (slow != null) {
            ListNode next = slow.next;
            slow.next = prev;
            prev = slow;
            slow = next;
        }

        ListNode left = head, right = prev;
        while (right != null) {
            if (left.val != right.val) return false;
            left = left.next;
            right = right.next;
        }
        return true;
    }
}
```

### Line-by-Line Explanation
* `if (head == null || head.next == null)` → Single node is palindrome
* `slow & fast pointers` → Find middle
* `while (fast != null && fast.next != null)` → Move fast twice
* `prev = null` → Start reversing
* Reverse loop → Reverse second half
* `left = head, right = prev` → Compare both halves
* If mismatch → return false
* Else → return true

### Complexity Analysis
* Time Complexity: O(n)
* Space Complexity: O(1)

### Dry Run
Input:
1 → 2 → 2 → 1

Middle → split
Reverse second half → 1 → 2

Compare:
1 == 1
2 == 2

Result → true

### Edge Cases
* Empty list
* Single node
* Even length
* Odd length

### Key Takeaways
* Slow-fast pointer is key
* Reverse linked list trick
* Compare halves efficiently
* No extra space needed
