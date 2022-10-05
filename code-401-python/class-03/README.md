# Class-03 
## Whiteboarding + Big O
### Reading
#### Beginners Guide to Big O

![Read files](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQq-ZZ5X3JcI9f2SHjTPptHkpNqPdwIX0kVEg&usqp=CAU)
- **Big O notation** is used in *Computer Science* to describe the performance or complexity of an algorithm. Big O specifically describes the **worst-case scenario**, and can be used to describe the execution time required or the space used (e.g. in memory or on disk) by an algorithm.

![big o](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRE-tjS6FtIhCG1ZDPckXhnZIOUVT_q4jWiGg&usqp=CAU)
 
- O(1) - Constant time complexity

    ```python
    if a > b:
        return True
    else:
        return False
    ```
- O(n) - Linear time complexity

    ```python 
    def search_algo(num, items):
        for item in items:
            if item == num:
                return True
            else:
                pass
    nums = [2, 4, 6, 8, 10]

    print(search_algo(2, nums))
    ```
- O(log n) - Logarithmic time complexity
    ```python
    def foo(x):
        n = len(x)
        print(x)
        if n <= 1:
            print("return")    
            return 17
        return foo(x[:n//2]) + foo(x[n//2:])
    ```


- O(n²) - Quadratic time complexity
    ```python
        for x in data:
            for y in data:
                print(x, y)
    ```
### Additional Resources
#### A friendly intro to Big O Notation
   - **Big O Notation** is a way of evaluating the performance of an algorithm.And it is a way to express the amount of time that a function, action, or algorithm takes to run based on how many elements we pass to that function.
   - Big O Notation takes into account: the *speed* and *efficiency* with which something functions when its input grows to be any (crazy big!) size.
   * **Basic Big O Notation Equations**
   ![O1&On](https://miro.medium.com/max/720/1*FC0XX0-9Vx7yCS0dTS2Zrw.jpeg)
        - An **O(1)** function takes *constant time*: it means that it doesn’t matter how many elements we have, or how huge our input is: it’ll always take the same amount of time and memory to run our algorithm. 
        - An **O(n)** function is *linear*(the upper bound on a function. (**Worst Case**)): which means that as our input grows (from ten numbers, to ten thousand, to ten million), the space and time that we need to run that algorithm grows linearly. 