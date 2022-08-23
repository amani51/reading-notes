# Class 03
## Passing Functions as Props

### React Docs - lists, and keys
> The map() method creates a new array populated with the results of calling a provided function on every element in the calling array.[1]
* What does .map() return?
return a different element to take the place of the element from the original array. 

* If I want to loop through an array and display each value in JSX, how do I do that in React?
by using the JavaScript map() function.

* Each list item needs a unique 
key.

* What is the purpose of a key?
A “key” is a special string attribute you need to include when creating lists of elements.

### The Spread Operator
* What is the spread operator?
The spread operator is a useful and quick syntax for adding items to arrays, combining arrays or objects, and spreading an array out into a function’s arguments.[2]

* List 4 things that the spread operator can do.
> * Copying an array
> * Concatenating or combining arrays
> * Using Math functions
> * Using an array as arguments


* Give an example of using the spread operator to combine two arrays.
```
const arr1 = [1,2,3]
const arr2 = [4,5,6]
const arr3 = [...arr1, ...arr2] //arr3 ==> [1,2,3,4,5,6]
```

* Give an example of using the spread operator to add a new item to an array.
```
const odd = [1,3,5];
const add = [2,...odd, 4,6];
//add=[[ 2, 1, 3, 5, 4, 6 ]]
```

* Give an example of using the spread operator to combine two objects into one.
```
let person= {
    firstName: 'Eslam',
    lastName: 'AL-Zoubi',
    age: 22,
};
let job = {
    jobTitle: 'Teacher',
    location: 'Jordan'
};
let employee = {
    ...person,
    ...job
};
//output={
    firstName: 'Eslam',
    lastName: 'AL-Zoubi',
    age: 22,
    jobTitle: 'Teacher',
    location: 'Jordan'
}
```
* How to Pass Functions Between Components
    call a method in the child component and pass that method as a prop to the child component, and use this. prop.methodName
* In the [video](https://youtu.be/c05OL7XbwXU), what is the first step that the developer does to pass functions between components?
pass the people object into increment  function by using the map method 

* In your own words, what does the increment function do?
it increases the value of "state" for the people's object by updating the count value on what name has passed in

* How can you pass a method from a parent component into a child component?
    1. parent component defines a function
    2. pass  the function as a prop to a child component
    3. child component invokes the prop
    4. call the parent function.
    5. parent component is re-rendered along with its children 

* How does the child component invoke a method that was passed to it from a parent component?
by using " this.methodName "

## Things I want to know more about
 Passing Functions Between Components

### References:
* [[1]](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) 
* [[2]](https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab) 