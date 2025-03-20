**Summarise by ChatGPT**

# **Greedy Algorithms & Graphs - Part 1**

---

## **1. Introduction to Greedy Algorithms**
Greedy algorithms make **locally optimal choices** at each step in the hope of finding a **global optimum**.

### **Pros & Cons**:
✔️ Simple, fast, and easy to implement.
❌ Might not always provide the best solution.

**Common Optimization Problems Solved by Greedy Algorithms:**
1. **Activity Selection Problem**
2. **Knapsack Problem**
3. **Data Compression using Huffman Coding**

---

## **2. Activity Selection Problem**
**Problem:**
- Given a set of activities with start & finish times, find the **maximum number of non-overlapping activities**.
- **Constraint:** One activity at a time.

**Greedy Approach:**
4. Sort activities by **increasing finish time**.
5. Select the activity that **finishes earliest** and does not overlap.
6. Repeat until all activities are considered.

**Time Complexity:** `O(n)` (if sorted beforehand).

---

## **3. Knapsack Problem**
**Problem:**
- A thief has a knapsack of capacity `W` and must maximize the total value of stolen items.
- **Two Variants:**
  1. **0/1 Knapsack:** Can take an item or leave it.
  2. **Fractional Knapsack:** Can take fractions of items.

**Greedy Approach:**
7. Compute **value-to-weight ratio** for each item.
8. Sort items by **highest ratio**.
9. Take items with the highest ratio until the knapsack is full.

**Time Complexity:** `O(n log n)` (due to sorting step).

---

## **4. Huffman Coding (Data Compression)**
**Problem:**
- Reduce file size without losing information by assigning shorter binary codes to **frequent** characters.

**Greedy Approach:**
10. **Build a frequency table** of characters.
11. **Construct a Huffman tree**:
   - Merge two lowest-frequency characters into a new node.
   - Repeat until one node remains.
12. **Assign binary codes**:
   - Left branch → `0`, Right branch → `1`.

**Time Complexity:** `O(n log n)` (due to sorting & tree construction).

---

## **5. Introduction to Graphs**
Graphs represent relationships between objects using **vertices (nodes)** and **edges (connections)**.

### **Types of Graphs:**
13. **Directed Graphs** - Edges have direction (e.g., one-way roads).
14. **Undirected Graphs** - Edges have no direction (e.g., friendships).
15. **Weighted Graphs** - Edges have weights (e.g., distances on a map).
16. **Cyclic & Acyclic Graphs** - Presence/absence of cycles.

### **Graph Representations:**
- **Adjacency List** (Efficient for sparse graphs, `O(V + E)`).
- **Adjacency Matrix** (Efficient for dense graphs, `O(V^2)`).

---

## **6. Graph Traversal Algorithms**
### **6.1 Depth-First Search (DFS)**
- Explores **deep** into a graph before backtracking.
- Uses a **stack** (or recursion).
- **Time Complexity:** `O(V + E)`.
- **Applications:**
  - Cycle detection
  - Pathfinding
  - Topological sorting

### **6.2 Breadth-First Search (BFS)**
- Explores **level by level**.
- Uses a **queue**.
- **Time Complexity:** `O(V + E)`.
- **Applications:**
  - Shortest path in **unweighted graphs**
  - Connected components

---

## **7. Topological Sorting**
**Problem:**
- Given a **Directed Acyclic Graph (DAG)**, produce a linear ordering of vertices such that **each node appears before its dependencies**.

**Greedy Approach:**
17. Find nodes with **no incoming edges**.
18. Add them to the result and remove their outgoing edges.
19. Repeat until all nodes are processed.

**Time Complexity:** `O(V + E)`.

---

## **8. Practice Questions**
20. Find the **maximum** set of non-overlapping activities for `{(1, 3), (2, 5), (4, 6), (6, 7)}`.
21. Solve the **Fractional Knapsack Problem** for items `{(value: 60, weight: 10), (100, 20), (120, 30)}`, `W = 50`.
22. Construct the **Huffman Tree** for `{(a, 45), (b, 13), (c, 12), (d, 16), (e, 9), (f, 5)}`.
23. Perform **DFS and BFS** on the following graph:
   - `{A -> B, A -> C, B -> D, C -> E, D -> F, E -> F}`.
24. Perform **Topological Sort** on the DAG: `{(A, B), (A, C), (B, D), (C, D), (D, E)}`.

---

## **9. Summary**
📌 **Greedy Algorithms** solve optimization problems efficiently but might not always be optimal.
📌 **Graph Algorithms** (DFS, BFS, Topological Sort) help explore and process graphs efficiently.
📌 **Practice these techniques** to strengthen your algorithmic skills!

🚀 **Master Greedy Algorithms & Graphs to tackle complex problems efficiently!**

