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
- Localized the **behavior of each state** into its own class
- **Removed** all the troublesome **conditional statements** that would have been difficult to maintain
- **Closed each state for modification**, and yet left the client open to extension by adding new state classe
- The State Pattern **allows an object to alter its behavior when its internal state changes**. The object will appear to change its class.
- An object's behavior depends on its state, and it **must change its behavior at run-time depending on that state**.
- Pros and Cons
  - Pros
    - Puts all behavior associated with a state into one object
    - Allows state transition logic to be incorporated into a state object rather than in a monolithic if or switch statement
    - Helps avoid inconsistent states since state changes occur using just the one state object and not several objects or attributes
  - Cons
    - Increased number of objects

<br>

### How to Use (Example)
- **State**
  ```Java
  public interface State {
      public void work();
  }
  ```
- **Concrete State**
  ```Java
  public class WorkingState implements State {
      public Person person;

      public WorkingState(Person person) {
          this.person = person;
      }

      @Override
      public void work() {
          System.out.println("I'm working!");
          person.setState(person.getRestingState());
      }
  }
  ```
  ```Java
  public class RestingState implements State {
      public Person person;

      public RestingState(Person person) {
          this.person = person;
      }

      @Override
      public void work() {
          System.out.println("I'm resting!");
          person.setState(person.getWorkingState());
      }
  }
  ```
- **Client**
  ```Java
  public class Person {
      private State workingState;
      private State restingState;
      private State state = workingState;
  
      public Person() {
          workingState = new WorkingState(this);
          restingState = new RestingState(this);
      }

      public void setState(State state) {
          this.state = state;
      }

      public State getWorkingState() {
          return workingState;
      }

      public State getRestingState() {
          return restingState;
      }

      public void work() {
          state.work();
      }
  }
  ```
