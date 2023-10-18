# Singleton Pattern

### Introduction
- **Purpose**
  - Ensures that **only one instance** of a class is allowed within a system.
- **Use When**
  - Exactly one instance of a class is required.
  - Controlled access to a single object is neccessary.

<br>

### How to Use (Example)
- **For single-thread**
  - Make the instructor be private
    - private Singleton() {}
  - Provide a getInstance() method
    - public static Singleton getInstance()
  - Remember the instance once you have created it
    - private static Singleton instance
    - if (instance == null) instance = new Singleton();
```java
public class Singleton {
    private static Singleton instance;

    // other useful instance variables;

    private Singleton() { //... }

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }

    // other useful methods
}
```

- **For multi-thread**
  - **Option 1**
    - Use **synchronized** keyword
      - public static synchronized Singleton getInstance()
    - cons: Too much locking
  ```java
  public class Singleton {
      private static Singleton instance;

      // other useful instance variables

      private Singleton() { //... }

      public static synchronized Singleton getInstance() {
          if (instance == null) {
              instance = new Singleton();
          }
          return instance;
      }

      // other useful methods
  }
  ```
  
  - **Option 2**
    - pros: no runtime overhead
    - cons: resource overhead when the instance is not used
  ```java
  public class Singleton {
      private static Singleton instance = new Singleton();

      // other useful instance variables

      private Singleton() { //... }

      public static Singleton getInstance() {
          return instance;
      }

      // other useful methods
  }
  ```
  
  - **Option 3**
    - Use volatile keyword and double-checked locking
    - pros: theoretically perfect solution
    - cons: dependent on the compiler (java version)
  ```java
  public class Singleton {
      private volatile static Singleton instance = null;

      // other useful instance variables

      private Singleton() { //... }

      public static Singleton getInstance() {
          if (instance == null) {
              synchronized(Singleton.class) {
                  if (instance == null) {
                      instance = new Singleton();
                  }
              }
          }
          return instance;
      }

      // other useful methods
  }
  ```
