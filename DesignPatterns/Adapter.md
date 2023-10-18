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
