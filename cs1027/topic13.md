# Topic 13: Iterators
* **iterator:** mechanism used to step through elements of collection one by one

## Iterator Interface ```Iterator<T>```
* ```public boolean hasNext();```: returns true if there are more elements in iteration
* ```public T next();``` returns the next element in the iteration
* ```public void remove();``` removes the last element returned by the iterator

## ArrayIterator
```java
// Represents an iterator over the elements of an array
import java.util.*;
public class ArrayIterator<T> implements Iterator<T>
{
  // Attributes
  private int count; // number of elements in collection
  private int current; // current position in the iteration
  private T[ ] items; // items in the collection
  // Constructor: sets up this iterator using the
  // specified items
  public ArrayIterator (T[ ] collection, int size) {
    items = collection;
    count = size;
    current = 0;
  }
  // Returns true if this iterator has at least one
  // more element to deliver in the iteration
  public boolean hasNext( ) {
    return (current < count);
  }
  // Returns the next element in the iteration.
  // If there are no more elements in this iteration,
  // throws an exception.
  public T next( ) {
    if (! hasNext( ))
      throw new NoSuchElementException( );
    current++;
    return items[current - 1];
  }
}
```

## LinkedIterator
```java
import java.util.*;
public class LinkedIterator<T> implements Iterator<T> {
  // Attributes
  private int count; // number of elements in collection
  private LinearNode<T> current; // current position
  // Constructor: Sets up this iterator using the specified items
  public LinkedIterator (LinearNode<T> collection, int size){
    current = collection;
    count = size;
  }
  // Returns true if this iterator has at least one more element
  // to deliver in the iteration.
  public boolean hasNext( ) {
    return (current!= null);
  }
  // Returns the next element in the iteration. If there are no
  // more elements in this iteration, throws an exception.
  public T next( ) {
    if (! hasNext( ))
      throw new NoSuchElementException( );
    T result = current.getElement( );
    current = current.getNext( );
    return result;
  }
}
```

## Iterators for a collection
* the ListADT interface has an operation called ```iterator```
* ```public Iterator<T> iterator();```

## *iterator* method for ArrayList
```java
/**
* Returns an iterator for the elements currently in this list.
*
* @return an iterator for the elements in this list
*/
  public Iterator<T> iterator()
  {
    return new ArrayIterator<T> (list, rear);
  }
```

## *iterator* method for LinkedList
```java
/**
* Returns an iterator for the elements currently in this list.
*
* @return an iterator for the elements in this list
*/
public Iterator<T> iterator( )
{
  return new LinkedIterator<T> (contents, count);
}
```

## Using an Iterator
* when ```iterator()``` method in collection is invoked, an "iterator object" is returned
* we then use ```hasNext()``` and ```next()``` on that object to iterate through the collection

```java
ArrayUnorderedList<Person> myList = new ArrayUnorderedList<Person>();
// Use iterator to display contents of list
Iterator<Person> iter = myList.iterator();
while(iter.hasNext())
{
  System.out.println(iter.next());
}
// Print just the email addresses now
// Note that we have to start a new iteration!
iter = myList.iterator(); // start new iteration
while(iter.hasNext())
{
  System.out.println(iter.next().getEmail());
}
```

### Using Iterator within Class Definition
```java
public String toString() {
  String result = “”;
  Iterator<T> iter = this.iterator();
  while ( iter.hasNext())
    result = result + iter.next().toString() + “\n”;
  return result;
}
