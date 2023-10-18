# Mediator Pattern

### Introduction
- **Purpose**
  - Allow loose coupling by **encapsulaing the way** disparate sets of objects **interact and communicate** with each other.
- **Use When**
  - Communication between sets of objects is well defined and complex.
  - Too many relationships exist and common point of control or communication is needed.
- **Characteristics**
  - Encapsulates interconnects between objects into Mediator
    - communications hub
    - Responsible for coordinating and controlling colleague interaction
  - Promotes **loose coupling** between classes
    - By preventing from referring to each other explicitly
    - Mediator is commonly used to coordinate related GUI components
  - Pros: easy to understand the flow of communication
  - Cons: Mediators are hardly ever reusable.
