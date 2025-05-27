# Exp No: 29
# Applications of graph

## AIM:

To find the minimum cost Hamiltonian cycle (shortest route that visits each city once and returns to the origin) for a Traveling Salesman Problem using a naive permutation-based solution.

## ALGORITHM :

Step 1: Input the number of cities (V = 4) and the cost matrix representing the graph.

Step 2: Create a list of all cities excluding the starting city s.

Step 3: Generate all permutations of the remaining cities to explore every possible tour.

Step 4: Calculate the total travel cost starting from s, visiting cities in the order of the permutation, and returning to s.

Step 5: Track the minimum cost of all possible Hamiltonian cycles.

Step 6: Return the minimum path cost found among all permutations.

Step 7: Output the result as the shortest possible route starting and ending at city s.

## PROGRAM :

```
# Python3 program to implement traveling salesman
# problem using naive approach.
from sys import maxsize
from itertools import permutations
V = 4

# implementation of traveling Salesman Problem
def travellingSalesmanProblem(graph, s):

	# store all vertex apart from source vertex
	vertex = []
	for i in range(V):
		if i != s:
			vertex.append(i)

	# store minimum weight Hamiltonian Cycle
	min_path = maxsize
	next_permutation=permutations(vertex)
	for i in next_permutation:

		# store current Path weight(cost)
		current_pathweight = 0

		# compute current path weight
		k = s
		for j in i:
			current_pathweight += graph[k][j]
			k = j
		current_pathweight += graph[k][s]

		# update minimum
		min_path = min(min_path, current_pathweight)
		
	return min_path


# Driver Code
if __name__ == "__main__":

	# matrix representation of graph
	graph = [[0, 10, 15, 20], [10, 0, 35, 25],
			[15, 35, 0, 30], [20, 25, 30, 0]]
	s = int(input())
	print(travellingSalesmanProblem(graph, s))
```

## OUTPUT:

![image](https://github.com/user-attachments/assets/dc770253-fda3-42c5-bca6-205eef5d06a2)

## RESULT :

Thus the python program to find the minimum cost Hamiltonian cycle for a Traveling Salesman Problem using a naive permutation-based solution was successfully implemented.

