# Bellman-Ford algorithm

Computes the shortests paths in a weighted graph from a source to all other nodes. It can handle negative weights, but the graph should not have negative cycles ("shortest path" would have no meaning).

Performance: O(V * E)

#### Initialisation

The source is given a distance of 0 and all other vertices are given a tentative distance of infinity.

#### Iterating

We do V-1 loops. In each, we iterate over all edges, and update the tentative distance if taking this edge would shorten it:  
if there is an edge of weight w from u to v, distance[v] = min(distance[v], distance[u]+w)

So at each step i, we compute the shortest paths of length i.

## Detecting negative-weight cycles

The algorithm can also be used to detect negative cycles.
Once all shortest paths have been calculated, we iterate over all edges and check consistency:  
if there is an edge of weight w from u to v and distance[v] > distance[u]+w, the graph contains a negative-weight cycle
