# Class-08
## Data Analysis with Pandas
### Reading
#### Pandas in 10
- **Pandas** is a software library written for the Python programming language for data manipulation and analysis.
- Pandas provide extended data structures to hold different types of labeled and relational data
![](https://i.imgur.com/zfxLzEv.png)
- A short introduction to pandas.

    -  **NumPy** arrays have one dtype for the entire array, while **pandas** DataFrames have one dtype per column
    - Creating a Series by passing a list of values, letting pandas create a default integer index
        ```python
        s = pd.Series([1, 3, 5, np.nan, 6, 8]) 
        ````
    - Creating a **DataFrame** by passing a NumPy array, with a datetime index using 'date_range()' and labeled columns
        ``` python
        dates = pd.date_range("20130101", periods=6)
        df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list("ABCD"))
        
                        A         B         C         D
        2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
        2013-01-02  1.212112 -0.173215  0.119209 -1.044236
        2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
        2013-01-04  0.721555 -0.706771 -1.039575  0.271860
        2013-01-05 -0.424972  0.567020  0.276232 -1.087401
        2013-01-06 -0.673690  0.113648 -1.478427  0.524988

        df.index # DatetimeIndex(['2022-01-01', '2022-01-02', '2022-01-03', '2022-01-04',
              # '2022-01-05', '2022-01-06'],
              #dtype='datetime64[ns]', freq='D')
        df.columns # Index(['A', 'B', 'C', 'D'], dtype='object')
        df.to_numpy() array([
        [ 0.4691, -0.2829, -1.5091, -1.1356],
        [ 1.2121, -0.1732,  0.1192, -1.0442],
        [-0.8618, -2.1046, -0.4949,  1.0718],
        [ 0.7216, -0.7068, -1.0396,  0.2719],
        [-0.425 ,  0.567 ,  0.2762, -1.0874],
        [-0.6737,  0.1136, -1.4784,  0.525 ]])
        df.describe() # shows a quick statistic summary of your data
                      A         B         C         D
        count  6.000000  6.000000  6.000000  6.000000
        mean   0.073711 -0.431125 -0.687758 -0.233103
        std    0.843157  0.922818  0.779887  0.973118
        min   -0.861849 -2.104569 -1.509059 -1.135632
        25%   -0.611510 -0.600794 -1.368714 -1.076610
        50%    0.022070 -0.228039 -0.767252 -0.386188
        75%    0.658444  0.041933 -0.034326  0.461706
        max    1.212112  0.567020  0.276232  1.071804
        df.T # to Transpose the data
           2013-01-01  2013-01-02  2013-01-03  2013-01-04  2013-01-05  2013-01-06
        A    0.469112    1.212112   -0.861849    0.721555   -0.424972   -0.673690
        B   -0.282863   -0.173215   -2.104569   -0.706771    0.567020    0.113648
        C   -1.509059    0.119209   -0.494929   -1.039575    0.276232   -1.478427
        D   -1.135632   -1.044236    1.071804    0.271860   -1.087401    0.524988
        ````
    - **DataFrame.to_numpy()** gives a NumPy representation of the underlying data , this can be an **expensive operation** when your DataFrame has columns with different data types, it *does not include the index or column labels in the output*
    - Creating a DataFrame by passing a **dictionary** of objects that can be converted into a series-like structure:
        ``` python
        df2 = pd.DataFrame(
            {
        "A": 1.0, # float64
        "B": pd.Timestamp("20130102"), # datetime64[ns]
        "C": pd.Series(1, index=list(range(4)), dtype="float32"), # float32
        "D": np.array([3] * 4, dtype="int32"), # int32
        "E": pd.Categorical(["test", "train", "test", "train"]), # category
        "F": "foo", #object
            }
        )
        A        B      C    D    E    F
        1.0 2013-01-02  1.0  3   test  foo
        1.0 2013-01-02  1.0  3  train  foo
        1.0 2013-01-02  1.0  3   test  foo
        1.0 2013-01-02  1.0  3  train  foo
        ````
    - Use **DataFrame.head()** and **DataFrame.tail()** to view the top and bottom rows of the frame respectively.
    - **Selection**
        - Selecting a single column, which yields a Series
            ```python
            df["A"]
            2013-01-01    0.469112
            2013-01-02    1.212112
            2013-01-03   -0.861849
            2013-01-04    0.721555
            2013-01-05   -0.424972
            2013-01-06   -0.673690
            Freq: D, Name: A, dtype: float64
            ```
        - Selecting via [] (__getitem__), which slices the rows:
            ```python
            df[0:3] # =df["20130101":"20130103"]
                               A         B         C         D
            2013-01-02  1.212112 -0.173215  0.119209 -1.044236
            2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
            2013-01-04  0.721555 -0.706771 -1.039575  0.271860
            ```
        - get a cross section using a label
            ```python
            df.loc[dates[0]]
            A    0.469112
            B   -0.282863
            C   -1.509059
            D   -1.135632
            Name: 2013-01-01 00:00:00, dtype: float64
            ```
        - Showing label slicing, both endpoints
            ```python
            df.loc["20130102":"20130104", ["A", "B"]]
                            A         B
                2013-01-02  1.212112 -0.173215
                2013-01-03 -0.861849 -2.104569
                2013-01-04  0.721555 -0.706771
            ```
        - Select via the position of the passed integers:
            ```python
            df.iloc[3]
            Out[32]: 
            A    0.721555
            B   -0.706771
            C   -1.039575
            D    0.271860
            Name: 2013-01-04 00:00:00, dtype: float64
            ```
    - **Boolean indexing**
        - Using a single column’s values to select data:
            ```python
            df[df["A"] > 0]
                        A         B         C         D
            2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
            2013-01-02  1.212112 -0.173215  0.119209 -1.044236
            2013-01-04  0.721555 -0.706771 -1.039575  0.271860
            ```
        - Selecting values from a DataFrame where a boolean condition is met.
            ```python
                df[df > 0]
                            A         B         C         D
            2013-01-01  0.469112       NaN       NaN       NaN
            2013-01-02  1.212112       NaN  0.119209       NaN
            2013-01-03       NaN       NaN       NaN  1.071804
            2013-01-04  0.721555       NaN       NaN  0.271860
            2013-01-05       NaN  0.567020  0.276232       NaN
            2013-01-06       NaN  0.113648       NaN  0.524988
            ```
        -  Using the **isin()** method for filtering
            ```python
            df2["E"] = ["one", "one", "two", "three", "four", "three"]
            df2[df2["E"].isin(["two", "four"])]
            Out[44]: 
                            A         B         C         D     E
            2013-01-03 -0.861849 -2.104569 -0.494929  1.071804   two
            2013-01-05 -0.424972  0.567020  0.276232 -1.087401  four
            ```
    - **Setting**
        - Setting a new column automatically aligns the data by the indexes.
            ```python
            s1 = pd.Series([1, 2, 3, 4, 5, 6], index=pd.date_range("20130102", periods=6))
            2013-01-02    1
            2013-01-03    2
            2013-01-04    3
            2013-01-05    4
            2013-01-06    5
            2013-01-07    6
            Freq: D, dtype: int64
            df.at[dates[0], "A"] = 0 # Setting values by label
            df.loc[:, "D"] = np.array([5] * len(df)) # Setting by assigning with a NumPy array
            ```
- **Missing data**
    - pandas primarily uses the value **np.nan** to represent missing data. It is by default not included in computations.
    - Reindexing allows you to change/add/delete the index on a specified axis
    ```python
        df1 = df.reindex(index=dates[0:4], columns=list(df.columns) + ["E"])

        df1.loc[dates[0] : dates[1], "E"] = 1
                        A         B         C  D    F    E
        2013-01-01  0.000000  0.000000 -1.509059  5  NaN  1.0
        2013-01-02  1.212112 -0.173215  0.119209  5  1.0  1.0
        2013-01-03 -0.861849 -2.104569 -0.494929  5  2.0  NaN
        2013-01-04  0.721555 -0.706771 -1.039575  5  3.0  NaN
    ```
- **Operations**
    - **Stats**: Operations in general exclude missing data
    ```python
    df.mean()
    A   -0.004474
    B   -0.383981
    C   -0.687758
    D    5.000000
    F    3.000000
    dtype: float64
    ```

