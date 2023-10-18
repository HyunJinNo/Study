# Iterator Pattern

### Introduction
- **a.k.a**
  - Cursor
- **Purpose**
  - Allows for access to the elements of an ***aggregate object*** without allowing access to its underlying representation.
  - Provides a way to access the elements of an ***aggregate object*** sequentially without exposing its underlying representation.

    > An aggregate object is an object that contains other objects for the purpose of grouping those objects as a unit. It's also called a container or a collection. Examples are linked list and hash table.
- **Use When**
  - Access to elements is needed without access to the entire representation.
  - Multiple or concurrent traversals of the elements are needed.
  - A uniform interface for traversal is needed.
  - Subtle differences exist between the implementation details of various iterators.

<br>

### How to Use (Example)
```java
public class MenuItem {
    String name;
    String description;
    boolean vegetarian;
    double price;

    public MenuItem(String name, String description, boolean vegetarian, double price) {
        this.name = name;
        this.description = description;
        this.vegetarian = vegatarian;
        this.price = price;
    }
}
```

```java
public interface Menu {
    public Iterator createIterator();
}
```

```java
public class DinerMenu implements Menu {
    MenuItem[] menuItems;

    @Override
    public Iterator createIterator() {
        return new DinerMenuIterator(menuItems);
    }
}
```

```java
import java.util.Iterator;

public class DinerMenuIterator implements Iterator {
    MenuItem[] items;
    int position;

    public DinerMenuIterator(MenuItem[] items) {
        this.items = items;
        position = 0;
    }

    @Override
    public Object next() {
        MenuItem menuItem = items[position];
        position++;
        return menuItem;
    }

    @Override
    public boolea hasNext() {
        if (position >= items.length)
            return false;
        else
            return true;
    }

    @Override
    public void remove() {
        // code for removing an item and shifting the rest
    }
}
```
