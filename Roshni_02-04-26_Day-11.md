### Day 11 – ACM POTD  
**LeetCode Problem 21: Merge Two Sorted Lists**

### Problem
You are given the heads of two sorted linked lists `list1` and `list2`.
Merge the two lists into one sorted linked list and return its head.
The new list should be made by splicing together the nodes of the first two lists.

### Intuition
Since both lists are already sorted, we don’t need to sort again.  
We just compare the current nodes of both lists and pick the smaller one each time — similar to the merge step of merge sort.

### Core Logic
Use two pointers:
- Compare values of nodes from both lists  
- Attach the smaller node to the result  
- Move that list’s pointer forward  

### Why This Works
Because both lists are sorted:
- The smallest remaining element will always be at the current pointer of one of the lists  
- By always choosing the smaller one, we maintain sorted order  

### Approach
1. Create a dummy node to simplify handling head  
2. Use a pointer `current` to build the merged list  
3. Traverse both lists:  
   - Compare values  
   - Attach smaller node  
   - Move pointer forward  
4. If one list ends, attach the remaining part of the other list  
5. Return `dummy.next`  

### Interview Answer
We use a two-pointer approach to merge both sorted linked lists. At each step, we compare nodes and append the smaller one to the result. This ensures sorted order and runs in linear time.

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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode result = new ListNode(-1);
        ListNode current = result;

        while(list1 != null && list2 != null){
            if(list1.val <= list2.val){
                current.next =list1;
                list1 = list1.next;
            }else{
                current.next = list2;
                list2 = list2.next;
            }
            current = current.next;
        } 
        current.next = (list1 != null)? list1:list2;
        return result.next;
    }
}
```

## Complexity Analysis
Time Complexity: O(n + m)
→ We traverse both linked lists once, where n and m are their lengths
Space Complexity: O(1)
→ No extra space used (in-place merging, only pointers used)