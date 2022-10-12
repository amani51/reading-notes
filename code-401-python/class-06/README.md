# Class-06
## OOP Part02
### Reading
#### What are Design Patterns
- a software **design pattern** is a general, reusable solution to a commonly occurring problem within a given context in software design. It is not a finished design that can be transformed directly into source or machine code.
![](https://jtmmartins.github.io/2017/11/25/Patterns/designpatterns.jpg)
- The difference between, **Programming Paradigms**, **Architectural Patterns**, **Design Patterns** and Design Principles:
    - **Programming Paradigms**: A way to classify programming languages based on their coding styles and features.
    - **Architectural Patterns**: Reusable solution to a commonly occurring problem in software architecture within a given context. 
    - **Design Patterns**: Reusable solution to a commonly occurring problem in software design within a given context.
    - **Design Principles**: Represent a set of guidelines that help developers to avoid having a bad design.
- The 3 major types of design patterns:
![](https://miro.medium.com/max/720/1*UYaL9INxMRYSvMbZo_Vivw.png)
    - **Creational Patterns**: provide ways to instantiate single or groups of objects. Making it easier to create objects in a way that suits the situation.
    - **Structural Patterns**: provide a manner to define relationships between classes or objects. Making it easier for these entities to work together.
    - **Behavioral Patterns**:define manners of communication between classes and objects. Making it easier and more flexible for these entities to communicate.

#### Risk Analysis
- It is the process of identifying the risks in applications or software that you built and prioritizing them to test.
- Using it at the beginning of a project highlights the potential problem areas. When a test plan has been created, risks involved in testing the product are to be taken into consideration along with the possibility of the damage they may cause to your software along with solutions.
- A list of possible risks that you could **encounter**:
    1. Use of new hardware.
    2. Use of new technology.
    3. Use of new automation tool.
    4. The sequence of code.
    5. Availability of test resources for the application.
- A certain risks that are **unavoidable**:
    1. The **time** that you allocated for **testing**
    2. A **defect leakage** due to the complexity or size of the application
    3. Urgency from the **clients** to deliver the project
    4. Incomplete requirements

- **Risk Identification**:
    1. Business Risks
    2. Testing Risks
    3. Premature Release Risk
    4. Software Risks
- **Risk Assessment**
![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2019/08/Picture1-528x290.png)

- Perspectives of Risk Assessment:
    - Effect
    - Cause
    - Likelihood

- steps to perform Risk Analysis:
    1. Searching the risk
    2. Analyzing the impact of each individual risk
    3. Measures for the risk identified

#### Dependency Injection
- It is transferring the task of creating the object to someone else and directly using the dependency.
- **Types of dependency injection**:
    1. **constructor injection**: the dependencies are provided through a class constructor.
        ```python class Client:
        def __init__(self, foo: Foo, bar: Bar):
            if foo is None:
                raise ValueError("foo must be provided")
            if bar is None:
                raise ValueError("bar must be provided")
            self.foo = foo
            self.bar = bar
            
        def do_something(self):
            self.foo.do_something()
            self.bar.do_something_else()

        ```
    2. **setter injection**: the client exposes a setter method that the injector uses to inject the dependency.
        ```python 
        class Client:
        def __init__(self):
            self.foo = None
            self.bar = None

        def set_foo(self, foo: Foo):
            if foo is None:
                raise ValueError("foo must be provided")
            self.foo = foo

        def set_bar(self, bar: Bar):
            if bar is None:
                raise ValueError("foo must be provided")
            self.bar = bar

        def validate_dependencies(self):
            if self.foo is None:
                raise ValueError("foo has not been set")
            if self.bar is None:
                raise ValueError("bar has not been set")

        def do_something(self):
            self.validate_dependencies()

            self.foo.do_something()
            self.bar.do_something_else()

        ```
    3. **interface injection**: the dependency provides an injector method that will inject the dependency into any client passed to it. 
- The **responsibility** of dependency injection’s :
    1. Create the objects
    2. Know which classes require those objects
    3. Provide them all those objects. 

| Benefits of using DI  | Disadvantages of DI |
| ------------- | ------------- |
| Helps in Unit testing  |  complex to learn  |
| Boiler plate code is reduced  | Many compile time errors are pushed to run-time. |
| Extending the application becomes easier  | Dependency injection frameworks are implemented with reflection or dynamic programming  |



