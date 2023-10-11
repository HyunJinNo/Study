# Strategy Pattern

### Introduction
- **Purpose**
  - Defines a set of encapsulated algorithms that can be swapped to carry out a specific behavior.
- **Use When**
  - The only difference between many related classes is their behavior.
  - Multiple versions or variations of an algorithm are required.
  - The behavior of a class should be defined at runtime.
  - Conditional statements are complex and hard to maintain.

<br>

### How to Use (Example)
```
public interface FlyBehavior {
    public void fly();
}

public class FlyWithWings implements FlyBehavior {
    public void fly() {
        System.out.println("I'm flying.");
    }
}

public class FlyNoWay implements FlyBehavior {
    public void fly() {
        System.out.println("I can't fly.");
    }
}
```

```
public abstract class Bird {
    FlyBehavior flyBehavior;

    public Bird() {}

    public void performFly() {
        flyBehavior.fly();
    }
}

public class MyBird extends Bird {
    public MyBird() {
        flyBehavior = new FlyNoWay();
    }

    public void setFlyBehavior(FlyBehavior flyBehavior) {
        this.flyBehavior = flyBehavior();
    }
}
```

```
public class Main {
    public static void main(String[] args) {
        Bird myBird = new MyBird();
        myBird.performFly();  // "I can't fly."

        myBird.setFlyBehavior(new FlyWithWings());
        myBird.performFly();  // "I'm flying."
    }
}
```
