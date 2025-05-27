# Exp No: 26
# Prim's Minimum Spanning Tree (MST)

## AIM:

To find the Minimum Spanning Tree (MST) of a connected, undirected, weighted graph using Prim’s algorithm, implemented with an adjacency matrix.

## ALGORITHM:

Step 1: Initialize:
        Create arrays:
        key[] to store the minimum weight to connect to the MST (set all to ∞ except key[0] = 0),
        parent[] to store the MST (set all to None),
        mstSet[] to track included vertices (set all to False).  
        
Step 2: Repeat (V times):
        Pick the vertex u with the minimum key value not yet included in mstSet[].
        
Step 3: Include u in MST:
        Set mstSet[u] = True.
        
Step 4: Update keys of adjacent vertices:
        For each adjacent vertex v of u:
        If graph[u][v] is non-zero, v is not in mstSet[], and graph[u][v] < key[v],then update key[v] = graph[u][v] and parent[v] = u.
        
Step 5: Repeat Steps 2–4 until all vertices are included in MST.

Step 6: Construct MST:
        Use the parent[] array to retrieve and print the MST edges and their weights.

## PROGRAM :

```
# A Python program for Prim's Minimum Spanning Tree (MST) algorithm.
# The program is for adjacency matrix representation of the graph

import sys # Library for INT_MAX

class Graph():

	def __init__(self, vertices):
		self.V = vertices
		self.graph = [[0 for column in range(vertices)]
					for row in range(vertices)]

	# A utility function to print the constructed MST stored in parent[]
	def printMST(self, parent):
		print ("Edge   Weight")
		for i in range(1, self.V):
			print (parent[i], "-", i, "  ",self.graph[i][parent[i]])

	# A utility function to find the vertex with
	# minimum distance value, from the set of vertices
	# not yet included in shortest path tree
	def minKey(self, key, mstSet):

		# Initialize min value
		min = sys.maxsize

		for v in range(self.V):
			if key[v] < min and mstSet[v] == False:
				min = key[v]
				min_index = v

		return min_index

	# Function to construct and print MST for a graph
	# represented using adjacency matrix representation
	def primMST(self):

		# Key values used to pick minimum weight edge in cut
		key = [sys.maxsize] * self.V
		parent = [None] * self.V # Array to store constructed MST
		# Make key 0 so that this vertex is picked as first vertex
		key[0] = 0
		mstSet = [False] * self.V

		parent[0] = -1 # First node is always the root of

		for cout in range(self.V):

			# Pick the minimum distance vertex from
			# the set of vertices not yet processed.
			# u is always equal to src in first iteration
			u = self.minKey(key, mstSet)

			# Put the minimum distance vertex in
			# the shortest path tree
			mstSet[u] = True

			# Update dist value of the adjacent vertices
			# of the picked vertex only if the current
			# distance is greater than new distance and
			# the vertex in not in the shortest path tree
			for v in range(self.V):

				# graph[u][v] is non zero only for adjacent vertices of m
				# mstSet[v] is false for vertices not yet included in MST
				# Update the key only if graph[u][v] is smaller than key[v]
				if self.graph[u][v] > 0 and mstSet[v] == False and key[v] > self.graph[u][v]:
						key[v] = self.graph[u][v]
						parent[v] = u

		self.printMST(parent)

g = Graph(5)
g.graph = [ [0, 2, 0, 6, 0],
			[2, 0, 3, 8, 5],
			[0, 3, 0, 0, 7],
			[6, 8, 0, 0, 9],
			[0, 5, 7, 9, 0]]

g.primMST();

```

## OUTPUT:

![image](https://github.com/user-attachments/assets/51e76c0e-8da9-4c8a-83b5-2246aa876911)

## RESULT:

Thus the Python program to To find the Minimum Spanning Tree (MST) of a connected, undirected, weighted graph using Prim’s algorithm, implemented with an adjacency matrix was implemented successfully.

