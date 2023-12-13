# Chain of Responsibility Pattern

### Introduction 
- **Purpose**
  - Gives more than one object an opportunity to handle a request by linking receiving objects together.
- **Use When**
  - **Multiple objects may handle a request** and the handler doesn't have to be a specific object.
  - **A set of objects should be able to handle a request with the handler determined at runtime.**
  - A request not being handled is an acceptable potential outcome.

<br> 

### Characteristics
- Each object in the chain receives the request and handles it or forwards it to the next object.
- Object making the request has no knowledge of which object is handling the request.
- The request has an implicit receiver.
- **Each object in the chain shares a common interface for handling requests and accessing its successor on the chain.**

<br>

### Participants
- **Handler**
  - defines an interface for handling the requests
  - (optinonal) implements the successor link
- **Concrete Handler**
  - handles requests it it responsible for
  - can access its successor
  - if the Concrete Handler can handle the request, it does so; otherwise it forwards the request to its successor
- **Client**
  - initiates the request to a Concrete Handler object on the chain
 
<br>

### Pros and Cons
- **Benefits**
  - Decoupling of senders and receivers
  - Added flexibility
  - Sender doesn't need to know specifically who the handlers are
- **Potential Drawbacks**
  - Client can't explicitly specify who handles a request
  - No guarantee of request being handled (request falls off end of chain)

<br>

### How to Use (Example)
- **Handler**
  ```java
  public abstract class Handler {
      proteced Handler successor;
  
      public void setSuccessor(Handler successor) {
          this.successor = successor;
      }

      public abstract void handleRequest(int request);  // your request to be handled
  }
  ```
- **Concrete Handler**
  ```java
  public class ConcreteHandler1 extends Handler {
      @Override
      public void handleRequest(int request) {
          if (request >= 0 && request < 10) {
              System.out.println("ConcreteHandler1 handled request " + request);
          } else if (successor != null) {
              successor.handleRequest(request);
          }
      }
  }
  ```
  ```java
  public class ConcreteHandler2 extends Handler {
      @Override
      public void handleRequest(int request) {
          if (request >= 10 && request < 20) {
              System.out.println("ConcreteHandler2 handled request " + request);
          } else if (successor != null) {
              successor.handleRequest(request);
          }
      }
  }
  ```
- **Client**
  ```java
  public class Main {
      public static void main(String[] args) {
          Handler h1 = new ConcreteHandler1();
          Handler h2 = new ConcreteHandler2();
          h1.setSuccessor(h1);

          int[] requests = new int[] { 5, 7, 13, 19, 20 };

          for (int request : requests) {
              h1.handleRequest(request);
          }
      }
  }
  ```
