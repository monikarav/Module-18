# Exp No: 28
# Dijkstra's Algorithm

## AIM:

To find the shortest path from a single source vertex to all other vertices in a connected, weighted, non-negative edge graph using Dijkstra's algorithm with an adjacency matrix representation.

## ALGORITHM:

Step 1: Create dist[] array to store shortest distances (initialize all to ∞, except dist[src] = 0).

Step 2: Create sptSet[] to track vertices included in the shortest path tree (initialize all to False).

Step 3: Select vertex x with the minimum distance not yet included in sptSet[]

Step 4: Set sptSet[x] = True.

Step 5: For every adjacent vertex y, if graph[x][y] is non-zero and y is not in sptSet[], update dist[y] if dist[x] + graph[x][y] < dist[y].

Step 6: Repeat steps 2–4 until all vertices are included.

Step 7: Print the shortest distance from source to each vertex.

## PROGRAM :

```
# Python program for Dijkstra's single source shortest path algorithm. 
# The program is for adjacency matrix representation of the graph

# Library for INT_MAX
import sys

class Graph():

	def __init__(self, vertices):
		self.V = vertices
		self.graph = [[0 for column in range(vertices)]
					for row in range(vertices)]

	def printSolution(self, dist):
		print("Vertex   Distance from Source")
		for node in range(self.V):
			print(node, "           ", dist[node])

	# A utility function to find the vertex with
	# minimum distance value, from the set of vertices
	# not yet included in shortest path tree
	def minDistance(self, dist, sptSet):

		# Initialize minimum distance for next node
		min = sys.maxsize

		# Search not nearest vertex not in the
		# shortest path tree
		for u in range(self.V):
			if dist[u] < min and sptSet[u] == False:
				min = dist[u]
				min_index = u

		return min_index

	# Function that implements Dijkstra's single source
	# shortest path algorithm for a graph represented
	# using adjacency matrix representation
	def dijkstra(self, src):

		dist = [sys.maxsize] * self.V
		dist[src] = 0
		sptSet = [False] * self.V

		for cout in range(self.V):

			# Pick the minimum distance vertex from
			# the set of vertices not yet processed.
			# x is always equal to src in first iteration
			x = self.minDistance(dist, sptSet)

			# Put the minimum distance vertex in the
			# shortest path tree
			sptSet[x] = True

			# Update dist value of the adjacent vertices
			# of the picked vertex only if the current
			# distance is greater than new distance and
			# the vertex in not in the shortest path tree
			for y in range(self.V):
				if self.graph[x][y] > 0 and sptSet[y] == False and 				dist[y] > dist[x] + self.graph[x][y]:
						dist[y] = dist[x] + self.graph[x][y]

		self.printSolution(dist)

# Driver program
g = Graph(9)
g.graph = [[0, 4, 0, 0, 0, 0, 0, 8, 0],
		[4, 0, 8, 0, 0, 0, 0, 11, 0],
		[0, 8, 0, 7, 0, 4, 0, 0, 2],
		[0, 0, 7, 0, 6, 14, 0, 0, 0],
		[0, 0, 0, 6, 0, 5, 0, 0, 0],
		[0, 0, 4, 14, 5, 0, 2, 0, 0],
		[0, 0, 0, 0, 0, 2, 0, 1, 6],
		[8, 11, 0, 0, 0, 0, 1, 0, 7],
		[0, 0, 2, 0, 0, 0, 6, 7, 0]
		];

g.dijkstra(0);
```

## OUTPUT:

![image](https://github.com/user-attachments/assets/8afbd380-173f-40b1-93ef-29ca4f1385bc)

## RESULT :

Thus the python program to  find the shortest path using Dijkstra's algorithm with an adjacency matrix representation was successfully implemented.

