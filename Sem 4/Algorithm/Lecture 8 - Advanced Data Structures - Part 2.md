# **Advanced Data Structures - Part 2**

---

## **1. Introduction to Binary Search Trees (BST)**
Binary Search Trees (BST) are data structures that efficiently support fundamental operations like **searching, insertion, deletion,** and **traversal**. BSTs are used in databases, compilers, and search engines.

### **BST Properties**:
- Left child **≤** Parent node **≤** Right child.
- Searching, insertion, and deletion depend on the tree height (`h`).
- **Best case:** `O(log n)` (Balanced Tree)
- **Worst case:** `O(n)` (Skewed Tree)

---

## **2. BST Operations**
### **2.1 Searching in a BST**
Given a **key `k`**, the search follows:
1. If `k` == root’s key → Found 🎉
2. If `k` < root’s key → Search **left subtree**.
3. If `k` > root’s key → Search **right subtree**.

**Time Complexity:** `O(h)`, where `h` is tree height.

### **2.2 Finding Min/Max in a BST**
- **Minimum:** Leftmost node of the tree.
- **Maximum:** Rightmost node of the tree.

---

## **3. Traversing a BST**
BSTs can be traversed in three ways:

### **3.1 Preorder Traversal (Root → Left → Right)**
- Visits root first, then left subtree, then right.
- **Use Case:** Copying a tree.
- **Example Output:** `F, B, A, D, C, E, G, I, H`

### **3.2 Inorder Traversal (Left → Root → Right)**
- Visits left subtree first, then root, then right.
- **Use Case:** Prints BST in sorted order.
- **Example Output:** `A, B, C, D, E, F, G, H, I`

### **3.3 Postorder Traversal (Left → Right → Root)**
- Visits left subtree, right subtree, then root.
- **Use Case:** Deleting a tree.
- **Example Output:** `A, C, E, D, B, H, I, G, F`

---

## **4. Inserting into a BST**
To insert a node **v**:
4. Compare `v` with root.
5. If `v` < root → Move left.
6. If `v` > root → Move right.
7. Repeat until an empty position is found.

**Time Complexity:** `O(h)`

---

## **5. Deleting from a BST**
### **5.1 Deletion Cases:**
8. **Leaf Node:** Simply remove it.
9. **One Child:** Replace the node with its child.
10. **Two Children:** Replace the node with **inorder successor** (smallest node in right subtree).

**Time Complexity:** `O(h)`

---

## **6. Successor and Predecessor in a BST**
- **Successor:** The next largest element after a given node.
- **Predecessor:** The next smallest element before a given node.
- **Finding Successor:**
  - If right subtree exists → leftmost node of right subtree.
  - Else → Lowest ancestor whose **left** child is also an ancestor.

---

## **7. Practice Questions**
11. Construct a BST using `{15, 6, 18, 3, 7, 17, 20, 2, 4, 13, 9}`.
12. Find the inorder, preorder, and postorder traversals of the BST.
13. Insert **13** into a BST and show the updated tree.
14. Delete **7** from a BST and show the updated tree.

---

## **8. Summary**
📌 **BSTs** optimize search, insertion, and deletion operations.
📌 **Traversals** (Preorder, Inorder, Postorder) help analyze tree structures.
📌 **Balancing** a BST improves efficiency (`O(log n)` operations).
📌 **Practice constructing and modifying BSTs** to master them!

🚀 **Master BSTs and level up your data structure skills!**

