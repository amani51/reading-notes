# Class-05
## Intro to OOP
### Reading
#### Classes and Objects
- **Object-oriented programming** is a programming paradigm that provides a means of structuring programs so that properties and behaviors are bundled into individual objects.
- **Objects** are an encapsulation of variables and functions into a single entity. Objects get their variables and functions from classes.
- **Classes** are essentially a template to create your objects.
```python
    class MyClass:
        variable = "blah"

        def function(self):
            print("This is a message inside the class.")

    myobjectx = MyClass()
    print(myobjectx.variable) #output => blah
    myobjectx.function() #output => This is a message inside the class.
```
- **\_\_init\_\_()** function, is a special function that is called when the class is being initiated. It's used for assigning values in a class.
```python
class NumberHolder:

   def __init__(self, number):
       self.number = number
```
#### Thinking Recursively
![img](https://files.realpython.com/media/Thinking-Recursively-in-Python_Watermarked.db67ac63aeb5.jpg)
- A recursive function is a function defined in terms of itself via self-referential expressions.
- This means that the function will continue to call itself and repeat its behavior until some condition is met to return a result. All recursive functions share a common structure made up of two parts: **base case** and **recursive case**.
- Behind the scenes, each recursive call adds a stack frame (containing its execution context) to the call stack until we reach the base case.
![case](https://files.realpython.com/media/stack.9c4ba62929cf.gif)
- When dealing with recursive functions, keep in mind that each recursive call has its own execution context, so to maintain state during recursion you have to either:

    - Thread the state through each recursive call so that the current state is part of the current call’s execution context.
    - Keep the state in global scope.
- **A data structure** is recursive if it can be deﬁned in terms of a smaller version of itself. A **list** is an example of a recursive data structure. 
- Recursive data structures and recursive functions go together. The recursive function’s structure can often be modeled after the definition of the recursive data structure it takes as an input.
- Python doesn’t have support for *tail-call elimination*. As a result, you can cause a stack overflow if you end up using more stack frames than the default call stack depth.
#### Pytest Fixtures and Coverage
- **Fixtures**
    Fixtures are used to feed some data to the tests such as database connections, URLs to test and some sort of input data. Therefore, instead of running the same code for every test, we can attach fixture function to the tests and it will run and return the data to the test before executing each test.
    ```python
    @pytest.fixture
    def input_value():
        input = 39
        return input

    def test_divisible_by_3(input_value):
        assert input_value % 3 == 0

    def test_divisible_by_6(input_value):
        assert input_value % 6 == 0
    ```
- **Coverage**
    It is a tool for measuring code coverage of Python programs. It monitors your program, noting which parts of the code have been executed, then analyzes the source to identify code that could have been executed but was not. Coverage measurement is typically used to gauge the effectiveness of tests.

    ![]()