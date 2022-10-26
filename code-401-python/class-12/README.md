# Class-12
## Stack and Queue
### Reading
##### Introduction to Stack and 
![](https://gohighbrow.com/wp-content/uploads/2018/07/Computer-science-fundamentals_6.1.png)
- The **stack** data structure is a linear data structure that accompanies a principle known as LIFO (Last In First Out) or FILO (First In Last Out).
    1. push the item into the stack
    2. pop the item out of the stack. 
![](https://everythingcomputerscience.com/images/stackImg.jpg)
- A **queue** is defined as a linear data structure that is open at both ends and the operations are performed in First In First Out (FIFO) order.
    1. Enqueue means to insert an item into the back of the queue, 
    2. dequeue means removing the front item.
![](https://everythingcomputerscience.com/images/queue.gif)
- **FIFO & LILO and LIFO & FILO Principles**
    - **Queue**: First In First Out (FIFO): The first object into a queue is the first object to leave the queue, used by a queue.
    - **Stack**: Last In First Out (LIFO): The last object into a stack is the first object to leave the stack, used by a stack

    OR

    - **Stack**: First In Last Out (FILO): The first object or item in a stack is the last object or item to leave the stack.

    - **Queue**: Last In Last Out (LILO): The last object or item in a queue is the last object or item to leave the queue.
![](https://media.geeksforgeeks.org/wp-content/uploads/FIFO.jpg)
#### Stack and Queue Implementation  
- Stack operations .

    1. **Push**: Add an element to the top of a stack
    2. **Pop**: Remove an element from the top of a stack
    3. **IsEmpty**: Check if the stack is empty
    4. **IsFull**: Check if the stack is full
    5. **Peek**: Get the value of the top element without removing it
- Working of Stack Data Structure
![](https://cdn.programiz.com/sites/tutorial2program/files/stack-operations.png)
- **Stack implementation in python**

    ```python
    # Creating a stack
    def create_stack():
        stack = []
        return stack


    # Creating an empty stack
    def check_empty(stack):
        return len(stack) == 0


    # Adding items into the stack
    def push(stack, item):
        stack.append(item)
        print("pushed item: " + item)


    # Removing an element from the stack
    def pop(stack):
        if (check_empty(stack)):
            return "stack is empty"

        return stack.pop()


    stack = create_stack()
    push(stack, str(1))
    push(stack, str(2))
    push(stack, str(3))
    push(stack, str(4))
    print("popped item: " + pop(stack))
    print("stack after popping an element: " + str(stack))

    ```
- **Stack Time Complexity**
For the array-based implementation of a stack, the push and pop operations take constant time, i.e. O(1).

- **Applications of Stack Data Structure**

    - *To reverse a word*: Put all the letters in a stack and pop them out. Because of the LIFO order of stack, you will get the letters in reverse order.
    - *In compilers*: Compilers use the stack to calculate the value of expressions like 2 + 4 / 5 * (7 - 9) by converting the expression to prefix or postfix form.
    - *In browsers*: The back button in a browser saves all the URLs you have visited previously in a stack. Each time you visit a new page, it is added on top of the stack. When you press the back button, the current URL is removed from the stack, and the previous URL is accessed.