# Observer patterns

### Introduction
- **a.k.a**
  - Publish/Subscibe model
- **Purpose**
  - Lets one or more objects be notified of state changes in other objects within the system
- **Use When**
  - Loose coupling is needed for commnucations
  - State changes in one or more objects should trigger behavior in other objects
  - Broadcasting capabilities are required.
  - An understanding exists that objects wiil be blind to the expense of notification
- **Definition**
  - It defines a **one-to-many dependency** between objects so that when one object changes state, all of its dependents are notified and updated automatically.
