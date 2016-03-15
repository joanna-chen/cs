# Topic 12: The List ADT

* **list:** linear collection, adding and removing elements from list does not have to happen at one end or the other

## Ordered Lists
* **ordered list:** elements are ordered by some inherent characteristic of the elements
* *add*: adds an element to list (in the correct place)

## Unordered Lists
* **unordered:** order of elements in list not based on characteristic of elements but determined by the user of the list
* *addToFront*: adds element to front of list
* *addToRear*: add element to rear of list
* *addAfter*: add element after particular element already in list

## Indexed Lists
* **indexed list:** elements are referenced by their numeric position in the list (index)
* every time list changes, position (index) of element may change
* *add*: add element at particular index
* *set*: set element at index in list
* *get*: return reference to element at specific index
* *indexOf*: return index of specific element
* *remove*: removes and returns element at index

## List Operations
* *removing* elements in various ways
* *checking status* of list (```isEmpty```, ```size```)
* *iterating* through elements in list
* removeFirst, removeLast, remove, first, last, contains (boolean), isEmpty, size, iterator, toString

## ListADT Interface
```java
import java.util.Iterator;
public interface ListADT<T> {
  // Removes and returns the first element from this list
  public T removeFirst ( );
  // Removes and returns the last element from this list
  public T removeLast ( );
  // Removes and returns the specified element from this list
  public T remove (T element);
  // Returns a reference to the first element on this list
  public T first ( );
  // Returns a reference to the last element on this list
  public T last ( );
  // Returns true if this list contains the specified target element
  public boolean contains (T target);
  // Returns true if this list contains no elements
  public boolean isEmpty( );
  // Returns the number of elements in this list
  public int size( );
  // Returns an iterator for the elements in this list
  public Iterator<T> iterator( );
  // Returns a string representation of this list
  public String toString( );
}
```

## OrderedListADT
```java
public interface OrderedListADT<T> extends ListADT<T>
  {
  // Adds the specified element to this list at the proper location
  public void add (T element);
  }
```

## UnorderedListADT
```java
public interface UnorderedListADT<T> extends ListADT<T>
{
  // Adds the specified element to the front of this list
  public void addToFront (T element);
  // Adds the specified element to the rear of this list
  public void addToRear (T element);
  // Adds the specified element after the specified target
  public void addAfter (T element, T target);
}
```

## IndexedListADT
```java
public interface IndexedListADT<T> extends ListADT<T>
{
  // Inserts the specified element at the specified index
  public void add (int index, T element);
  // Sets the element at the specified index
  public void set (int index, T element);
  // Adds the specified element to the rear of this list
  public void add (T element);
  // Returns a reference to the element at the specified index
  public T get (int index);
  // Returns the index of the specified element
  public int indexOf (T element);
  // Removes and returns the element at the specified index
  public T remove (int index);
}
```

## List Implementation using Arrays
* container: array
* fix one end of list at index 0, shift as needed when element added/removed

```java
//-----------------------------------------------------------------
// Removes and returns the specified element.
//-----------------------------------------------------------------
public T remove (T element) throws ElementNotFoundException
{
  T result;
  int index = find (element); // uses helper method find
  if (index == NOT_FOUND)
    throw new ElementNotFoundException("list");
  result = list[index];
  rear--;
  // shift the appropriate elements
  for (int scan=index; scan < rear; scan++)
    list[scan] = list[scan+1];
  list[rear] = null;
  return result;
}

//-----------------------------------------------------------------
// Returns the array index of the specified element,
// or the constant NOT_FOUND if it is not found.
//-----------------------------------------------------------------
private int find (T target)
{
  int scan = 0, result = NOT_FOUND;
  boolean found = false;
  if (! isEmpty( ))
    while (! found && scan < rear)
      if (target.equals(list[scan])
        found = true;
      else
        scan++;
  if (found)
    result = scan;
  return result;
}

//-----------------------------------------------------------------
// Returns true if this list contains the specified element.
//-----------------------------------------------------------------
public boolean contains (T target)
{
  return (find(target) != NOT_FOUND);
  //uses helper method find
}

//-----------------------------------------------------------------
// Adds the specified Comparable element to the list,
// keeping the elements in sorted order.
//-----------------------------------------------------------------
public void add (T element)
{
  if (size( ) == list.length)
    expandCapacity( );
    Comparable<T> temp = (Comparable<T>)element;
  int scan = 0;
  while (scan < rear && temp.compareTo(list[scan]) > 0)
    scan++;
  for (int scan2=rear; scan2 > scan; scan2--)
    list[scan2] = list[scan2-1]
  list[scan] = element;
  rear++;
}
```
 
