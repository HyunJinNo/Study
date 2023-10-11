# Command Pattern

### Introduction
- **Purpose**
  - **Encapsulates a request as an object**
  - This allows the request to be handled in traditionally **object based relationships** such as queuing and callbacks.
- **Use When**
  - Requests need to be specified, queued, and executed at variant times or in variant orders.
  - A history of requests is needed.
  - The invoker should be decoupled from the object handling the invocation.
