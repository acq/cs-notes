# Bloom filter

A bloom filter represents a set of elements.
It is composed of a bit array (of size `m`) and `k` different hash functions to a position in the bit array.  
Very efficient to detect if an element has been encountered, but may return false positives (no false negatives possible). Two results possible on query: "possibly in set" or "definitely not in set".

Add an element: puts the bits in the `k` array positions given by the hash functions to 1.  
Query an element: detect if the `k` array positions given by the hash functions are all set to 1.

Named after the creator (Burton Howard Bloom, 1970).

![Bloom filter implementation](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ac/Bloom_filter.svg/649px-Bloom_filter.svg.png)  
([Source](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ac/Bloom_filter.svg/649px-Bloom_filter.svg.png))

### False positives

Less than 10 bits per element are necessary for 1% false positive probability.

![Bloom filter fp probability](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/Bloom_filter_fp_probability.svg/600px-Bloom_filter_fp_probability.svg.png)  
([Source](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/Bloom_filter_fp_probability.svg/600px-Bloom_filter_fp_probability.svg.png))

Classic Bloom filters use 1.44 log2(1/e) bits of space per inserted key, where e is the false positive rate of the Bloom filter. ([Source](https://en.wikipedia.org/wiki/Bloom_filter#Interesting_properties))

### Union and intersection

Bloom filters with same bit array size and same hash functions have trivial union and intersection operations, using OR and AND bit operations.  
The union is lossless but the intersection may result in more false positives.

If the filters don't have the same properties, one can only evaluate the number of elements in the resulting sets though approximations.

### Uses ([Source](https://en.wikipedia.org/wiki/Bloom_filter#Examples))

* Akamai uses bloom filters to prevent caching of "one-hit wonders" (unique requests: approx 75% of traffic). If a request is not already in the bloom filter, it is added but not cached. Only request already present in the bloom filter will be cached.

* Google Chrome stores a bloom filter in the browser for a list of malicious URLs. If a URL matches the bloom filter, a request to Google is made to ensure it is indeed a malicious URL.

* Medium uses a bloom filter to avoid recommending previously read articles.
