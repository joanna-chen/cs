# Topic 6: Linked Data Structures

* **linked:** consists of items that are linked together
* **singly linked list:** each item points to next item
* **doubly linked list:** each item points to next item and previous item

## Advantages
* items do not have to be stored consecutively in memory locations
* linked lists can grow dynamically

## Nodes
* linked list is an ordered sequence of items called nodes
* **node:** basic unit of representation in linked list
  * consists of *data* portion and *link (pointer)* to next node in Structures
  * **front/head:** the first node in the linked list

## Linked List Operations
* *add* item to linked list
* *delete* item from linked list

## References as Links
* **pointer:** reference to an object
* linked structure uses *references* to link one object to another

## Implementation of Linked List
* linked list is a list of *node objects* (data object, next node object)
* *head pointer* is the reference to the linked list
* the last node has ```null``` value as its next node object

## LinearNode Class
```java
public class LinearNode<T>
  {
    private LinearNode<T> next;
      private T element;
      public LinearNode( ){
      next = null;
      element = null;
  }
    public LinearNode (T elem){
      next = null;
      element = elem;
  }
    public LinearNode<T> getNext( ){
      return next;
  }
    public void setNext (LinearNode<T> node){
      next = node;
  }
    public T getElement( ){
      return element;
  }
    public void setElement (T elem) {
      element = elem;
    }
  }
```
```java
// create node that contains the integer 7
LinearNode<Integer> inode = new LinearNode<Integer> (new Integer(7));
```
