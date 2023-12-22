# Composite Pattern

### Introduction
- **Purpose**
  - Facilitates the creation of **object hierarchies** where each object can be treated independently or as a set of nested objects through the same interface.
- **Use When**
  - **Hierarchical** representations of objects are needed.
  - **Objects and compositions of objects** should be treated uniformly.

<br>

### Characteristics
- composes objects into **tree** structures to represent **whole-part hierarchies**.
- lets clients **treat** individual objects and compositions of objects **uniformly**.

<br>

### Related patterns
- **Composite vs Decorator**
  - Both have similar structure diagrams
    - **recursive composition** to organize an open-ended number of objects
  - Different intentions
    - **Decorator** lets you **add responsibilities** to objects without subclassing
    - **Composite**'s focus is not on embellishment but on **representation**
    - They are complementary; hence, Composite and Decorator are often used in concert
- **Iterator**
  - Provide a way to access the elements of an **aggregate object (=typically uses composite pattern)** sequentially without exposing its underlying representation
