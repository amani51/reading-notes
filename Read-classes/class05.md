# Class 05
## Readings: Putting it all together
### React Docs - Thinking in React

* **What is the single responsibility principle and how does it apply to components?**
    a component should ideally only do one thing.
Separate UI into components, where each component matches one piece of data 
* **What does it mean to build a ‘static’ version of your application?**
 takes your data model and renders the UI but has no interactivity
* **Once you have a static application, what do you need to add?**
build components that reuse other components and pass data using props.
* **What are the three questions you can ask to determine if something is state?**
    > 1. Is it passed in from a parent via props? If so, it probably isn’t state.
    > 2. Does it remain unchanged over time? If so, it probably isn’t state.
    > 3. Can you compute it based on any other state or props in your component? If so, it isn’t state.

* **How can you identify where state needs to live?**
    > 1. Identify every component that renders something based on that state.
    > 2. Find a common owner component (a single component above all the components that need the state in the hierarchy).
    > 3. Either the common owner or another component higher up in the hierarchy should own the state.
    > 4. If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

 ### Higher-Order Functions

* **What is a “higher-order function”?**
    Functions that operate on other functions, either by taking them as arguments or by returning them
* **Explore the greaterThan function as defined in the reading. In your own words, what is line 2 of this function doing?**
    it takes a number as an initial or first number and compares it with another number and returns true if the new number is greater than it
* **Explain how either map or reduce operates, with regards to higher-order functions.**
*map* : transforming an array by putting each element through a function
*reduce* : combine all the elements in an array into a single value
## Things I want to know more about
difference between filter , map,reduce,foreach...