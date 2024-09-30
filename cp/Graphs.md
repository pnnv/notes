###### DFS Tree + Bridges
[sauce](https://codeforces.com/blog/entry/68138)
This is a tutorial/exploration of problems that can be solved using the "DFS tree" of a graph.

Sometimes there are questionable greedy algorithms whose correctness becomes obvious once you think about the DFS tree.

#### The DFS tree
Consider an undirected connected graph G. Let's run a depth-first traversal of the graph. It can be implemented by a recursive function, perhaps something like this:

```
1 function visit(u):
2     mark u as visited
3     for each vertex v among the neighbours of u:
4         if v is not visited:
5             mark the edge uv
6             call visit(v)
```

Let's look at the edges that were marked in line 5. They form a spanning tree of G, rooted at the vertex 1. We'll call these edges _span-edges_; all other edges are called _back-edges_.
