# Class-01 
## Testing and Modules
![test](https://files.realpython.com/media/Getting-Started-with-Testing-in-Python_Watermarked.9f22be97343d.jpg)
### Reading
#### In Tests We Trust - TDD with Python
The most common things that programmers think about are refactoring and unit tests; so this article [1] gives you a gentle introduction to TDD with Python and how to do unit tests and how to refactor safely.
* **Unit tests and TDD?**
*Unit tests* are some pieces of code to exercise the input, the output and the behavior of your code. You can write them anytime you want.
*Test-Driven Development* "TDD":
    * baby steps, what is the smaller test that we can do against a function (method/class) that will return the output? so make a test by giving specific input and it should return specific output...
    * Important aspects about the unit test:
        - The test file name should follow the same name of module name
        - separate the tests folder from production code
        - structure : A convention widely used is the AAA: *Arrange, Act and Assert*.
    * The Cycle : 
    by doing these steps : 
        1. Write a unit test and make it fail 
        2. Write the feature and make the test pass!
        3. Refactor the code
    * TDD is not about the money/tests
        How we can grow our software design consciously and well, just building what is needed to make the test pass. When we are writing tests we are forced to think about the design first and how we can break it into small pieces.
#### If name equals main
Before executing code, Python interpreter reads source file and define few special variables/global variables.[2]
```
# Python program to execute
# main directly
print ("Always executed")
 
if __name__ == "__main__":
    print ("Executed when invoked directly")
else:
    print ("Executed when imported")
```
1. All of the code that is at indentation level 0 [Block 1] gets executed. Functions and classes that are defined are, well, defined, but none of their code runs.
2. execute file_name.py directly => ```__name__ = "__main__"``` 
output => Always executed & Executed when invoked directly
3. script is getting imported by some other module at that time ```__name__ = "module_name"```
output => Always executed & Executed when imported
* Advantages : 
    1. Every Python module has it’s __name__ defined and if this is __main__, it implies that the module is being run standalone by the user and we can do corresponding appropriate actions.
    2. If you import this script as a module in another script, the __name__ is set to the name of the script/module.
    3. Python files can act as either reusable modules, or as standalone programs.
    4. ```if __name__ == '__main__':``` is used to execute some code only if the file was run directly, and not imported.
#### Recursion
The process in which a function calls itself directly or indirectly is called **Recursion** and the corresponding function is called a **Recursive function** [3]
![recursion](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQv9z2N8p9xDkWa5MmQaox8vP2ho1Qku0vrcjF9O5FzRVhnGesSyRpQPBhXUPT1BFAAzzQ&usqp=CAU)
* **A recursive function** solves a particular problem by calling a copy of itself and solving smaller subproblems of the original problems.
* **Properties of Recursion**:
    * Performing the same operations multiple times with different inputs.
    * In every step, we try smaller inputs to make the problem smaller.
    * Base condition is needed to stop the recursion otherwise infinite loop will occur.
* Recursion uses **more memory**, because the recursive function adds to the stack with each recursive call, and keeps the values there until the call is finished. The recursive function uses LIFO (LAST IN FIRST OUT) Structure just like the stack data structure.
* The solution to the base case is provided and the solution to the bigger problem is expressed in terms of smaller problems. 
* If the base case is not reached or not defined, then the stack overflow problem may arise
* When any function is called from main(), the memory is allocated to it on the stack. A recursive function calls itself, the memory for a called function is allocated on top of memory allocated to the calling function and a different copy of local variables is created for each function call.

| SR No.| Recursion | 	Iteration |
  | --- | ----- |----- |
  |  1)   |   Terminates when the base case becomes true.    | Terminates when the condition becomes false.  |
  | 2)   |  Used with functions.    | Used with loops. | 
  |3) |  Every recursive call needs extra space in the stack memory.   | Every iteration does not require any extra space. | 
  |  4)   |  Smaller code size.    |  Larger code size. |
