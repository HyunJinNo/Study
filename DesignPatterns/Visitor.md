# Visitor Pattern

### Introduction
- **Purpose**
  - **Allowing one or more operations to be applied to a set of objects at runtime**
  - **Decoupling the operations from the object structure (= the set of objects)**
    > It's important that the visitor pattern is used when the above two purposes are needed.
- **Use When**
  - An object structure must have many unrelated operations performed upon it
  - The object structure can't change but operations on it can
  - Operations must be performed on the concrete classes of an object structure
  - Operations should be able to operate on multiple object structures that implement the same interface sets
