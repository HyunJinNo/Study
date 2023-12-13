# Chain of Responsibility Pattern

### Introduction 
- Purpose
  - Gives more than one object an opportunity to handle a request by linking receiving objects together.
- Use When
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
- Handler
  - defines an interface for handling the requests
  - (optinonal) implements the successor link
- Concrete Handler
  - handles requests it it responsible for
  - can access its successor
  - if the Concrete Handler can handle the request, it does so; otherwise it forwards the request to its successor
- Client
  - initiates the request to a Concrete Handler object on the chain
 
<br>

### Pros and Cons
- Benefits
  - Decoupling of senders and receivers
  - Added flexibility
  - Sender doesn't need to know specifically who the handlers are
- Potential Drawbacks
  - Client can't explicitly specify who handles a request
  - No guarantee of request being handled (request falls off end of chain)
