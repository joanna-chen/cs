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
```
