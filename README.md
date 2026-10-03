# My_Custom_Graph_Package

# Java Object-Oriented Graph Library

Hi, I'm Shubham. I'm a 3rd-year B.Tech CSE (AI/ML) student at K.R. Mangalam University. 

I built this Object-Oriented Graph package entirely from scratch. While preparing for GATE and studying advanced data structures, I realized I didn't just want to blindly import standard libraries. I wanted to manually engineer the math and memory architecture under the hood before using them. 

This library is a highly optimized, generic Adjacency List graph implementation that can be used for anything from competitive programming to custom routing logic for transit simulators.

## Features & Architecture

* **Fully Generic (``)**: Vertices aren't limited to `int`. You can use `String`, `Character`, or custom Objects as your graph nodes.
* **Programming to an Interface**: The architecture separates the `Graph` blueprint from the `AdjacencyListGraph` implementation, meaning the underlying data structure can be swapped without breaking any algorithm code.
* **O(1) Time Complexity**: Built using Java `HashMap` and `HashSet` to ensure adding vertices, adding edges, and neighbor lookups happen in constant time.
* **Directed & Undirected Support**: Can act as a two-way street or a strict one-way directional network.

## Algorithms Implemented

I've separated all traversal and pathfinding logic into stateless, static utility methods in the `algo` package.

* **Breadth-First Search (BFS):** Layer-by-layer traversal using a Queue. Perfect for finding the shortest path in an unweighted network.
* **Depth-First Search (DFS):** Plunges deep into a path using a Stack. Useful for maze solving and topological sorting.
* **Dijkstra’s Algorithm:** Calculates the absolute shortest path across a weighted graph using a `PriorityQueue`. 
* **Bellman-Ford Algorithm:** A brute-force relaxation algorithm that accurately finds shortest paths even if the network has negative weight edges, and trips a wire if it detects a mathematically impossible negative-weight cycle.

## How to Use

If you want to use this in your own project, you can download the `.jar` file and import it, or just drop the `core`, `impl`, and `algo` folders into your workspace.

```java
import core.Graph;
import impl.AdjacencyListGraph;
import algo.GraphTraversal;

public class Main {
    public static void main(String[] args) {
        // Create a Directed Graph with String vertices
        Graph transitMap = new AdjacencyListGraph<>(true);

        transitMap.addVertex("Station A");
        transitMap.addVertex("Station B");
        transitMap.addEdge("Station A", "Station B", 5.5); // Add edge with weight

        // Find shortest paths using Dijkstra
        GraphTraversal.dijkstra(transitMap, "Station A");
    }
}
