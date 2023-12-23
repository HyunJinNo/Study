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
