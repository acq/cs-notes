# Timsort

Sorting algorithm used in Java. Mix of merge and insertion sorts.

Timsort operates by runs. A run is a sequence of non-descending values (already sorted) or strictly descending values. When a run is encountered, it is then processed, its information (start and length) are stored, and the algorithm goes to the next run.  
But if a run is too short, elements are added to it via insertion, so that merges are done on equivalent-length runs.

When a new run Z is added to the queue, the two previous runs (X and Y) must respect the following rules:
* X > Y+Z
* Y > Z
If they do not, X and Y are merged.
