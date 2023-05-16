Algorithm to find the sortest path between nodes.

## Pseudo code
```python
function Dijkstra(graph, source):
	# set all graphs to infinity distance and set start to 0
	for each vertex V in Graph.Vertices
		dist[v] <- INFINITY
		prev[v] <- UNDEFINED
		add v to Q
	dist[source] <- 0

	# iterate through queue of items and add all neighbours distances to the existing distances. Replace the value if another neighbour is closer.
	while Q is not empty:
		u <- vertex in Q with min dist[u]
		remove u from Q
		for each neighbour V of u still in Q:
			alt <- dist[u] + Graph.Edges(u, v)
			if alt < dist[v]:
				dist[v] <- alt
				prev[v] <- u
	return dist[], prev[]
```

Start by going through all graph vertices (the points on the graph) and add their distances as `INFINITY` to some form of data structure that allows for key value pairs.

In this loop we also need to add the vertex to a queue of nodes to visit.

For example:

```tsx
function Dijstra(graph, startPoint) {
	const dist = {};
  const prev = {};
  const queue = [];
  for(const vertex in graph.vertices) {
     dist[vertex] = INFINITY; // assumption is vertex can be a key.
		 queue.push(vertex);
  }
}
```

Once you’ve gone through and generate a list of items that need to be checked we will then start from our start point. Investigate our neighbours. Return and update their distances `dist` and then move to the closets one.

This allows us to quickly explore the graph and find the closest value.

[[Myers diff algorithm]]