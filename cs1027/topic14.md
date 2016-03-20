# Topic 14: Binary Tree ADT

## Trees
* **tree:** nonlinear data structure used to represent entities that are in some hierarchical relationship
  * a set of elements of the same type such that: it is empty, or it has a distinguished element called the *root* from which descend zero or more *trees* (subtrees)

## Terminology
* **nodes:** the elements in the tree
* **edges:** connections between nodes
* **root:** *the* distinguished element that is the origin of the tree
* **leaf node:** node without an edge to another node
* **interior node:** node that isn't a leaf node
* **empty tree:** has no nodes and no edges
* **parent/predecessor:** node directly above in the hierarchy
* **child/successor:** node directly below in the hierarchy
* **siblings:** nodes that have ht same parent
* **ancestors:** its parent, the parent of its parent, etc.
* **descendants:** its children, the children of its children, etc.
* **path:** sequence of edges leading from one node to another
* **length of path:** number of edges on the path
* **height of a (non-empty) tree:** length of the longest path from the root to a leaf
  * by convention, height of an empty tree is -1
* **level of node:** number of edges between root and node
* **subtree (of a node):** consists of child node and all its descendants
* **degree/arity (of a node):** number of children it has
* **degree/arity (of a tree):** max degrees of the tree's nodes

## B-Trees
* **general tree:** tree each of whose node may have any number of children
* **n-ary tree:** tree each of whose nodes may have no more than n children
* **binary tree:** tree each of whose nodes may have no more than 2 children
  * **positional tree:** matters whether the subtree is left or right

## Tree Traversals
* **traversal:** requires that each node of the tree be *visited* once

### Preorder Traversal
* if tree not empty
  * visit root node of tree
  * perform preorder traversal of left subtree
  * perform preorder traversal of right subtree

### Inorder Traversal
* if tree not empty
  * perform inorder traversal of left subtree
  * visit root node of tree
  * perform inorder traversal of right subtree

### Postorder Traversal
* if tree not empty
  * perform postorder traversal of left subtree
  * perform postorder traversal of right subtree
  * visit root node of tree

### Level Order Traversal
```
// Assumption: the tree is not empty
Create an empty container to hold references to nodes yet to be visited.

Put reference to the root node in the container.

While the container is not empty {
  Remove a reference x from the container.
  Visit the node x points to.
  Put references to non-empty children of x in the container.
  }
}
```
* *stack*: push the right successor of node before left successor, we get *preorder* traversal
* *queue*: enqueue the left successor before the right, we get *level order* traversal

## Traversal Analysis
* binary tree with n nodes, 2n recursive calls at most --> O(n)

## Possible B-Tree Operations
* removeLeftSubtree, removeRightSubtree, removeAllElements
* isEmpty, size, contains, find, toString
* iteratorInOrder, iteratorPreOrder, iteratorPostOrder, iteratorLevelOrder

## Linked B-Tree Implementation
* *root*: reference the node that is the root of the tree
* *count*: keep track of the number of nodes in the tree
* binary tree node will contain reference to data element and reference to its left and right children

### BinaryTreeNode
* attributes: element, left, right

## LinkedBinaryTree
```java
// attributes
protected BinaryTreeNode<T> root;
protected int count;
//Creates empty binary tree
public LinkedBinaryTree() {
  count = 0;
  root = null;
}
//Creates binary tree with specified element as its root
public LinkedBinaryTree (T element) {
  count = 1;
  root = new BinaryTreeNode<T> (element);
}
/* Returns a reference to the specified target element if it is
found in this binary tree.
Throws an ElementNotFoundException if not found. */
public T find(T targetElement) throws ElementNotFoundException
{
  BinaryTreeNode<T> current =
  findAgain( targetElement, root );
  if ( current == null )
    throw new ElementNotFoundException("binary tree");
  return (current.element);
}
private BinaryTreeNode<T> findAgain(T targetElement, BinaryTreeNode<T> next)
{
  if (next == null)
    return null;
  if (next.element.equals(targetElement))
    return next;
  BinaryTreeNode<T> temp = findAgain(targetElement, next.left);
  if (temp == null)
    temp = findAgain(targetElement, next.right);
  return temp;
}
/* Performs an inorder traversal on this binary tree by
calling a recursive inorder method that starts with
the root.
Returns an inorder iterator over this binary tree */
public Iterator<T> iteratorInOrder()
{
  ArrayUnorderedList<T> tempList = new ArrayUnorderedList<T>();
  inorder(root, tempList);
  return tempList.iterator();
}
/* Performs a recursive inorder traversal.
Parameters are: the node to be used as the root
for this traversal, the temporary list for use in this
traversal */
protected void inorder (BinaryTreeNode<T> node, ArrayUnorderedList<T> tempList)
{
  if (node != null)
  {
    inorder(node.left, tempList);
    tempList.addToRear(node.element);
    inorder(node.right, tempList);
  }
}
```

## Expression Trees
* programs that manipulate/evaluate arithmetic expressions can use b-trees
* root node and interior nodes contain operations, leaf nodes contain operands
* ############# more on this later
