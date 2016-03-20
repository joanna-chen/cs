# More on List ADT

## The ```Comparable``` Interface
* for ordered list, the actual class for the generic style T must have a way of comparing elements, so that it can be ordered
* to implement the ```Comparable``` interface -> define method called ```compareTo```
* declare var of type ```Comparable<T>``` and convert var of type ```T``` to var of type ```Comparable<T>```
* ```Comparable<T> temp = (Comparable<T>) element;```

## List Implementation Using Arrays (Circular Arrays)

## List Implementation Using Links
```java
//-----------------------------------------------------------------
// Removes the first instance of the specified element
// from the list, if it is found in the list, and returns a
// reference to it. Throws an ElementNotFoundException
// if the specified element is not found on the list.
//-----------------------------------------------------------------
public T remove (T targetElement) throws ElementNotFoundException
{
if (isEmpty( ))
  throw new ElementNotFoundException ("List");
  boolean found = false;
  LinearNode<T> previous = null
  LinearNode<T> current = head;
  while (current != null && !found)
    if (targetElement.equals (current.getElement( )))
      found = true;
    else {
      previous = current;
      current = current.getNext( );
    }   
    if (!found)
throw new ElementNotFoundException ("List");
if (size( ) == 1)
head = tail = null;
else
if (current.equals (head))
head = current.getNext( );
else
if (current.equals (tail))
{
tail = previous;
tail.setNext(null);
}
else
previous.setNext(current.getNext( ));
count--;
return current.getElement( );
}
```

## Doubly Linked Lists
* **doubly linked list:** two references in each node, one to ```next``` and one to the ```previous```

```java
//-----------------------------------------------------------------
// Removes and returns the specified element.
//-----------------------------------------------------------------
public T remove (T element) throws ElementNotFoundException
{
  T result;
  DoubleNode<T> nodeptr = find (element);
    // uses helper method find for doubly-linked list
  if (nodeptr == null)
    throw new ElementNotFoundException ("list");
  result = nodeptr.getElement( );
  // check to see if front or rear
  if (nodeptr == front)
    result = this.removeFirst( );
  else
    if (nodeptr == rear)
      result = this.removeLast( );
    else
    {
      nodeptr.getNext( ).setPrevious(nodeptr.getPrevious( ));
      nodeptr.getPrevious( ).setNext(nodeptr.getNext( ));
      count--;
    }
  return result;
}
```

## Analysis of List Implementations
* most operations in both array and linked implementations are O(1) unless there is shifting or searching needed in which ase it is O(n)
