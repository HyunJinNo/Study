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

<br>

### Characteristics
- Pros
  - **Makes adding new operations easy**
    - You can define a new operation simply by adding a new visitor
    - In contrast, if you spread functionality over many classes, then you must change each class to define a new operation
  - **Gathers related opertations and separates unrelated operations**
    - Related behavior is not spread over the classes defining the object structure; it’s localized in a visitor
    - Unrelated sets of behavior are partitioned in their own visitor classes
- Cons
  - **Adding new ConcreteElement classes is hard**
    - The Visitor pattern makes it hard to add new subclasses of Element
    - Each new ConcreteElement gives rise to a new abstract operation on Visitor and a corresponding implementation in every ConcreteVisitor class
  - **Breaking encapsulation**
    - Visitor’s approach assumes that the ConcreteElement interface is powerful enough to let visitors do their job
    - The pattern often forces you to provide public operations that access an element’s internal state, which may compromise its encapsulation  
- Visitors can visit objects that don't have a common parent class.

<br> 

### Participants
- **Visitor**
  - declares a visit operation for each class of ConcreteElement in the object structure
- **ConcreteVisitor**
  - implements each operation declared by Visitor
- **Element**
  - **defines an Accept operation** that takes a visitor as an argument
- **ConcreteElement**
  - implements an Accept operation that takes a visitor as an argument
- **ObjectStructure**
  - can enumerate its elements 
  - may provide a high-level interface to allow the visitor to visit its elements
  - may be a composite or a collection like a set or list

<br>

### How to Use (Example)
