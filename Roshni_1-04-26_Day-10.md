# Day X - ACM POTD

# Middle of the Linked List (LeetCode 876)

---

## Problem

Given the head of a singly linked list, return the middle node.
If there are two middle nodes, return the second one.

---

## Intuition

If one pointer moves faster than another, the slower pointer will reach the middle when the faster pointer reaches the end.

---

## Core Logic

Use two pointers:

* Slow pointer moves 1 step
* Fast pointer moves 2 steps

When fast reaches the end, slow will be at the middle.

---

## Why This Works

Fast pointer moves twice as fast as slow.
So when fast covers the entire list, slow covers only half of it, which places it at the middle.

---

## Approach

1. Initialize two pointers:

   * slow = head
   * fast = head

2. Traverse the list:

   * Move slow by 1 step
   * Move fast by 2 steps

3. When fast reaches null or end:

   * slow will be at the middle

4. Return slow

---

## Interview Answer

Use two pointers where one moves twice as fast as the other.
When the fast pointer reaches the end, the slow pointer will be at the middle of the list.

---

## Code

```java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        return slow;
    }
}
```

---

## Complexity

Time Complexity: O(n)
Space Complexity: O(1)

---

## Dry Run

Input:
1 → 2 → 3 → 4 → 5

Step 1:
slow = 1, fast = 1

Step 2:
slow = 2, fast = 3

Step 3:
slow = 3, fast = 5

Step 4:
fast reaches null

Output:
3 (middle node)

---

## Edge Cases

* Single node → return that node
* Even number of nodes → return second middle
* Empty list → not applicable (constraints ensure at least one node)

---

## Key Takeaways

* Two-pointer technique is very efficient
* Fast moves twice as fast as slow
* When fast reaches end, slow is at middle
