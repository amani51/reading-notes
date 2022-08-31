# Class 10
## In memory storage

### Understanding the JavaScript Call Stack

* **What is a 'call'?**
A call stack is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions
* **How many 'calls' can happen at once?**
one call stack
* **What does LIFO mean?**
*Last In, First Out,* it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.

* **Draw an example of a call stack and the functions that would need to be invoked to generate that call stack.**
![](/download.png)
* **What causes a Stack Overflow?**
when programs try to use more memory than has been allocated, which can cause programs to terminate.
### JavaScript error messages

* **What is a 'reference error'?**
    when an attempt is made to reference a variable that does not exist or is out of scope.

* **What is a 'syntax error'?**
Syntax errors occur when the code has grammatical mistakes
* **What is a 'range error'?**
trying to pass a value as an argument to a function that does not allow a range that includes the value.
* **What is a type error'?**
when a variable or parameter is not of a valid type
* **What is a breakpoint?**
pause your program once execution reaches a certain point.
* **What does the word 'debugger' do in your code?**
 the process of analyzing how your program runs, how it generates data in order to find defects and issues in your code.


### References:
* [[1]](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack) 

