# Class-09
## Linkedlist
### Reading
#### What is the data structure
- A **data structure** is a specialized format for organizing, processing, retrieving and storing data. There are several basic and advanced types of data structures, all designed to arrange data to suit a specific purpose. Data structures make it easy for users to access and work with the data they need in appropriate ways.

- Data Structures are necessary for *designing efficient algorithms*. It provides reusability and abstraction. Using appropriate data structures can help programmers save a good amount of time while performing operations such as **storage**, **retrieval**, or **processing** of data. Manipulation of large amounts of data is easier.
-  Five factors to consider when picking a data structure include the following:
    1. What kind of information will be stored?
    2. How will that information be used?
    3. Where should data persist, or be kept, after it is created?
    4. What is the best way to organize the data?
    5. What aspects of memory and storage reservation management should be considered?
- In general, data structures are used **to implement the physical forms of abstract data types**. Data structures are a crucial part of designing efficient software. They also play a critical role in algorithm design and how those algorithms are used within computer programs.
- **Examples of using data structures**:
    - Storing data
    - Managing resources and services
    - Data exchange.
    - Ordering and sorting
    - Indexing
    - Searching
- **Characteristics of data structures**
    - **Linear or non-linear**
    ![](https://media.geeksforgeeks.org/wp-content/uploads/20191010170332/Untitled-Diagram-183.png)
    - **Homogeneous or heterogeneous**. 
    This characteristic describes whether all data items in a given repository are of the same type. One example is a collection of elements in an array, or of various types, such as an abstract data type defined as a structure in C or a class specification in Java.
    - **Static or dynamic**
    ![](https://beginnersbook.com/wp-content/uploads/2018/10/DS_Classification.jpg)
- **Types of data structures**
    - **Array**: An array stores a collection of items at adjoining memory locations. Items that are the same type are stored together so the position of each element can be calculated or retrieved easily by an index. Arrays can be fixed or flexible in length.
    ![](https://cdn.ttgtmedia.com/rms/onlineimages/sqlserver-one_dimensional_array_four_elements-f.png)
    - **Stack**. A stack stores a collection of items in the linear order that operations are applied. This order could be last in, first out (LIFO) or first in, first out (FIFO).
    - **Queue**. A queue stores a collection of items like a stack; however, the operation order can only be first in, first out.
    - **Linked** list. A linked list stores a collection of items in a linear order. Each element, or node, in a linked list contains a data item, as well as a reference, or link, to the next item in the list.
    - **Tree**. A tree stores a collection of items in an abstract, hierarchical way. Each node is associated with a key value, with parent nodes linked to child nodes -- or subnodes. There is one root node that is the ancestor of all the nodes in the tree.
    ![](https://cdn.ttgtmedia.com/rms/onlineimages/sqlserver-binary_search_tree-f.png)
    - **Heap**. A heap is a tree-based structure in which each parent node's associated key value is greater than or equal to the key values of any of its children's key values.
    - **Graph**. A graph stores a collection of items in a nonlinear fashion. Graphs are made up of a finite set of nodes, also known as vertices, and lines that connect them, also known as edges. These are useful for representing real-world systems such as computer networks.
    - **Trie**. A trie, also known as a keyword tree, is a data structure that stores strings as data items that can be organized in a visual graph.
    - **Hash table**. A hash table -- also known as a hash map -- stores a collection of items in an associative array that plots keys to values. A hash table uses a hash function to convert an index into an array of buckets that contain the desired data item.
    ![](https://cdn.ttgtmedia.com/rms/onlineimages/sqlserver-hash_table_example-f.png)
#### Linked List
- **Linked List** is a sequence of links which contains items. Each link contains a **connection to another link**. Linked list is the second most-used data structure after array.
- The important terms. 
    - **Link** − Each link of a linked list can store a data called an element.
    - **Next** − Each link of a linked list contains a link to the next link called Next.
    - **LinkedList** − A Linked List contains the connection link to the first link called First.
- **Linked List Representation**
    - Linked list can be visualized as a chain of nodes, where every node points to the next node.
    ![](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list.jpg)
        - Linked List contains a link element called first.
        - Each link carries a data field(s) and a link field called next.
        - Each link is linked with its next link using its next link.
        - Last link carries a link as null to mark the end of the list
- **Types of Linked List**
![](https://miro.medium.com/max/1400/0*4zUyzf2X2sLWP118.png)
- **Basic Operations**
    - *Insertion*
    ![](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list_insertion_0.jpg)
    ![](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list_insertion_1.jpg)
    ![](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list_insertion_2.jpg)
    ![](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list_insertion_3.jpg)
    - *Deletion*
    ![](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list_deletion_0.jpg)
    1[](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list_deletion_1.jpg)
    ![](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list_deletion_2.jpg)
    ![](https://www.tutorialspoint.com/data_structures_algorithms/images/linked_list_deletion_3.jpg)
    - *Display*: Displays the complete list.
    - *Search*: Searches an element using the given key.
    - *Delete*: Deletes an element using the given key.