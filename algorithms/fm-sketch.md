# FM-Sketch algorithm

Probabilistic algorithm to estimate the number of distinct elements in a stream.

It uses a hashmap (end space: binary strings of length L) and a bitmask of length L.
For each element e encountered, the bit in the bitmask matching the bit of least-significant value of h(e) is set to 1.
The number of distinct elements is ~ 2^B, where B is the left most 0 bit of the bitmask.

If there are N distinct elements in the stream:
* for i >> log(N), bitmask[i] = 0
* for i << log(N), bitmask[i] = 1
* for i ~ log(N), bitmask[i] could be either.
