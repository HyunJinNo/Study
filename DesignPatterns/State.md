# State Pattern

### Introduction
- **Purpose**
  - Ties object circumstances to its behavior, allowing the object to **behave in different ways** based upon its **internal state**.
- **Use When**
  - **The behavior of an object should be influenced by its state**.
  - **Complex conditions** tie object behavior to its state.
  - Transitions between states need to be explicit.

<br>

### Characteristics
- **Encapsulate what varies**
  - Put each state’s behavior in its own class, then every state just implements its own actions
  - The client object can delegate to the state object that represents the current state
- **Favor composition over inheritance**
- **Get rid of** all of our **conditional code** and instead delegate to the state object to do the work for us.

<br>

### How to Use (Example)
- **State**
  ```Java
  public class State {
      public State() {
      }
  }
  ```
- **Concrete State**
- **Client**
  ```Java
  public class Person {
      public Person() {
          
      }
  }
  ```
