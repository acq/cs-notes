# Hash map

## Solving collisions

### Separate chaining

In separate chaining, each bucket is independent, and stores a list of entries with the same index (generally with a linked list).

Worst-case scenario: all elements end in the same bucket -> back to the performance of a linked list

Also has a memory overhead, due to the memoryr requirements of each linked lists

### Open addressing

In case of a collision, use a probe function to determine where to find an empty bucket, based of the index of the element.

Probe sequence options:
- linear probing: interval between probes is fixed (usually: 1)
- quadratic probing: interval calculated from a quadratic polynomial
- double hashing: interval between probes is computed by another hash function

Performance dramatically degrades when load factor > 0.7

More efficient than separate chaining in memory, but can be more costly in duration.

![Open vs close addressing](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/Hash_table_average_insertion_time.png/800px-Hash_table_average_insertion_time.png)

### Cuckoo hashing

Variant of open addressing. N hashmaps are used. If the slots corresponding to all hash functions are taken, the element drives an occupying element out, which iterates on his own hash values until it finds a spot, or moves yet another element out.

This allows very high space utilization.
