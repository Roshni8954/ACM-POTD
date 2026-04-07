### Day 16 – ACM POTD

**LeetCode Problem 225: Implement Stack using Queues**

---

### Problem

Implement a LIFO (Last In First Out) stack using only queues.

---

### Intuition

Queue is FIFO, Stack is LIFO → opposite behavior.
So we rearrange elements during push to always keep the last element at the front.

---

### Core Logic

* Use one queue
* On push → rotate previous elements behind the new element
* So front of queue always acts like stack top

---

### Why This Works

By rotating elements after every push, we simulate LIFO using FIFO.

---

### Approach

1. Push element into queue
2. Rotate queue (size-1 times)
3. Now front = latest element
4. Pop → remove from front

---

### Interview Answer

Use a single queue and rotate elements after every push so that the most recent element is always at the front, simulating stack behavior.

---

### Code (Java)

```java
class MyStack {
    Queue<Integer> queue;
    public MyStack() {
        queue = new LinkedList();
    }
    
    public void push(int x) {
        int size = queue.size();
        queue.add(x);
        while(size-- > 0){
            queue.add(queue.poll());
        }
    }
    
    public int pop() {
        return queue.poll();
    }
    
    public int top() {
       return  queue.peek();
    }
    
    public boolean empty() {
        return queue.isEmpty();
    }
}

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack obj = new MyStack();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.top();
 * boolean param_4 = obj.empty();
 */
```

---

### Line-by-Line Explanation

#### Initialization

* `Queue<Integer> q;` → declare queue

---

#### Constructor

* `q = new LinkedList<>();` → initialize queue (Queue needs implementation)

---

#### Push Operation

* `q.add(x);` → insert element
* `int size = q.size();` → total elements
* `while (size-- > 1)` → rotate previous elements
* `q.add(q.remove());` → move front to back

👉 Latest element comes to front

---

#### Pop Operation

* `return q.remove();` → removes front (top of stack)

---

#### Top Operation

* `return q.peek();` → returns front (top element)

---

#### Empty Check

* `return q.isEmpty();`

---

### Common Doubt: Why LinkedList?

* We are **not allowed to use Stack directly**
* We must use Queue to simulate stack
* `Queue` is an interface in Java
* `LinkedList` is used because it implements Queue

👉 That’s why:

```java
Queue<Integer> q = new LinkedList<>();
```

---

### Complexity Analysis

* Time Complexity:

  * Push → O(n)
  * Pop → O(1)
  * Top → O(1)
* Space Complexity: O(n)

---

### Dry Run

Push: 1 → [1]
Push: 2 → [2,1]
Push: 3 → [3,2,1]

Pop → 3 ✔
Top → 2 ✔

---

### Edge Cases

* Pop on empty stack
* Single element
* Multiple pushes

---

### Key Takeaways

* Rotation trick is key
* Queue simulates stack
* Costly push, fast pop
