# Stack
* collection where elements are added and removed from one end (the top of the stack) 

## Operations
* push, pop, peek, isEmpty, size, toString

# Stack Calculator
* infix expression: a * b + c
* postfix expression: ab * c + 

# Java Interfaces
* **interface:** list of abstract methods and constants
  * must be ```public```, constants declared as ```final static```
* **abstract method:** method that does not have an implementation
```java
return type methodName(parameterList)
```

** Java Interface for Stack ADT
```java
public interface StackADT<T>
{
public void push (T element);
public T pop();
public T peek();
public boolean isEmpty();
public int size();
public String toString();
}
```
* **generic type <T>:** for generality, we define a class/interface based on generic type