### Bookmark and Review
#### Google for Education: Python Lists
Python has a great built-in list type named "list". List literals are written within square brackets [ ]. Lists work similarly to strings -- use the len() function and square brackets [ ] to access data, with the first element at index 0.[4]
```
  colors = ['red', 'blue', 'green']
  print(colors[0])    ## red
  print(colors[2])    ## green
  print(len(colors))  ## 3
```
![list](https://developers.google.com/static/edu/python/images/list1.png)
* Assignment with an **=** on lists **DOES NOT** make a copy. Instead, assignment makes the two variables point to the one list in **memory**.
* **FOR and IN**
Python's *for* and *in* constructs are extremely useful, and the first use of them is with lists.
You can also use for/in to work on a string. The string acts like a list of its chars, so for ch in s: print(ch) prints all the chars in a string.
```
 squares = [1, 4, 9, 16]
  sum = 0
  for num in squares:
    sum += num
  print(sum)  ## 30
  if sum in squares:
    print(" sum is inside your list.")
```

* **Range**
The range(n) function yields the numbers 0, 1, ... n-1, and range(a, b) returns a, a+1, ... b-1 -- up to but not including the last number. The combination of the for-loop and the range() function allow you to build a traditional numeric for loop. 
```
 ## print the numbers from 0 through 99
  for i in range(100):
    print(i)
```
* **While Loop**
With the while loop we can execute a set of statements as long as a condition is true.
```
## Access every 3rd element in a list
  i = 0
  while i < len(a):
    print(a[i])
    i = i + 3
```
* **List Build Up**
One common pattern is to start a list as the empty list [], then use append() or extend() to add elements to it:
```
  list = []          ## Start as the empty list
  list.append('a')   ## Use append() to add elements
  list.append('b')
  ```
*  **List Slices**
Slices work on lists just as with strings, and can also be used to change sub-parts of the list.
![list methods](https://i.pinimg.com/736x/e0/75/b0/e075b06e44873cb327f7ac161175aeba.jpg)
#### Google for Education: Python Strings
* Python has a built-in string class named "**str**" with many handy features. String literals can be enclosed by either "double" or 'single' quotes.
* Python strings are "**immutable**" which means they cannot be changed after they are created.
* Characters in a string can be accessed using the standard [ ] syntax.
* The **str()** function converts values to a string form so they can be combined with other strings.
        ```
        pi = 3.14
        text = 'The value of pi is '  + str(pi) 
       ```
* **String Methods**
![string methods](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQHIRQZqjEgH45Brz7wLm5QxwQirijmsPrLnQ&usqp=CAU)
* **String formatting**
    * Formatted String Literals
    ```
    bugs = 'roaches'
    count = 13
    area = 'living room'
    print(f'Debugging {bugs=} {count=} {area=}')
    # Debugging bugs='roaches' count=13 area='living room'
    ```
    * The String format() Method
    ```
    print('We are the {} who say "{}!"'.format('knights', 'Ni'))
    # We are the knights who say "Ni!"
    ```
    * String %
    ```
    # Add parentheses to make the long line work:
  text = ("%d little pigs come out, or I'll %s, and I'll %s, and I'll blow your %s down."
    % (3, 'huff', 'puff', 'house'))
    ```
* **If Statement**
 The if statement alone tells us that if a condition is true it will execute a block of statements and if the condition is false it won't.
 ```
 if time_hour < 10: print('coffee')
  else: print('water')
 ```




### References:
* [[1]](https://code.likeagirl.io/in-tests-we-trust-tdd-with-python-af69f47e6932) 
* [[2]](https://www.geeksforgeeks.org/what-does-the-if-__name__-__main__-do/) 
* [[3]](https://www.geeksforgeeks.org/introduction-to-recursion-data-structure-and-algorithm-tutorials/)
* [[4]](https://developers.google.com/edu/python/lists)
