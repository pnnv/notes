###### DFS Tree + Bridges
[sauce](https://codeforces.com/blog/entry/68138)
This is a tutorial/exploration of problems that can be solved using the "DFS tree" of a graph.

Sometimes there are questionable greedy algorithms whose correctness becomes obvious once you think about the DFS tree.

#### The DFS tree
Consider an undirected connected graph G. Let's run a depth-first traversal of the graph. It can be implemented by a recursive function, perhaps something like this:

```
 function visit(u):
     mark u as visited
     for each vertex v among the neighbours of u:
         if v is not visited:
             mark the edge uv
             call visit(v)
```

The edges marked while traversal form a spanning tree and can be called span edges