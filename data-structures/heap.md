# Heap

Tree-based data structure that satisfies the heap property: in a min-heap (resp. max-heap), if A is a the parent of B, A is smaller (resp. bigger) than B.

![Binary max-heap example](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Max-Heap.svg/501px-Max-Heap.svg.png)

Basic operations:
* find-max / find-min / peek
* insert
* extract-max / extract-min / pop

## Binary heap

Based on a binary tree, which will always be balanced.

### Insert

* Add the element at the bottom level of the heap
* Compare the added element with its parent. If in the right order, stop
* If in the wrong order, swap with the parent. Go to previous step.

There is no need to check the other branch when stopping: since the heap was valid before, the swapped element was bigger than any the other sub-tree.

### Extract

* Replace the root element with one on the bottom level
* Compare the new root with its new children. If in the correct order, stop.
* Swap the new root with the biggest children (for a max-heap). Go to previous step.

### Implementation

Commonly implemented with an array (like all binary trees, but a heap has the advantage of being always a complete tree).

![Binary tree array representation](https://upload.wikimedia.org/wikipedia/commons/8/86/Binary_tree_in_array.svg)

### Performance

* Insert: log n
* Extract: log n
* Merge: n
* Decrease-key: log n

## Fibonacci heap

Based on a collection of trees.

The roots of all trees are stored in a doubly linked list (the children of a node are also stored that way).  
For each node, we store its number of children and a potential mark.
We also keep a pointer to the smallest root (for a min-heap).

![Fibonacci heap](https://upload.wikimedia.org/wikipedia/commons/4/45/Fibonacci_heap.png)

The flexibility of the data structure allows us to delay operations, to keep the complexity of all operations low.

The name of Fibonacci comes from the fact that the size of a subtree of degree k is at least F(k+2).

### Peek

Trivial: we already have a pointer to the element.

### Merge

Just concatenate the lists of roots.

### Insert

Create a new heap and merge it (ie, create a new root node)

### Extract

First, remove the element on which we have a pointer. Its children become new roots.

We need to put the pointer on the new minimum root.

But we may have too many roots to check. So we need to reduce the number of roots by merging trees.  
We do this by finding roots with same degrees (number of children) and make one the parent of the other (obviously: the smaller one). We repeat until all roots have different degrees.  
In the end, we have at most log n roots. The whole operation takes log n.

Then we find the root with the smallest value. This takes log n.

### Decrease-key (modifying a value)

This uses the marks and takes O(1).  
A mark signifies the node already had one of its children cut. If we want to cut a child on a marked node, we cut the marked node too (recursively).

### Performance

* Insert: 1
* Extract: log n
* Merge: 1
* Decrease-key: 1
