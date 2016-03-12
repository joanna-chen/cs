# Topic 7: Stack: a Linked Implementation
* linked list implementation of Stack collection: elements of stack are stored as nodes of the linked list

## LinkedStack Class
* nodes in the linked list are represented by the ```LinearNode``` class
```java
//-----------------------------------------------------------------
// Creates an empty stack.
//-----------------------------------------------------------------
public LinkedStack ()
  {
    top = null;
    count = 0;
  }
//-----------------------------------------------------------------
// Adds the specified element to the top of the stack.
//-----------------------------------------------------------------
  public void push (T element)
  {
    LinearNode<T> temp = new LinearNode<T> (element);
    temp.setNext(top);
    top = temp;
    count++;
  }
//-----------------------------------------------------------------
// Removes the element at the top of the stack and returns
// a reference to it. Throws an EmptyCollectionException if
// the stack is empty.
//-----------------------------------------------------------------
  public T pop( ) throws EmptyCollectionException
  {
    if (isEmpty( ))
      throw new EmptyCollectionException(“Stack” );
    T result = top.getElement( );
    top = top.getNext( );
    count--;
  return result;
  }
```
