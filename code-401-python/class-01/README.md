# Class-01 
## Intro to Python

### A friendly intro to Big O Notation 
   * **Big O Notation** is a way of evaluating the performance of an algorithm.And it is a way to express the amount of time that a function, action, or algorithm takes to run based on how many elements we pass to that function.
   * Big O Notation takes into account: the *speed* and *efficiency* with which something functions when its input grows to be any (crazy big!) size.
   * **Basic Big O Notation Equations**
   ![O1&On](https://miro.medium.com/max/720/1*FC0XX0-9Vx7yCS0dTS2Zrw.jpeg)
     * An **O(1)** function takes *constant time*: it means that it doesn’t matter how many elements we have, or how huge our input is: it’ll always take the same amount of time and memory to run our algorithm. 
     * An **O(n)** function is *linear*(the upper bound on a function. (**Worst Case**)): which means that as our input grows (from ten numbers, to ten thousand, to ten million), the space and time that we need to run that algorithm grows linearly. 
-----------------------------------
### Facts and Myths about Python names and values
The behavior of names and values in Python can be confusing. Like many parts of Python, it has an underlying simplicity that can be hard to discern, especially if you are used to other programming languages. This video [1] explains how it all works, and presents some facts and myths along the way.
* **Fact:**
    * Names refer to values.
    * Many names can refer to one value. 
    * Names are reassigned independently of other names.
    * Values live until nothing references them.
    * Assignment never copies data.
    * Changes in a value are visible through all of its names. (Mutable Presto-Chango)
    * References can be more than just names.
    * Lots of things are assignment.
    * Python passes function arguments by assigning to them.

* **Myth:**
    * Python assigns mutable and immutable values differently.
    * Python has no variables.
    * Python is confusing.
--------------------------------------
### Awesome Python Environment
![awesome](https://files.realpython.com/media/Setting-Up-an-Effective-Terminal-Environment-for-Python-Development_Watermarked.856435b7bcb0.jpg)
* **The Interpreter.**
    > *pyenv* is a wonderful tool for managing multiple Python versions.use pyenv to install almost any python interpreter, including pypy, and anaconda.
* **Dependency Management**
    > *poetry* helps you to easily manage your projects’ dependencies, separate your projects through virtual environments, build both applications as well as libraries without headaches.
* **Consistent Formatting and Readability**
    > *Black* is a tool for python that allows you to focus on what is necessary, the content
    It does that by freeing you from manual code formatting through automation.
* **Type-Correctness**
    > *Mypy* is a static type checker for python code, that finds errors before they appear.
* **Automate the Automation**
    > *Pre-commit* is a tool that executes checks before you commit code to your repository 
-------------------------------------
### Python Module of the Week

* **PyMOTW-3** is a series of articles written by *"Doug Hellmann"* to demonstrate how to use the modules of the Python 3 standard library. It is based on the original PyMOTW series, which covered Python 2.7. [2]
    The site offers breakdowns of the Python Standard Library modules, including, but not limited to:

        Text Manipulation
        Data Structures
        Algorithms
        Cryptography
        Concurrency and Multithreading
        Internationalization
        Networking
-------------------------------------
### References:
* [[1]](https://www.youtube.com/watch?v=_AEJHKGk9ns) 
* [[2]](https://pymotw.com/3/index.html) 