# Hash Functions

Formal definition: any function that can be used to map data of arbitrary size to data of fixed size. ([Source](https://en.wikipedia.org/wiki/Hash_function))

Properties:  
* uniformity: a good hash function should have values uniformly distributed
* continuity: on the opposite, it can be desired that similar data have as continuous values as possible (rare, ex: nearest neighbor search)
* range: size of the output
* normalization: a hash function can ignore certain properties of the input data, meaning for this comparison, two different data can have the same hash (example: looking up for a person name: ignore case)

Minimal perfect hashing: n keys are mapped to 0 -> n-1 values (with no collisions). Hard to build, but can be useful for predetermined sets of keys.

### Cryptographic hash Functions

* easy to compute message -> hash
* infeasible to compute hash -> message (pre-image resistance)
* infeasible to modify the message without modifying the hash (second pre-image resistance)
* infeasible to find two messages with the same hash (collision resistance)

(3) and (4) are different: (3) starts from a given hash where (4) requires to find any two messages giving the same any hash  
Collision resistance: birthday paradox gives us an upper bound: if a hash function produces N bits of output, a collision can be (probably) found in 2^(N/2) hash operations

Hard to reverse problems:
* discret logarithm
* finding modular roots
* integer factorization
* subset sum

Applications:  
* integrity verification (~ checksum)
* password verification
* proof-of-work
* data identifier
* pseudorandom generation

In 2009, most commonly used: MD5 and SHA-1.  
MD5 broken before 2008.  
SHA-1: possible to find collisions in 2⁶³ operations (2005)  
Both vulnerable to rainbow tables (collections of message -> hash) => always use salt-ing

Current recommendations: SHA-2 (SHA256 or SHA512), or even better: SHA-3
