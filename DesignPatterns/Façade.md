# Façade Pattern

<br>

## Introduction
- **Purpose**
  - Supplies a single interface to a set of interfaces within a system.
- **Use When**
  - A simple interface is needed to provide access to a complex system.
  - There are many dependencies between system implementations and clients.
  - Systems and subsystems should be layered.
- **Characteristics**
  - Provide **a unified interface** to a set of interfaces in a subsystem. It defines a higher-level interface that makes a subsystem easier to use.
  - **Does not prevent sophisticated clients from accessing the underlying classes.**
  - **It doesn't add any functionality. It just simplifies interfaces.**
- **Benefits**
  - Hides the implementations of the subsystem from clients.
    - makes the subsystem easier to use
  - Promotes weak coupling between the subsystem and its clients
    - allows changing the classes comprising the subsystem without affecting the clients

<br>

## How to Use (Example)
- **A set of interfaces**
  ```java
  public class Class1 {
      public void doSomething() {
          System.out.print("Hello, ");
      }
  }
  public class Class2 {
      public void doSomething() {
          System.out.print("World!");
      }
  }
  ```

- **Façade**
  ```java
  public class MyClass {
      public void doSomething() {
          Class1 c1 = new Class1();
          Class2 c2 = new Class2();
          c1.doSomething();
          c2.doSomething();
      }
  }
  ```
