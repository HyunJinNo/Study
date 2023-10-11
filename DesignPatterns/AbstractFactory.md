# Abstract Factory Pattern

### Introduction
- **Purpose**
  - Provide an **interface that delegates creation calls** to one or more concrete classes in order to deliver **specific objects.**
- **Use When**
  - The creation of objects should be independent of the system utilizing them.
  - Systems should be capable of using multiple families of objects.
  - Families of objects must be used together.
  - Libraries must be published without exposing implementation details.
  - Concrete classes should be decoupled from clients.
- **Characteristics**
  - Delegates object creation to a factory object.
  - Uses **composition and delegation**.
