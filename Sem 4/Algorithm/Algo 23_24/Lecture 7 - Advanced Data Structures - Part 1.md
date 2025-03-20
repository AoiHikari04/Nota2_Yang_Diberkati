# **Advanced Data Structures - Part 1**

---

## **1. Introduction to Advanced Data Structures**  
Advanced data structures optimize operations like **searching, insertion, and deletion** for efficient data processing. These structures are widely used in databases, caching, and compiler design.  

---

## **2. Direct Address Tables**  
### **How It Works**:  
- Uses an array where each **index corresponds to a key**.
- Searching, insertion, and deletion happen in **O(1) time**.

### **Pros & Cons**:  
✔️ Super fast lookup.  
❌ Requires large memory if the universe of keys is big.

### **Example**:  
- **Keys**: `{A, B, C, ..., Z}`  
- **Index Mapping**: `{0, 1, 2, ..., 25}`  

---

## **3. Hash Tables**  
### **How It Works**:  
- Uses a **hash function** to convert a key into an index.  
- **Reduces memory usage** compared to direct addressing.  
- Can have **collisions** (multiple keys mapping to the same index).  

### **Example**:  
- **Text**: `hello world`
- **Hash Function**: `h(k) = k mod table_size`
- **Issue**: If `k1` and `k2` map to the same index → **Collision!** 🔥

### **Time Complexity**:  
- **Best Case**: `O(1)` lookup.  
- **Worst Case**: `O(n)`, if all keys hash to the same slot.

---

## **4. Hash Functions**  
### **What Makes a Good Hash Function?**  
✔️ **Distributes keys evenly** across slots.  
✔️ **Minimizes collisions**.  
✔️ **Fast to compute**.  

### **Common Hashing Methods**:  
1. **Division Method**: `h(k) = k mod m`  
2. **Multiplication Method**: `h(k) = ⌊m(kA mod 1)⌋`, where `0 < A < 1`

---

## **5. Collision Handling Strategies**  
### **1️⃣ Chaining**  
- Each **slot** holds a **linked list** of keys with the same hash.  
- **Load Factor (α)** = `number of elements / number of slots`.  
- **Worst Case**: `O(n)`, if all keys land in the same slot.

### **2️⃣ Open Addressing**  
#### **🔷 Linear Probing**  
- If a slot is occupied, move to the **next** available slot.  
- ❌ **Issue**: Clustering happens, slowing down search.

#### **🔷 Quadratic Probing**  
- Instead of checking the **next** slot, move by `i²` positions.  
- ✔️ **Reduces clustering** but still not perfect.

#### **🔷 Double Hashing**  
- Uses **two** hash functions to find an empty slot.  
- Formula: `h(k, i) = (h1(k) + i × h2(k)) mod m`  
- ✔️ **Best method** for open addressing.

---

## **6. Practice Questions**  
1. Using **chaining**, insert `{6, 28, 19, 16, 20, 33, 12, 17, 10}` into a hash table of size `7`, with `h(k) = k mod 7`.  
2. Using **linear probing**, insert `{11, 4, 5, 12, 25, 18}` into a table of size `8`, with `h(k) = k mod 8`.  
3. Using **quadratic probing**, insert `{76, 40, 48, 5, 20}` into a table of size `7`, with `h(k) = (k + i²) mod 7`.  
4. Using **double hashing**, insert `{19, 26, 13, 47, 17}` into a table of size `7`, with `h1(k) = k mod 7` and `h2(k) = 5 - (k mod 5)`.  

---

## **7. Summary**  
📌 **Direct Address Tables** are fast but memory-hungry.  
📌 **Hash Tables** offer efficient storage with hashing.  
📌 **Good Hash Functions** reduce collisions.  
📌 **Collision Handling** includes **Chaining & Open Addressing**.  

🚀 **Master these techniques to level up your algorithm skills!**

