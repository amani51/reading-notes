# Class-33
## Next- Forms and Conditional Rendering 
### Custom Hooks
- Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.
- In simple terms, the React Hooks are the new feature that was introduced with the release of React 16.8 version, and it allows us to use various class-based component features such as state and other React features without using a class-based syntax. The hooks are the functions that allow us to hook React state and lifecycle methods approach into the function components. One thing to be remembered is that hooks won't work with the class-based component. The React hooks are backward-compatible, which means that it does not contain any breaking changes and allow us to write clear function components.
- **What are the benefits of using Hooks?**


    - It revolutionizes the way you write components

    - You can write concise and clearer code.

    - Hooks are simpler to work with and test. Code would appear cleaner and easier to read.

    - A related logic could be tightly coupled inside a custom hook. 

    - It simplifies how to make code more composable and reusable. 

    - Unlike HOCs, they don’t create another element in DOM.

    - Hooks would work more efficiently with the future React optimizations. For example, it would work ahead of time compilation as well as components folding.

    - Components folding may be implemented in the future. It suggests that for code elimination at compile-time, hooks are simple to reuse the stateful logic
### Lifting State Up
- Lifting state involves writing more “boilerplate” code than two-way binding approaches, but as a benefit, it takes less work to find and isolate bugs. Since any state “lives” in some component and that component alone can change it, the surface area for bugs is greatly reduced.
- The components need to share some state, some todo state. You need to share that todo state order to display the number of todos as well as to update your todo list.
### Memoization in React
- Memoization is an optimization technique that allows an increase in the performance of a program by storing the results of some expensive function so that we don’t need to call that function when the same inputs are given.
- Memoization can increase performance for some functions. But, if we use it for every component rendering, it might decrease performance since it stores results that increase memory used for the program. We should only use memoization when there is a clear benefit for doing so.
- To utilize useMemo we need to pass a create function and an array of dependencies. useMemo optimizes performance by recomputing the memoized value only when one of the passed dependencies changes.
    ```python
    /* use of useMemo hook for memoization */
    const valueMemoized = useMemo(() => computeExpensiveValue(a, b), [a, b]);
    ```
- 