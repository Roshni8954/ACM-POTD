### Day 15 – ACM POTD
**LeetCode Problem 232: Implement Queue using Stacks**

### Problem
Implement a FIFO (First In First Out) queue using only two stacks.

### Intuition
Instead of delaying reversal during pop, we **reverse during push** so that the front element is always on top of `stack2`.


### Core Logic
* `stack1` → temporary stack
* `stack2` → main queue stack (top = front)
* During push → rearrange elements so order is maintained

### Why This Works
By reversing twice during push, we maintain correct queue order in `stack2`.

### Approach
1. Move all elements from `stack2` → `stack1`
2. Push new element into `stack1`
3. Move everything back to `stack2`
4. Now top of `stack2` = front of queue


### Interview Answer
We maintain queue order in a single stack by reversing elements during push using a helper stack. This ensures O(1) pop and peek.


### Code (Java)

```java
class MyQueue {
    Stack<Integer> stack1, stack2;
    public MyQueue() {
        stack1 = new Stack();
        stack2 = new Stack();
    }
    
    public void push(int x) {
        while(!stack2.isEmpty()){
            stack1.push(stack2.pop());
        }
        stack1.push(x);
        while(!stack1.isEmpty()){
            stack2.push(stack1.pop());
        }
    }
    
    public int pop() {
        return stack2.pop();
    }
    
    public int peek() {
        return stack2.peek();
    }
    
    public boolean empty() {
        return stack2.isEmpty();
    }
}

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */
```

### Line-by-Line Explanation

#### Initialization
* `Stack<Integer> stack1, stack2;` → Two stacks
* `stack1` → helper
* `stack2` → main queue

#### Constructor
* Initialize both stacks

#### Push Operation
* `while (!stack2.isEmpty())` → Move all elements to stack1
* `stack1.push(stack2.pop())` → reverse order
* `stack1.push(x)` → insert new element
* Move everything back to stack2 → restore order

 Now **top of stack2 = front element**

#### Pop Operation

* `return stack2.pop();`
   Directly remove front

#### Peek Operation
* `return stack2.peek();`
  Get front element

#### Empty Check
* `return stack2.isEmpty();`

### Complexity Analysis
* Time Complexity:

  * Push → O(n)
  * Pop → O(1)
  * Peek → O(1)
* Space Complexity: O(n)

### Dry Run
Push: 1
stack2 → [1]

Push: 2
stack2 → [1,2]

Push: 3
stack2 → [1,2,3]

Pop → 1 ✔
Peek → 2 ✔

### Edge Cases
* Pop on empty queue
* Single element
* Multiple push before pop

### Key Takeaways
* Two ways to solve this problem
* This approach: **costly push, fast pop**
* Maintains queue order at all times
* Good for understanding stack reversal
