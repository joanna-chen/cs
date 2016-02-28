# Topic 9: Queues

* **queue:** collection whose elements are added to one end (tail) and removed from other end (head)
  * first in, first out

## Queue Operations
* **enqueue:** add element to tail of queue
* **dequeue:** remove element from the head of queue
* **first:** examine element at head of queue ("peek")
* **isEmpty:** determines whether queue is empty
* **size:** determines number of elements in queue
* **toString:** returns string representation of queue

```java
public interface QueueADT<T>
{
// Adds one element to the rear of the queue
public void enqueue (T element);
// Removes and returns the element at the front of the queue
public T dequeue( );
// Returns without removing the element at the front of the queue
public T first( );
// Returns true if the queue contains no elements
public boolean isEmpty( );
// Returns the number of elements in the queue
public int size( );
// Returns a string representation of the queue
public String toString( );
}
```

## Using Queues

### Coded Message
* Caesar cipher (substitution code) shift each letter in message by constant amount
* **repeating key:** sequence of integers that determine how much each character is shifted, when list is exhausted, start over
  * dequeue key value when needed, enqueue when exhausted

## Implementing
* need data structure, *front* indication, *end* indication
* represented as a linked list of nodes
* need two pointers (one for *front*, one for *end*), count for number of items

## LinkedQueue class
```Java
public class LinkedQueue<T> implements QueueADT<T>
{
/**
* Attributes
*/
private int count;
private LinearNode<T> front, rear;
/**
* Creates an empty queue.
*/
public LinkedQueue()
{
count = 0;
front = rear = null;
}
//-----------------------------------------------------------------
// Adds the specified element to the rear of the queue.
//-----------------------------------------------------------------
public void enqueue (T element)
{
LinearNode<T> node = new LinearNode<T> (element);
if (isEmpty( ))
front = node;
else
rear.setNext (node);
rear = node;
count++;
}
//-----------------------------------------------------------------
// Removes the element at the front of the queue and returns a
// reference to it. Throws an EmptyCollectionException if the
// queue is empty.
//-----------------------------------------------------------------
public T dequeue ( ) throws EmptyCollectionException
{
if (isEmpty( ))
throw new EmptyCollectionException ("queue");
T result = front.getElement( );
front = front.getNext( );
count--;
if (isEmpty( ))
rear = null;
return result;
}
}
```

## ArrayQueue class
```java
public class ArrayQueue<T> implements QueueADT<T>
{
private final int DEFAULT_CAPACITY = 100;
private int rear;
private T[] queue;
public ArrayQueue()
{
rear = 0;
queue = (T[])(new Object[DEFAULT_CAPACITY]);
}
public ArrayQueue (int initialCapacity)
{
rear = 0;
queue = (T[])(new Object[initialCapacity]);
}
//-----------------------------------------------------------------
// Removes the element at the front of the queue and returns
// a reference to it. Throws anEmptyCollectionException if the
// queue is empty.
//-----------------------------------------------------------------
public T dequeue ( ) throws EmptyCollectionExceptio
n
{
if (isEmpty( ))
throw new EmptyCollectionException ("queue");
T result = queue[0];
rear--;
// shift the elements
for (int i = 0; i < rear; i++)
queue[i] = queue[i+1];
queue[rear] = null;
return result;
}
}
```

## Analysis of Queue Operations
* **enqueue operation:** O(1) for linked implementation, O(n) for circular array if need to expand capacity otherwise O(1)
* **dequeue operation:** O(1) for linked implementation, O(1) for circular array, O(n) for noncircular array
