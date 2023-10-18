# Decorator Pattern

### Introduction
- **Purpose**
  - Allows for the **dynamic wrapping** of objects in order to **modify their existing responsibilities** and behaviors.
- **Use When**
  - Object responsibilities and behaviors should be dynamically modifiable.
  - Concrete implementions should be decoupled from responsibilities and behaviors.
  - Subclassing to achieve modification is impratical or impossible.
  - Specific functionality should not reside high in the object hierarchy.
  - A lot of little objects surrounding a concrete implementation is acceptable.
- **Characteristics**
  - We can use one or more decorators to wrap an object.
  - **Decorators have the same super type as the objects they decorate.**
  - We can decorate objects **dynamically** at runtime with as many decorators as we want.
- **Design Principle**
  - Open-Closed Principle (OCP)
- **Mechanisms**
  - Uses object composition and delegation
  - Decorator class mirrors the type of components they are decorating.
    - We can wrap a component with any number of decorators
- **Advantages**
  - attaches **additional responsibilities** to an object **dynamically**
  - **flexible alternative** to **subclassing for extending functionality**
- **Disadvantages**
  - can generate a lot of small classes (ex. Java I/O)
  - hard to understand if not familiar with the pattern
