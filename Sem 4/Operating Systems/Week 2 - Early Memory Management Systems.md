
**Summarised by DeepSeek:**

---

### **1. Introduction**
- **Memory management** is critical for system performance.
- Early memory management schemes laid the foundation for modern techniques.
- Key factors: **memory availability** and **optimization** during job processing.

---

### **2. Types of Memory Allocation Schemes**
Four early memory management schemes:
1. **Single-User Contiguous Scheme**:
   - Entire program loaded into contiguous memory.
   - No multiprogramming; only one job at a time.
   - **Disadvantage**: Inefficient memory use, no support for multiple users.

2. **Fixed Partitions**:
   - Memory divided into fixed-size partitions.
   - Supports multiprogramming but suffers from **internal fragmentation** (unused memory within partitions).

3. **Dynamic Partitions**:
   - Memory allocated dynamically based on job size.
   - Reduces internal fragmentation but leads to **external fragmentation** (free memory scattered in small blocks).

4. **Relocatable Dynamic Partitions**:
   - Memory compaction to reduce fragmentation.
   - Programs relocated to create larger contiguous free memory blocks.
   - **Overhead**: Increased due to relocation and compaction.

---

### **3. Memory Allocation Algorithms**
- **First-Fit**: Allocates the first available memory block that fits the job.
- **Best-Fit**: Allocates the smallest available block that fits the job.
- **Worst-Fit**: Allocates the largest available block (theoretical, not practical).
- **Next-Fit**: Starts searching from the last allocated block.

---

### **4. Deallocation**
- **Fixed Partitions**: Simple deallocation by marking memory as free.
- **Dynamic Partitions**: Complex deallocation to merge adjacent free blocks.
  - **Case 1**: Merge with one adjacent free block.
  - **Case 2**: Merge with two adjacent free blocks.
  - **Case 3**: Isolated block deallocated without merging.

---

### **5. Relocatable Dynamic Partitions**
- **Compaction**: Relocates programs to create a large contiguous free memory block.
- **Special Registers**:
  - **Bounds Register**: Ensures programs don’t access unauthorized memory.
  - **Relocation Register**: Adjusts memory addresses after relocation.
- **Compaction Timing**:
  - When a certain percentage of memory is busy.
  - When jobs are waiting in the queue.
  - After a fixed time interval.

---

### **6. Summary**
- Early memory management schemes:
  - **Single-user**, **fixed partitions**, **dynamic partitions**, and **relocatable dynamic partitions**.
- **Limitations**:
  - Programs must be loaded contiguously.
  - Entire program resides in memory until completion.
  - Severe restrictions on job size.
- **Modern Trends**:
  - Programs no longer need to be stored contiguously.
  - Not all program segments reside in memory during execution.

---

### **Key Takeaways**
- Early memory management systems were designed for **batch processing** and had limited capabilities.
- **Fragmentation** (internal and external) was a major issue.
- **Relocatable dynamic partitions** introduced compaction to optimize memory use but increased overhead.
- These early systems paved the way for modern memory management techniques.

---

Keys stuff to understand:
- How partition work, 
	- Single User Contiguous Scheme
	- fixed-partition
	- best-fit vs First-fit
- How to deallocation dynamic/fix
- Relocate Dynamic Partition

---


vid source : https://youtu.be/LbgWuzmc8YE?si=j9ifax2oghSOOOk-

LO:
- What are the four early memory allocation schemes
- What is best-fit and First-Fit
- What is Deallocation and compaction
- Problems with early memory allocation Schemes

---
Characteristic:
- Entire programs need to be loaded into memory
- Be stored contiguously            # contiguously = in sequence
- Remain in the memory until entire job is completed

1. Single User Contiguous
2. Fixed Partitions
3. Dynamic Partitions
4. Relocatable Dynamic Partition

---
## Single User Contiguous
- Memory  guna sebelah2 therefore x practical sbb makan ruang

---
## Fixed Partitions
- allow more than one job to work
- memory are stored in smaller block
- size are STATIC unless system is rebooted

partition memory table include
- Partition size
- Memory Address
- Access --> which job are using the partitions
- Status

---
## Dynamic Partitions
- Still kept in contiguous block
- Job memory allocated based on request
- introduce problems --> Fragmentation = internal and external both wasting memory
- Fragmentation will occur as more jobs are loaded

First-Fit Allocation
- cari first space yg muat letak job
- doesnt take into account how much memory can be wasted in partition

Best-Fit Allocation
- Looks for the smallest partitions that can accommodate the job
- Efficient but slow

---
## Deallocation

- Release the memory after job is done

for Fixed Partition --> just free the partitions

For Dynamic Partitions --> there are three scenarios
1. Joining two free block
2. Joining three free block
3. Deallocating an isolated block

---
## Relocatable Dynamic Partitions
- Address some concern pasal Fragmentation and Demand
- Have a separate manager that manage the memory, 
- Which gather all the empty blocks and compact them into one block 
- Compactions of memory (Defragmentation) is performed by reclaim the fragmented space
- All programs must be reallocated to place them in one sequence memory location
- All tables must be updated
- Improve throughput but requires more overhead (lagi cepat tapi lagi susah)

---
## Are these viable today?
no

Problems with these methods:
1. require entire program to be loaded into memory
2. Require contiguous locations in memory