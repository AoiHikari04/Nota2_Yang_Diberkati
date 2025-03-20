**Summarise by ChatGPT**

# **Graphs - Part 2**

---

## **1. Introduction to Shortest Path Algorithms**
Shortest path algorithms help find the most efficient route between nodes in a graph. These are widely used in **navigation, networking, and optimization problems**.

### **Types of Shortest Path Problems**:
1. **Single-Source Shortest Path:** Find the shortest path from a single source node to all other nodes.
2. **All-Pairs Shortest Path:** Find the shortest path between every pair of nodes.

**Common Algorithms:**
- **Dijkstra’s Algorithm (Greedy Approach)**
- **Bellman-Ford Algorithm (Dynamic Programming Approach)**
- **Floyd-Warshall Algorithm (All-Pairs Shortest Path)**

---

## **2. Concept of Relaxation**
Relaxation is the process of gradually improving the shortest path estimates.

### **Steps in Relaxation:**
1. Initialize distances: Set the source distance to `0`, all others to `∞`.
2. For each edge `(u, v)`, update `v.d` if `u.d + w(u, v) < v.d`.
3. Repeat for all edges to ensure the shortest paths are found.

---

## **3. Dijkstra’s Algorithm**
Dijkstra’s algorithm finds the shortest path in a **weighted graph with non-negative edge weights**.

### **Steps:**
4. Mark all nodes as unvisited and set initial distances (`0` for source, `∞` for others).
5. Pick the **closest unvisited node** and update distances for its neighbors.
6. Repeat until all nodes have been visited.

**Time Complexity:** `O((V + E) log V)` (with a priority queue)

### **Example:**
Find the shortest path from `A` to all other nodes in:
```
     A
   /  \
  B    C
  |    |
  D -- E
```
- Start from `A`, update distances.
- Select the next closest node and repeat.

---

## **4. Bellman-Ford Algorithm**
Bellman-Ford is similar to Dijkstra but can handle **negative weights**.

### **Steps:**
7. Initialize distances (`0` for source, `∞` for others).
8. **Relax all edges** `|V|-1` times.
9. **Check for negative-weight cycles** by verifying if another relaxation is possible.

**Time Complexity:** `O(VE)`

### **Key Advantage:**
- Works with **negative-weight edges** unlike Dijkstra.

---

## **5. Floyd-Warshall Algorithm (All-Pairs Shortest Path)**
This algorithm finds the shortest path between **every pair of nodes**.

### **Steps:**
10. Create a distance matrix with initial values.
11. Use each node as an intermediate point to update distances.
12. Repeat for all nodes.

**Time Complexity:** `O(V^3)`

---

## **6. Practice Questions**
13. Apply **Dijkstra’s Algorithm** to the following graph and find shortest paths from `S`:
   ```
   S → A (4), S → B (2), A → B (1), A → C (5), B → C (8), B → D (10), C → D (2)
   ```
14. Solve **Bellman-Ford** for a graph with **negative-weight edges**.
15. Compute the shortest path for all pairs using **Floyd-Warshall Algorithm**.

---

## **7. Summary**
📌 **Dijkstra’s Algorithm** is efficient but doesn’t work with negative weights.
📌 **Bellman-Ford Algorithm** handles negative weights but is slower.
📌 **Floyd-Warshall Algorithm** solves the all-pairs shortest path problem efficiently.
📌 **Relaxation** is the key concept behind these algorithms.

🚀 **Master these algorithms to efficiently solve shortest path problems!**

