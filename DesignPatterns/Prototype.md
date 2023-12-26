# Prototype Pattern

### Introduction
- **Purpose**
  - Create objects based upon a template of **an existing objects through cloning.**
- **Use When**
  - Composition, creation, and representation of objects should be decoupled from a system
  - **Classes to be created are specified at runtime.**
  - **Objects or object structures are required that are identical or closely resemble other existing objects or object structures.**
  - **The initial creation of each object is an expensive operation.**
  - **When to avoid building a class hierarchy of factories that parallels the class hierarchy of products**

<br>

### Characteristics
- **Advantage**
  - **Hides concrete product classes from clients**
  - **Decouples the clients from the creational process**
- Prototypes can be **supplied and changed at runtime**
- It provides **great flexibility** in configuring and changing a program at runtime
  - Adding and removing products at run-time
  - Reduced subclassing
  - Configuring an application with classes **dynamically**
    - Loading the classes dynamically

<br>

### Participants
- **Prototype**
  - Defines the interface (an operation) of cloning itself.
- **ConcreteProduct**
  - Concrete objects that can clone themselves.
- **Client**
  - Obtain more objects by asking them to clone themselves.

<br>

### How to Use (Example)
