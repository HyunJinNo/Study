# Observer patterns

### Introduction
- **a.k.a**
  - Publish/Subscibe model
- **Purpose**
  - Lets one or more objects be notified of state changes in other objects within the system
- **Use When**
  - Loose coupling is needed for commnucations
  - State changes in one or more objects should trigger behavior in other objects
  - Broadcasting capabilities are required.
  - An understanding exists that objects wiil be blind to the expense of notification
- **Definition**
  - It defines a **one-to-many dependency** between objects so that when one object changes state, all of its dependents are notified and updated automatically.

<br>

### How to Use
- **Observable (Publisher) side**
  - To send notifications
    - Call SetChanged()
    - Call either notifyObservers() or notifyObservers(Object arg)
```java
import java.util.Observable;
import java.util.Observer;

public class MyData extends Observable {
    private int number;

    public MyData() {}

    public void measurementsChanged() {
        setChanged();
        notifyObservers();
    }

    public void setMeasurements(int number) {
        this.number = number;
        measurementsChanged();
    }

    public int getNumber() {
        return number;
    }
}
```

- **Observer (Subsciber) side**
  - To become an observer
    - Implement java.util.Observer interface
  - To subscribe
    - Call addObserver() on any Observable object
  - To unsubscribe
    - Call deleteObserver()
  - To get updated
    - Implement update(Observable o, Object arg)
```java
import java.util.Observable;
import java.util.Observer;

public class MyObserver implements Observer {
    Observable observable;
    private int number;

    public MyObserver(Observable observable) {
        this.observable = observable;
        observable.addObserver(this);
    }

    public void update(Observable obs, Object arg) {
        if (obs instanceof MyData) {
            MyData myData = (MyData) obs;
            this.number = myData.getNumber();

            // Something to execute
        }
    }
}
```
