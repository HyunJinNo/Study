# Template Method Pattern

### Introduction
- **Purpose**
  - Identifies the **framework of an algorithm**, allowing implementing classes to define the actual behavior.
- **Use When**
  - A single abstract implementation of an algorithm is needed.
  - Common behavior among subclasses should be localized to a common class.
  - Parent classes should be able to **uniformly invoke behavior in their subclasses**.
  - Most or all subclasses need to implement the behavior.
