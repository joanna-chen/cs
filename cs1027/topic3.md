# Topic 3: The Stack ADT

## Overview
* **stack:** collection whose elements are added and removed from one end (*top* of the stack)
* last in, first out
* useful for backtracking, browsers, word processors/editors, markup language, stack calculators, compilers, call stack

## Operations
* **push:** add to top of stack
* **pop:** remove the element at top of stack
* **peek:** examine element at top of stack
* **isEmpty:** determine if stack is empty
* **size:** determine number of elements in stack
* **toString:** return string representation of stack

## Java Interfaces
* *programming construct* called interface used to formally define operations on collection are in Java
* **Java interface:** list of *abstract methods* and constants
  * must be ```public``` and constants ```final static```
* **abstract method:** method that does not have an implementation
  * just consists of header of method

```Java
public interface StackADT<T>
{
// Adds one element to the top of this stack
public void push (T element);
// Removes and returns the top element from this stack
public
T pop( );
// Returns without removing the top element of this stack
public
T peek( );
// Returns true if this stack contains no elements
public boolean isEmpty( );
// Returns the number of elements in this stack
public int size( );
// Returns a string representation of this stack
public String toString( );
}
```

### Generic Types
* ```<T>``` represents a *generic type* to define a class in generality
* *actual type* known only when application program creates object of the class

### Interface implementation
* a class *implements the interface* by providing implementations (bodies) for abstract methods
* uses ```implements``` followed by the interface name

## ArrayStack Class
* in *Java Collections API*, class names indicate both underlying data structure and collection
```Java
public class ArrayStack<T> implements StackADT<T>

  private T[ ] stack; // the container for the data
  private int top; // indicates the next open slot
  private final int DEFAULT_CAPACITY=100;

  //-----------------------------------------------------------------
  // Creates an empty stack using the default capacity.
  //-----------------------------------------------------------------
  public ArrayStack( )
  {
  top = 0;
  stack = (T[ ]) (new Object[DEFAULT_CAPACITY]); // casting an array of Object objects into array of type T
  }

  //-----------------------------------------------------------------
  // Creates an empty stack using the specified capacity.
  //-----------------------------------------------------------------
  public ArrayStack (int initialCapacity)
  {
  top = 0;
  stack = (T[ ]) (new Object[initialCapacity]); // casting an array of Object objects into array of type T
  }

  //-----------------------------------------------------------------
  // Adds the specified element to the top of the stack,
  // expanding the capacity of the stack array if necessary
  //-----------------------------------------------------------------
  public void push (T element)
  {
  if (top == stack.length)
    expandCapacity( );
  stack[top] = element;
  top++;
  }

  //-----------------------------------------------------------------
  // Helper method to create a new array to store the
  // contents of the stack, with twice the capacity
  //-----------------------------------------------------------------
  private void expandCapacity( )
  {
  T[ ] larger = (T[ ]) (new Object[stack.length*2]);
  for (int index=0; index < stack.length; index++)
    larger[index] = stack[index];
  stack = larger;
  }

  //-----------------------------------------------------------------
  // Removes the element at the top of the stack and returns a
  // reference to it. Throws an EmptyCollectionException if the
  // stack is empty.
  //-----------------------------------------------------------------
  public T pop( ) throws EmptyCollectionException
  {
  if (isEmpty( ))
    throw new EmptyCollectionException(“Stack” );
  top--;
  T result = stack[top];
  stack[top] = null;
  return result;
  }

  //-----------------------------------------------------------------
  // Returns a string representation of this stack.
  //-----------------------------------------------------------------
  public String toString( )
  {
  String result = "";
  for (int index=0; index < top; index++)
    result = result + stack[index].toString( ) + "\n";
  return result;
  }

  //-----------------------------------------------------------------
  // Returns the number of elements in the stack
  //-----------------------------------------------------------------
  public int size( )
  {
    return top;
  }

  //-----------------------------------------------------------------
  // Returns true if the stack is empty and false otherwise
  //-----------------------------------------------------------------
  public boolean isEmpty( )
  {
    return (top == 0);
  }

  //-----------------------------------------------------------------
  // Returns a reference to the element at the top of the stack.
  // The element is not removed from the stack.
  // Throws an EmptyCollectionException if the stack is empty.
  //-----------------------------------------------------------------
  public T peek( ) throws EmptyCollectionException
  {
    if (isEmpty())
      throw new EmptyCollectionException("stack");
    int tempTop = top;
    tempTop--;
    T result = stack[tempTop];
    return result
  }
```

## Example: Postfix Expressions
* **infix notation:** operators are between operands, parentheses force preceedence
* **postfix expression:** operator comes fater its two operands
**********
algorithm to evaluate postfix Expressions
*****

## ```java.util.Stack``` Class
* the Java Collections API contains implementation of *Stack* class with similar operations
* *Stack* class derived from *Vector* class, which has dynamically *growable* array
