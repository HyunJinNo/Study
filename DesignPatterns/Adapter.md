# Adapter Pattern

### Introduction
- **a.k.a**
  - Wrapper
- **Purpose**
  - Permits classes with **different interfaces** to work together by creating a common object by which they may communicate and interact.
- **Use When**
  - A class to be used doesn't meet interface requirements.
- **Mechanism**
  - A **client** makes a request to the adapter by **calling a method** on it using the **target interface**.
  - The **adapter translates the request** into one or more calls on the **adaptee** using the **adaptee interface**.
  - The **client receives the results** of the call and never knows there is an adapter doing the translation.
- **Motivation**
  - A toolkit or class library may have an interface which is incompatible with an application's interface we want to integrate.
  - It's possible that we don't have access to the source code of the toolkit or library.
  - Even if the source code is available, we may want to minimize the change.
- **Summary**
  - Converts the interface of a class into another interface clients expect.
  - Lets classes work together that couldn't otherwise because of incompatible interfaces.
  - Class adapter and object adapter

<br>

### How to Use (Example)
- **Adaptee Interface**
```java
public interface Duck {
    public void quack();
    public void fly();
}

public class MallardDuck implements Duck {
    public void quack() {
        System.out.println("Quack.");
    }
    public void fly() {
        System.out.println("I'm flying.");
    }
}
```

- **Target Interface**
```java
public interface Turkey {
    public void gobble();
    public void fly();
}

public class WildTurkey implements Turkey {
    public void gobble() {
        System.out.println("Gobble.");
    }
    public void fly() {
        System.out.println("I'm flying.");
    }
}
```

- **Object Adapter**
```java
public class TurkeyAdapter implements Duck {
    Turkey turkey;
    public TurkeyAdapter(Turkey turkey) {
        this.turkey = turkey;
    }
    public void quack() {
        turkey.gobble();
    }
    public void fly() {
        for (int i = 0; i < 5; i++) {
            turkey.fly();
        }
    }
}
```
