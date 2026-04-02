### Day 11 – ACM POTD
**LeetCode Problem 83: Remove Duplicates from Sorted List**

### Problem
Given the head of a sorted linked list, delete all duplicates such that each element appears only once.

Return the linked list sorted as well.

### Intuition
Since the list is sorted, duplicates will always be adjacent.
So we just compare current node with next node.

### Core Logic
If `current.val == current.next.val`, skip the next node.

### Why This Works
Sorted property ensures all duplicates are consecutive, so one pass is enough.

### Approach
1. Start from head
2. Traverse while `current.next != null`
3. If values same → skip node
4. Else move forward

### Interview Answer
Traverse the sorted list once and remove duplicates by skipping nodes with same values. Since duplicates are adjacent, one pass is sufficient.

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
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null) return null;
        ListNode current = head;

        while (current != null && current.next != null) {
            if (current.val == current.next.val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }
        
        return head;
    }
}
```
### Line-by-Line Explanation
* `ListNode current = head;` → Start from head
* `while (current != null && current.next != null)` → Traverse list
* `if (current.val == current.next.val)` → Check duplicate
* `current.next = current.next.next;` → Skip duplicate
* `else current = current.next;` → Move forward
* `return head;` → Return updated list

### Complexity Analysis
* Time Complexity: O(n)
* Space Complexity: O(1)

### Dry Run
Input:
1 → 1 → 2 → 3 → 3

Steps:
1 → skip duplicate → 1 → 2 → 3 → 3
move → 2
move → 3 → skip duplicate

Result:
1 → 2 → 3

### Edge Cases
* Empty list
* Single node
* All duplicates
* No duplicates

### Key Takeaways
* Works because list is sorted
* In-place modification
* One traversal only
