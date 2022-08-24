# Class 04
## React and Forms

### React Docs - Forms
* What is a ‘Controlled Component’?
    An input form element whose value is controlled by React

* Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why.
    we update the state with their responses as soon as they enter them, since handleChange runs on every keystroke to update the React state, the displayed value will update as the user types.

* How do we target what the user is entering if we have an event handler on an input field?
    by adding an attribute to each element and letting the handler function target what to do based on the value of event.target.attributeName.

### The Conditional (Ternary) Operator Explained

* Why would we use a ternary operator?
    to improve the readability of the code

* Rewrite the following statement using a ternary statement:

    ```
    if(x===y){
    console.log(true);
    } else {
    console.log(false);
    }
    ```
```
(x===y)?  console.log(true) : console.log(false)
```
## Things I want to know more about
 Passing Functions Between Components and handling them.