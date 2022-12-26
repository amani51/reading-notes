# Class-31
## React Review
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRiiEFgK5MqjqfovnQmeDWCOkRlWc3zpHNKaw&usqp=CAU)
#### Component-Based Architecture
- **Component architecture** is a way to build software based on reusable components that can easily be combined and changed.
- **What is a Component?**
    A component is a modular, portable, replaceable, and reusable set of well-defined functionality that encapsulates its implementation and exporting it as a higher-level interface.
- **Views of a Component**
    - `Object-oriented view`:
    A component is viewed as a set of one or more cooperating classes. 
    - `Conventional view`:
    It is viewed as a functional element or a module of a program that integrates the processing logic, the internal data structures that are required to implement the processing logic and an interface that enables the component to be invoked and data to be passed to it.
    - `Process-related view`:
    The system is building from existing components maintained in a library
- **Characteristics of Components**
    - Reusability 
    - Replaceable 
    - Not context specific
    - Extensible 
    - Encapsulated
    - Independent 
- **Principles of Component−Based Design**
![](https://www.tutorialspoint.com/software_architecture_design/images/principles_of_component_based_design.jpg)
    - The software system is decomposed into reusable, cohesive, and encapsulated component units.

    - Each component has its own interface that specifies required ports and provided ports.

    - A component should be extended without the need to make internal code or design modifications to the existing parts of the component.

    - Depend on abstractions component do not depend on other concrete components.

    - Connectors connected components, specifying and ruling the interaction among components. 

    - Components interaction can take the form of method invocations, asynchronous invocations, broadcasting, message driven interactions, data stream communications, and other protocol specific interactions.

- **Advantages**
    - Ease of deployment
    - Reduced cost
    - Ease of development
    - Reusable 
    - Modification of technical complexity 
    - Reliability 
    - System maintenance and evolution 
    - Independent