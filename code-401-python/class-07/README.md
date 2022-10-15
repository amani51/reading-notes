# Class-07
## Data Analysis
### Reading
#### What is Jupyter Lab
- **Data analysis** is the practice of working with data to glean useful information, which can then be used to make informed decisions.
- **JupyterLab** is a next-generation web-based user interface for Project Jupyter.
![](https://cdn.hackersandslackers.com/2019/03/jupyter.jpg)
- JupyterLab enables you to **work with documents** and **activities** such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner.
- **Text, Code consoles, & Terminals**
    - **Text editor** and Jupiter includes syntax highlighting and configurable indentation create a cold consul for your text by clicking on " New Console for Editor" then selecting a **kernel**
    - **Terminals** in Jupiter provide full support for system shells on Mac,Linux and PowerShell on Windows including programs like at vim or Emacs hack away to your heart's content.
    - **Common Formats**
    All popular image formats are supported as standalone files and in notebooks after opening them up some super useful keyboard shortcuts are **- /= to zoom in/out**, **[ ] rotate left/right** and **0 to reset** . PDFs are viewed easily as is HTML and latex.
    - **JSON** files can be edited as cell outputs searchable tree views they go to point X and **.VEGA** light one point X files can be rendered as files or cell outputs.
- **Jupiter notebook** is anew way to work easily with data and code seamlessly together.and it has two modes.
    1. **command mode** is designed for easily navigating and changing the framework of your book. 
    2. **edit mode** pressed M for write in a markdown language, pressed Y for write in a python language

#### Numpy Tutorial
- **NumPy** is a commonly used Python data analysis package.
- you can read a **ssv file** in python by using csv library that convert ";" to ","
```python 
import csv
with open('file_name.csv', 'r') as f:
    read_ssv = list(csv.reader(f, delimiter=';'))
```
- **Numpy 2-Dimensional Arrays**
    - In a NumPy array, the number of **dimensions** is called the **rank**, and each dimension is called an axis. So the **rows** are the **first axi**s, and the **columns** are the **second axis**.
    - One of the limitations of NumPy is that all the elements in an array have to be of the *same type.*
    ```python 
    import csv
    with open('file_name.csv', 'r') as f:
        ssv_csv = list(csv.reader(f, delimiter=';'))
    import numpy as np
    ssv_csv = np.array(ssv_csv[1:], dtype=np.float)
    ```
    - We can check the number of rows and columns in our data using the shape property of NumPy arrays
    ```python 
    ssv_csv.shape # (1599, 12) 1599=>rows,12=>columns
    ```
    - There are a variety of methods that you can use to create NumPy arrays
    ```python 
    empty_array = np.zeros((3,4)) # create an array with 3 rows and 4 columns, where every element is 0
    np.random.rand(3,4) # an array where each element is a random number.
    ```
    - **Using NumPy To Read In Files** 
        - It’s possible to use NumPy to directly read csv or other files into arrays. We can do this using the *numpy.genfromtxt function*.
        ```python 
        ssv_csv = np.genfromtxt("file_name.csv", delimiter=";", skip_header=1)
        ```
        -  NumPy will automatically pick a data type for the elements in an array based on their format.
    - **Indexing NumPy Arrays**
        - NumPy is zero-indexed, meaning that the index of the first row is 0, and the index of the first column is 0.
        ```python
        ssv_csv[2,3] #The first index is the row, or axis 1, index, and the second index is the column, or axis 2, index.
        ssv_csv[0:3,3] #the first three items from the fourth column
        ssv_csv[:,:] #the entire array
        ```
        - We can also use indexing to assign values to certain elements in arrays
        ```python 
        ssv_csv[1,5] = 10 
        ssv_csv[:,10] = 50 # overwrites all the values in the eleventh column with 50
        ```
- **1-Dimensional NumPy Arrays**
    - Each row and column in a 2-dimensional array is a 1-dimensional array.
    ```python
    third_row = ssv_csv[3,:]
    third_row[1] # second item in third_row
    np.random.rand(3) #generate a random vector
    ```

- **N-Dimensional NumPy Arrays**
    ```python
    earnings = [
    [
        [500,505,490],
        [810,450,678],
        [234,897,430],
        [560,1023,640]
    ],
    [
        [600,605,490],
        [345,900,1000],
        [780,730,710],
        [670,540,324]
    ]
    ]
    earnings = np.array(earnings)
    earnings[0,0,0] # 500
    earnings.shape # (2, 4, 3)
    earnings[:,0,0] #[500, 600]
    earnings[:,0,:] #[[500, 505, 490], [600, 605, 490]]
    ```
    - We now need three indexes to retrieve a single element
- **NumPy Data Types**
    - The core of NumPy is written in a programming language called C, which stores data differently than the Python data types. *NumPy data types map between Python and C*, allowing us to use NumPy arrays without any conversion hitches.
    ```python
    ssv_csv.dtype # float64 
    ```
    - Data types additionally end with a suffix that indicates how many bits of memory they take up. So **int32** is a **32 bit integer data type**, and **float64** is a **64 bit float data type**.
    ```python
    int_conv= ssv_csv.astype(int) # convert an array to a different type
    
    ```
    - The method will actually copy the array, and return a new array with the specified data type
    ```python
    int_conv.dtype.name # int64
    ```
- **NumPy Array Operations**
    - Single Array Math:
    If you do any of the basic mathematical operations (/, *, -, +, ^) with an array and a value, it will apply the operation to each of the elements in the array.
    ```python
    ssv_csv[:,11] + 10 # [ 15., 15., 15., ..., 16., 15., 16.]
    ssv_csv[:,11] += 10
    ```
    - Multiple Array Math:
    ```python
    ssv_csv[:,11] + ssv_csv[:,11] # = ssv_csv[11] * 2 
    ```
- ***Broadcasting***
    NumPy performs broadcasting to try to match up elements. Essentially, broadcasting involves a few steps:

    -  The last dimension of each array is compared.
        - If the dimension lengths are equal, or one of the dimensions is of length 1, then we keep going.
        - If the dimension lengths aren’t equal, and none of the dimensions have length 1, then there’s an error.
    - Continue checking dimensions until the shortest array is out of dimensions.
    ```python 
    array_one = np.array(
    [
        [1,2],
        [3,4]
    ]
    )
    array_two = np.array([4,5])
    array_one + array_two # [[5, 7],[7, 9]]
  ```
- **NumPy Array Comparisons**
    - NumPy makes it possible to test to see if rows match certain values using mathematical comparison operations like <, >, >=, <=, and ==.
    ```python 
    ssv_csv[:,11] > 5 # [False, False, False, ..., True, False, True], dtype=bool
    ```

