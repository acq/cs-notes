# Count-min sketch

Probabilistic data structure for frequencies of events in a stream of data. (pretty close to a counting bloom filter)

Based on a two-dimensional array of `w` columns and `d` rows. Good values: `w = ceil(e/s)` and `d = ceil(ln(1/p))` for an error within a factor `s` with probability `p`.
Also need `d` hash functions (pairwise independant)

Adding an event: for each `i` in `[1:d]`, increment the value in `(i, h_i(event))` position, where `h_i` is the hash function associated with row `i`.
Probability of an event: `min table[i][h_i(event)]`

Caution: can overestimate probabilities, never underestimate them.
