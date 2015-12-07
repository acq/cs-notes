# MinHash

Algorithm to quickly estimate how similar too sets are.

Measure of similarity: Jaccard similarity coefficient `J(A,B) = |A inter B| / |A union B|`

Uses `hmin` function: `hmin(S)` returns the value from the set for which the image through the hash function `h` is minimal.

Estimating `J(A,B)`: use `k` hashmaps and `J(A,B)` will be approximated by the ratio of hashmaps for which `hmin(A) == hmin(B)`.
