### Day 12 – ACM POTD
**LeetCode Problem 160: Intersection of Two Linked Lists**

### Problem
Given the heads of two singly linked lists `headA` and `headB`, return the node at which the two lists intersect.

If the two linked lists have no intersection, return `null`.

### Intuition
If we traverse both lists and switch heads when reaching the end, both pointers will travel equal distance and meet at the intersection point.

### Core Logic
Use two pointers:

* Traverse both lists
* When a pointer reaches end → switch to other list
* They will meet at intersection or null

### Why This Works
Both pointers travel:
lengthA + lengthB
So they align at intersection point automatically.

### Approach
1. Initialize two pointers `a` and `b`
2. Traverse both lists
3. If pointer becomes null → redirect to other list head
4. Continue until they meet
5. Return intersection node

### Interview Answer
Use two pointers and switch heads when reaching the end. This ensures both pointers traverse equal distance and meet at the intersection node in O(n) time.

### Code (Java)

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode a = headA, b = headB;

        while(a != b){
            a = (a == null)? headB:a.next;
            b = (b == null)? headA:b.next;
        }
        return a;
    }
}
```

### Line-by-Line Explanation
* `ListNode a = headA;` → Pointer for list A
* `ListNode b = headB;` → Pointer for list B
* `while (a != b)` → Loop until both meet
* `a = (a == null) ? headB : a.next;` → Switch list when null
* `b = (b == null) ? headA : b.next;` → Same for b
* `return a;` → Intersection node or null

### Complexity Analysis
* Time Complexity: O(n + m)
* Space Complexity: O(1)

### Dry Run
List A: 1 → 2 → 3 → 4 → 5
List B: 9 → 4 → 5

After switching traversal:
Both pointers meet at node `4`

### Edge Cases
* No intersection → return null
* One list empty
* Both lists same
* Intersection at head

### Key Takeaways
* No need to calculate lengths
* Elegant two-pointer trick
* Equal traversal ensures meeting point
* Very important interview problem
