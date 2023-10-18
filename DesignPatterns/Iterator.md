# Iterator Pattern

### Introduction
- **a.k.a**
  - Cursor
- **Purpose**
  - Allows for access to the elements of an ***aggregate object*** without allowing access to its underlying representation.
  - Provides a way to access the elements of an ***aggregate object*** sequentially without exposing its underlying representation.

    > An aggregate object is an object that contains other objects for the purpose of grouping those objects as a unit. It's also called a container or a collection. Examples are linked list and hash table.
- **Use When**
  - Access to elements is needed without access to the entire representation.
  - Multiple or concurrent traversals of the elements are needed.
  - A uniform interface for traversal is needed.
  - Subtle differences exist between the implementation details of various iterators.
