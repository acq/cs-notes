# Dijkstra's algorithm

Finds the shortest paths in a graph between a source node and all the other nodes. The graph should have negative weights.

Performance: O(E + V log V) with E = number of edges and V = number of vertices

The algorithm works by a creating two sets of nodes: the ones that have been visited (initialized with the source), and the remaining ones (initialized with all the other vertices).

Every time a node is added to the visited set, all its neighbors in the remaining set are given a tentative distance (min(distance to this node + distance between the nodes, previous tentative distance). We then pick the node with minimum tentative distance in the remaining set, move it to the visited set, and update its neighbors.

The best implementation for the remaining set is a priority queue, which allows priorities to be updated quickly (instead of removing + re-adding the element).
