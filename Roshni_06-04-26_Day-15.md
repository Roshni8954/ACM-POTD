### Day 15 – ACM POTD
**LeetCode Problem 232: Implement Queue using Stacks**

### Problem
Implement a FIFO (First In First Out) queue using only two stacks.

### Intuition
Instead of reversing during push, we reverse **only when needed (lazy transfer)**.

### Core Logic
* `stack1` → for push operations
* `stack2` → for pop/peek operations
* Transfer happens **only when stack2 is empty**

### Why This Works
Elements are reversed only when required, giving efficient amortized performance.

### Approach
1. Push → always into `stack1`
2. For peek/pop →

   * If `stack2` empty → move all elements from `stack1` to `stack2`
3. Perform operation on `stack2`

### Interview Answer
Use two stacks where one handles input and the other handles output. Transfer elements only when needed to simulate queue behavior efficiently.

### Code (Java)
```java
class MyQueue {
    Stack<Integer> stack1, stack2;
    public MyQueue() {
        stack1 = new Stack();
        stack2 = new Stack();
    }
    
    public void push(int x) {
        stack1.push(x);
    }
    
    public int pop() {
        peek();
        return stack2.pop();
    }
    
    public int peek() {
        if(stack2.isEmpty()){
            while(!stack1.isEmpty())
            stack2.push(stack1.pop());
        }
        return stack2.peek();
    }
    
    public boolean empty() {
        return stack2.isEmpty() && stack1.isEmpty();
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
* `stack1` → push stack
* `stack2` → pop/peek stack

#### Constructor
* Initialize both stacks

#### Push Operation
* `stack1.push(x);`
  👉 Simply add element (no reversal here)

#### Pop Operation
* `peek();` → ensures correct order in stack2
* `return stack2.pop();` → removes front element

#### Peek Operation
* `if(stack2.isEmpty())` → check if transfer needed
* Move all elements from stack1 → stack2
  👉 This reverses order
* `return stack2.peek();` → front element

#### Empty Check
* `return stack2.isEmpty() && stack1.isEmpty();`
  👉 Queue empty only if both stacks empty

### Complexity Analysis
* Time Complexity:

  * Push → O(1)
  * Pop → O(1) amortized
  * Peek → O(1) amortized
* Space Complexity: O(n)

### Dry Run
Push: 1, 2, 3

stack1 → [1,2,3]
stack2 → []

Peek → transfer happens
stack2 → [3,2,1]

Pop → 1 ✔

### Edge Cases
* Pop on empty queue
* Single element
* Multiple pushes before pop

### Key Takeaways
* Lazy transfer improves efficiency
* Amortized O(1) solution
* Most optimal approach for this problem
