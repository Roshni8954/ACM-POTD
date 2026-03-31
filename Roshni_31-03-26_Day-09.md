# Day 9 - ACM POTD
# Linked List Cycle (LeetCode 141)

## Problem
Given the head of a linked list, determine if the list contains a cycle.

## Intuition
If a linked list has a cycle, traversing it will never reach null.
Using two pointers moving at different speeds helps detect this efficiently.

## Core Logic (Floyd’s Cycle Detection)

We use two pointers:

* Slow pointer moves 1 step at a time
* Fast pointer moves 2 steps at a time

If a cycle exists:

* Both pointers will eventually meet inside the cycle

If no cycle exists:

* Fast pointer will reach null

## Why This Works
Let:

* Slow moves 1 step
* Fast moves 2 steps

Difference in movement per step = 1

Inside a cycle:

* Fast gains 1 step over slow in every iteration
* After at most one full cycle length, fast will catch slow

## Approach
1. Initialize two pointers:

   * slow = head
   * fast = head

2. Traverse the list:

   * Move slow by 1 step
   * Move fast by 2 steps

3. Check:

   * If slow == fast → cycle exists
   * If fast reaches null → no cycle

## Code

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head == null) return false;
        ListNode fast = head, slow = head;
        while(fast != null && fast.next != null){
            fast= fast.next.next;
            slow = slow.next;
            if(slow == fast)   
                return true;
        }
        return false;
    }
}
```

## Line-by-Line Explanation

* `if (head == null)`
  → Empty list cannot have a cycle

* `slow = head`, `fast = head`
  → Both pointers start from beginning

* `while (fast != null && fast.next != null)`
  → Ensures fast can move two steps safely

* `slow = slow.next`
  → Moves slow pointer by one step

* `fast = fast.next.next`
  → Moves fast pointer by two steps

* `if (slow == fast)`
  → If both pointers meet, cycle exists

* `return false`
  → If loop ends, no cycle

## Dry Run
List with cycle:
1 → 2 → 3 → 4 → 2 ...

| Step  | slow | fast |
| ----- | ---- | ---- |
| start | 1    | 1    |
| 1     | 2    | 3    |
| 2     | 3    | 2    |
| 3     | 4    | 4    |

Pointers meet → cycle detected

## Complexity
Time Complexity: O(n)
Space Complexity: O(1)

## Edge Cases
* Empty list → return false
* Single node without loop → false
* Single node pointing to itself → true

## Key Takeaways
* Use two pointers with different speeds
* Meeting of pointers indicates a cycle
* No extra memory required
