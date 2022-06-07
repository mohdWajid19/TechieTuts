---
title: Depth First Search (DFS- Traversal)
author: Mohd wajid
date: 2022-05-08
tags: ["post", "featured"]
# image: /assets/blog/article-1.jpg
# imageAlt: This is a test
description: Depth First Algorithm is a Traversal Algorithm used in Trees and Graphs, Both has similar Implementation, with a slight change i.e. Graphs may contain cycles unlike trees 
---

<p> 
Depth First Traversal (or Search) for a graph is similar to Depth First Traversal of a tree. The only catch here is, unlike trees, graphs may contain cycles (a node may be visited twice). To avoid processing a node more than once, use a boolean visited array. 
</p>
<!-- <p>
Example: <br/>
Input: n = 4, e = 6 <br/>
0 -> 1, 0 -> 2, 1 -> 2, 2 -> 0, 2 -> 3, 3 -> 3 <br/>
Output: DFS from vertex 1 : 1 2 0 3 
</p> -->
<p>
Approach: <br/>
Depth-first search is an algorithm for traversing or searching tree or graph data structures. The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking. So the basic idea is to start from the root or any arbitrary node and mark the node and move to the adjacent unmarked node and continue this loop until there is no unmarked adjacent node. Then backtrack and check for other unmarked nodes and traverse them. Finally, print the nodes in the path.
</p>
<p>
Implementation: <br/>
Below are implementations of simple Depth First Traversal. The C++ implementation uses an adjacency list representation of graphs. STL’s list container is used to store lists of adjacent nodes.
</p>
<h2>Python 3 program to print DFS</h2>
<div class="table-container">
<pre class="inner-table-container">
from collections import defaultdict

class Graph:

	def __init__(self):
		self.graph = defaultdict(list)


	def addEdge(self, u, v):
		self.graph[u].append(v)

	def DFSUtil(self, v, visited):

		visited.add(v)
		print(v, end=' ')

		for neighbour in self.graph[v]:
			if neighbour not in visited:
				self.DFSUtil(neighbour, visited)

	def DFS(self, v):
		visited = set()

		self.DFSUtil(v, visited)

g = Graph()
g.addEdge(0, 1)
g.addEdge(0, 2)
g.addEdge(1, 2)
g.addEdge(2, 0)
g.addEdge(2, 3)
g.addEdge(3, 3)

print("Following is DFS from (starting from vertex 2)")
g.DFS(2)

</pre></div> <br/>
<h2>Java program to print DFS</h2>
<div class="table-container">
<pre class="inner-table-container">
import java.io.*;
import java.util.*;

class Graph {
	private int V; // No. of vertices
	private LinkedList<Integer> adj[];

	@SuppressWarnings("unchecked") 
    Graph(int v)
	{
		V = v;
		adj = new LinkedList[v];
		for (int i = 0; i < v; ++i)
			adj[i] = new LinkedList();
	}

	void addEdge(int v, int w)
	{
		adj[v].add(w); // Add w to v's list.
	}

	void DFSUtil(int v, boolean visited[])
	{
		visited[v] = true;
		System.out.print(v + " ");
		Iterator<Integer> i = adj[v].listIterator();
		while (i.hasNext()) {
			int n = i.next();
			if (!visited[n])
				DFSUtil(n, visited);
		}
	}

	void DFS(int v)
	{
		boolean visited[] = new boolean[V];
		DFSUtil(v, visited);
	}

	public static void main(String args[])
	{
		Graph g = new Graph(4);

		g.addEdge(0, 1);
		g.addEdge(0, 2);
		g.addEdge(1, 2);
		g.addEdge(2, 0);
		g.addEdge(2, 3);
		g.addEdge(3, 3);

		System.out.println(
			"Following is Depth First Traversal "
			+ "(starting from vertex 2)");

		g.DFS(2);
	}
}
</pre></div>
<p>
Time complexity: O(V + E), where V is the number of vertices and E is the number of edges in the graph.<br/>
Space Complexity: O(V), since an extra visited array of size V is required.
</p>
<p>
Handling A Disconnected Graph:

Solution: 
This will happen by handling a corner case. 
The above code traverses only the vertices reachable from a given source vertex. All the vertices may not be reachable from a given vertex, as in a Disconnected graph. To do a complete DFS traversal of such graphs, run DFS from all unvisited nodes after a DFS. 
The recursive function remains the same.
Algorithm: 
Create a recursive function that takes the index of the node and a visited array.
Mark the current node as visited and print the node.
Traverse all the adjacent and unmarked nodes and call the recursive function with the index of the adjacent node.
Run a loop from 0 to the number of vertices and check if the node is unvisited in the previous DFS, call the recursive function with the current node.
</p>
<h2>Java program to print DFS of a disconnected graph</h2>
<div class="table-container">
<pre class="inner-table-container">
import java.io.*;
import java.util.*;

class Graph {
	private int V; 
	private LinkedList<Integer> adj[];

	@SuppressWarnings("unchecked") 
    Graph(int v)
	{
		V = v;
		adj = new LinkedList[v];
		for (int i = 0; i < v; ++i)
			adj[i] = new LinkedList();
	}

	void addEdge(int v, int w)
	{
		adj[v].add(w); // Add w to v's list.
	}

	void DFSUtil(int v, boolean visited[])
	{
		visited[v] = true;
		System.out.print(v + " ");
		Iterator<Integer> i = adj[v].listIterator();
		while (i.hasNext()) {
			int n = i.next();
			if (!visited[n])
				DFSUtil(n, visited);
		}
	}

	void DFS()
	{
		boolean visited[] = new boolean[V];

		for (int i = 0; i < V; ++i)
			if (visited[i] == false)
				DFSUtil(i, visited);
	}

	// Driver Code
	public static void main(String args[])
	{
		Graph g = new Graph(4);

		g.addEdge(0, 1);
		g.addEdge(0, 2);
		g.addEdge(1, 2);
		g.addEdge(2, 0);
		g.addEdge(2, 3);
		g.addEdge(3, 3);

		System.out.println(
			"Following is Depth First Traversal");

		g.DFS();
	}
}
</pre></div>
<p>
Time complexity: O(V + E), where V is the number of vertices and E is the number of edges in the graph. <br/>
Space Complexity: O(V), since an extra visited array of size V is required.
</p>