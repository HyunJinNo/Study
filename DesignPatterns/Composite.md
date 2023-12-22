# Composite Pattern

### Introduction
- **Purpose**
  - Facilitates the creation of **object hierarchies** where each object can be treated independently or as a set of nested objects through the same interface.
- **Use When**
  - **Hierarchical** representations of objects are needed.
  - **Objects and compositions of objects** should be treated uniformly.

<br>

### Characteristics
- composes objects into **tree** structures to represent **whole-part hierarchies**.
- lets clients **treat** individual objects and compositions of objects **uniformly**.
- Child Mgt. Interface
  - Placing in Component class gives **Transparency**.
    - since all components can be treated the same. However, it is not safe. Clients can try to do meaningless things to leaf components at **run-time**.
  - Placing in Composite class gives **Safety**.
    -  since any attempt to perform a child operation on a leaf component will be caught at **compile-time**. However, we lose transparency because now leaf and composite components have different interfaces.

<br>

### Related patterns
- **Composite vs Decorator**
  - Both have similar structure diagrams
    - **recursive composition** to organize an open-ended number of objects
  - Different intentions
    - **Decorator** lets you **add responsibilities** to objects without subclassing
    - **Composite**'s focus is not on embellishment but on **representation**
    - They are complementary; hence, Composite and Decorator are often used in concert
- **Iterator**
  - Provide a way to access the elements of an **aggregate object (=typically uses composite pattern)** sequentially without exposing its underlying representation

<br>

### How to Use (Example)
- **Component**
  ```Java
  public class Component {
      public void add(Component component) {
          throw new UnsupportedOperationException();
      }
  }
  ```
- **Leaf**
  ```Java
  public class Leaf extends Component {
      public String name;
      public Leaf(String name) {
          this.name = name;
      }
      public String getName() {
          return name;
      }
      public Iterator createIterator() {
          return new NullIterator();
      }
  }
  ```
  ```Java
  public class NullIterator implements Iterator {
      public Object next() {
          return null;
      }
      public boolean hasNext() {
          return false;
      }
      public void remove() {
          throw new UnsupportedOperationException();
      }
  }
  ```
- **Composite**
  ```Java
  import java.util.ArrayList;
  
  public class Composite extends Component {
      public String name;
      public ArrayList<Component> components;
      public Iterator iterator = null;
  
      public Composite(String name) {
          this.name = name;
          components = new ArrayList<Component>();
      }

      @Override
      public void add(Component component) {
          components.add(component);
      }

      public Iterator createIterator() {
          if (iterator == null) {
              iterator = new CompositeIterator(components.iterator());
          }
          return iterator;
      }
  }
  ```
  ```Java
  import java.util.Stack;
  
  public class CompositeIterator implements Iterator {
      public Stack<Component> stack = new Stack<Component>();
      public CompositeIterator(Iterator iterator) {
          stack.push(iterator);
      }
      public Object next() {
          if (hasNext()) {
              Iterator iterator = (Iterator) stack.peek();
              Component component = (Component) iterator.next();
              if (component instanceof Composite) {
                  stack.push(component.createIterator());
              }
              return component;
          } else {
              return null;
          }
      }
      public boolean hasNext() {
          if (stack.empty()) {
              return false;
          }
          Iterator iterator = (Iterator) stack.peek();
          if (!iterator.hasNext()) {
              stack.pop();
              return hasNext();
          } else {
              return true;
          }
      }
      public void remove() {
          throw new UnsupportedOperationException();
      }
  }
  ```
