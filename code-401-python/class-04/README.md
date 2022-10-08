# Class-04
## FileIO & Exceptions
### Reading
#### Read & Write Files in Python
![img](https://files.realpython.com/media/Reading-and-Writing-Files-in-Python_Watermarked.0d394921fd90.jpg)
* What Is a File?
    * It is a **contiguous set of bytes used to store data**. This data is organized in a specific format and can be anything as simple as a text file or as complicated as a program executable. In the end, these byte files are then **translated into binary 1 and 0** for easier processing by the computer.
    * The main parts of file systems:
        1. **Header**
        2. **Data**
        3. **End of file (EOF)**
    * the major parts of *File Paths*:
        1. **Folder Path**
        2. **File Name**
        3. **Extension**
    * The **line ending** has its roots from back in the Morse Code era, and it should use the sequence of the Carriage Return (CR or \r) and the Line Feed (LF or \n) characters (CR+LF or \r\n). 
    * An **encoding** is a translation from byte data to human readable characters.
* Opening and Closing a File in Python
    ```python 
    # 1. use try & finally method 
    reader = open('dog_breeds.txt')
    try:
        # Further file processing goes here
    finally:
        reader.close()
    # 2. use with method 
    with open('dog_breeds.txt') as reader:
        # Further file processing goes here
    ```
    * categories of file objects:
        * Text files `open('abc.txt', 'r')`
        * Buffered binary files `open('abc.txt', 'rb')`
        * Raw binary files `open('abc.txt', 'rb', buffering=0)`
* Reading and Writing Opened Files
    * Read methods:
        * `.read(size=-1)`: This reads from the file based on the number of *size* bytes.
        * `.readline(size=-1)`: This reads at most *size* number of characters from the line
        * `.readlines()`: This reads the remaining lines from the file object and returns them as a list.
    * Write methods:
        * `.write(string)`: This writes the string to the file.
        * `.writelines(seq)`:This writes the sequence to the file. No line endings are appended to each sequence item.
#### Exceptions in Python
![img](https://files.realpython.com/media/intro.8915db1758d8.png)
* **Syntax errors** occur when the parser detects an incorrect statement.
* **exception errors** occur whenever syntactically correct Python code results in an error
    ```python 
    print( 0 / 0 ))
                  ^
    # SyntaxError: invalid syntax
    print( 0 / 0 )
    # exception error ==> ZeroDivisionError: integer division or modulo by zero 

    ```
* **Raising an Exception**
    use **raise** to throw an exception if a condition occurs. The statement can be complemented with a custom exception.
    ```python 
    x = 10
    if x > 5:
        raise Exception('x should not exceed 5. The value of x was: {}'.format(x))
    # Exception: x should not exceed 5. The value of x was: 10
    ```
* **AssertionError Exception**
    The assert keyword is used when debugging code. The assert keyword lets you test if a condition in your code returns True, if not, the program will raise an AssertionError. 
    ```python
    import sys
    assert ('linux' in sys.platform), "This code runs on Linux only."
    # AssertionError: This code runs on Linux only.
    ```
* The **try** and **except** Block: Handling Exceptions
    It is used to catch and handle exceptions. Python executes code following the try statement as a “normal” part of the program. The code that follows the except statement is the program’s response to any exceptions in the preceding try clause.
    ```python 
    def linux_interaction():
        assert ('linux' in sys.platform)
        print('Doing something.')
    try:
        linux_interaction()
    except:
        print('Linux function was not executed')
    ```
* **Else Clause**
    lets you code sections that should run only when no exceptions are encountered in the try clause.
    ```python 
    try:
        linux_interaction()
    except AssertionError as error:
        print(error)
    else:
        print('Executing the else clause.')
    ```
* **Cleaning Up After Using finally**
    Enables you to execute sections of code that should always run, with or without any previously encountered exceptions.
    ```python 
    try:
        linux_interaction()
    except AssertionError as error:
        print(error)
    else:
        try:
            with open('file.log') as file:
                read_data = file.read()
        except FileNotFoundError as fnf_error:
            print(fnf_error)
    finally:
        print('Cleaning up, irrespective of any exceptions.')
    ```

