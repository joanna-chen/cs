# Topic 15: Binary Search Tree ADT
* **binary search tree (BST):** binary tree with an ordering property of its elements, such that data in any internal node is *greater than* data in left subtree and *less than* data in right subtree
  * does not allow for duplicates

## BST Operations
* *add* element (maintaining the BST property)
* *remove* element (maintaining the BST property)
* *remove max* element
* *remove min* element

## Search Operation
```
To search for a value k; returns true if found or false if not found
If the tree is empty, return false.
If k == value at root
  return true: we’re done.
If k < value at root
  return result from search for k in the left subtree
Else
  return result from search for k in the right subtree.
```

## Add Operation
```
To insert a value k into a tree, returning true if successful and false if not
Build a new node for k.
If tree is empty
  add new node as root node, return true.
If k == value at root
  return false (no duplicates allowed).
If k < value at root
  If root has no left child
    add new node as left child of root, return true
  Else insert k into left subtree of root.
If k > value at root
  If root has no right child
    add new node as right child of root, return true
  Else insert k into the right subtree of root.
```

## Remove Min Operation
* leftmost node is the min element
* cases: no left child (root is min), leftmost node is leaf (set parent's left child to null), left most node is internal (right child of node to be removed becomes parent's left child)

## BinarySearchTreeADT
```
public interface BinarySearchTreeADT<T> extends BinaryTreeADT<T> {
  public void addElement (T element);
  public T removeElement (T targetElement);
  public void removeAllOccurrences (T targetElement);
  public T removeMin( );
  public T removeMax( );
  public T findMin( );
  public T findMax( );
 }
```

 ################

## Balanced Trees
* **balanced tree:** has property that for any node in tree, height of left and right subtrees can differ by at most 1

## Analysis of Ordered List Implementations: Linked List vs. Balanced BST
| Operation      | LinkedList     | BinarySearchTreeList |
| :------------- | :------------- | :-------------       |
| removeFirst    | O(1)           | O(log n)             |
| removeLast     | O(n)           | O(log n)             |
| remove         | O(n)           | O(log n)             |
| first          | O(1)           | O(log n)             |
| last           | O(n)           | O(log n)             |
| contains       | O(n)           | O(log n)             |
| isEmpty        | O(1)           | O(1)                 |
| size           | O(1)           | O(1)                 |
| add            | O(n)           | O(log n)             |

## Degenerate Binary Trees
* without rebalancing, essentially a linked list
* add operation would be O(n) for a degenerate tree
