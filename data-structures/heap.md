# Heap

Tree-based data structure that satisfies the heap property: in a min-heap (resp. max-heap), if A is a the parent of B, A is smaller (resp. bigger) than B.

![Binary max-heap example](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Max-Heap.svg/501px-Max-Heap.svg.png)

Basic operations:
* find-max / find-min / peek
* insert
* extract-max / extract-min / pop

## Binary heap

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
