# Topic 16: Sorting

## Insertion Sort
* orders sequence of values by repetitively inserting particular value into sorted subset of sequence

### Insertion Sort Using Stacks
* two temporary stacks *sorted* and *temp*
* contents of *sorted* are in order, smallest item on top of stack
* *temp* holds items needed to be shifted out to insert new item

### Algorithm
* ```remove``` first item from list
* while *sorted* is not empty && top of *sorted* is smaller than this item, ```pop``` top of *sorted* and ```push``` onto *temp*
* ```push``` current item onto *sorted*
* while *temp* is not empty, ```pop``` top item and ```push``` onto *sorted*
* to restore list, ```pop``` items one at a time from *sorted* and ```add``` to rear of list

### Analysis
* O(n^2) ** more detail in notes

## Selection Sort
* orders sequence of values by repetitively putting particular value into *final* position
* find smallest value in sequence, switch with value in first position, find next smallest value, switch with second position, repeat until all ordered

### Selection Sort Using Queue
* create queue *sorted*, originally empty, to hold items sorted so far
* *sorted* is always in order, new items are added to the end of the queue

### Algorithm
* while unordered list *list* is not empty: ```remove``` smallest item from *list* and enqueue to the end of *sorted*

```java
smallestSoFar = first item in list (removeFirst)
while (list is not empty)
{
  removeFirst item from list
  if (item is less than smallestSoFar)
  {
    enqueue smallestSoFar to end of temp
    smallestSoFar = item
  }
  else enqueue item to temp
}
```

* to restore list, ```dequeue``` items one at a time from *sorted* and ```add``` to the rear of *list*

### Analysis
* O(n^2)

## Quick Sort
* orders sequence of values by partitioning list around one element (the pivot or partition element), then sorting each partition
* choose one element to be the pivot
* organize remaining elements into two partitions: greater than pivot and less than pivot

### Algorithm
* ```remove``` itms to be sorted from list and ```put``` into empty container
* if container is not empty
  * randomly get a *pivot*
  * create containers *smaller* and *bigger*, originally empty
  * while container not empty
    * ```get``` *item* from container
    * if *pivot* < *item*, ```put``` *item* into *bigger* otherwise ```put``` *item* into *smaller*
  * sort *smaller*
  * ```add``` *pivot* at rear of list
  * sort *bigger*

### Analysis
* O(n log n)
