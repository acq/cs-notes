# Hash Functions

Formal definition: any function that can be used to map data of arbitrary size to data of fixed size. ([Source](https://en.wikipedia.org/wiki/Hash_function))

Properties:  
* uniformity: a good hash function should have values uniformly distributed
* continuity: on the opposite, it can be desired that similar data have as continuous values as possible (rare, ex: nearest neighbor search)
* range: size of the output
* normalization: a hash function can ignore certain properties of the input data, meaning for this comparison, two different data can have the same hash (example: looking up for a person name: ignore case)

Minimal perfect hashing: n keys are mapped to 0 -> n-1 values (with no collisions). Hard to build, but can be useful for predetermined sets of keys.
