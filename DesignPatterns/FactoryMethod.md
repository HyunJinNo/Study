# Factory Method Pattern

### Introduction
- **Purpose**
  - Exposes a **method for creating objects, allowing subclasses** to control the actual creation process.
- **Use When**
  - A class will not know what classes it will be required to create.
  - Subclasses may specify what objects should be created.
  - Parent classes wish to defer creation to their subclasses.
- **Characteristics**
  - Uses **inheritance** to decide the object to be instantiated.
  - Defines an interface for creating an object, but lets subclasses decide which class to instantiate.
  - Lets a class defer instantiation to subclasses.
