**Summary From DeepSeek**

# **Algorithm Design & Analysis Notes**  
**Lecture 3: Sorting Algorithms**  

---

## **1. Recap: Asymptotic Notation**  
- **Big-O (O)**: Upper bound (worst-case).  
- **Big-Omega (Ω)**: Lower bound (best-case).  
- **Big-Theta (Θ)**: Tight bound (average-case).  

**Example**:  
- If `f(n) = n` and `g(n) = n²`, then `f(n) = O(g(n))` because `n` is upper bounded by `n²`.  

---

## **2. Sorting Algorithms Overview**  
Sorting algorithms arrange elements in a specific order (e.g., ascending or descending). In this lecture, we cover:  
1. **Bubble Sort**  
2. **Counting Sort**  
3. **Radix Sort**  
4. **Bucket Sort**  
5. **Shell Sort**  

---

## **3. Bubble Sort**  
### **How It Works**:  
- Compares adjacent elements and swaps them if they are in the wrong order.  
- Repeats until no swaps are needed (the list is sorted).  

### **Steps**:
1. Compare the first two elements. Swap if necessary.  
2. Move to the next pair and repeat.  
3. After one pass, the largest element "bubbles" to the end.  
4. Repeat for the remaining elements.  

### **Time Complexity**:  
- **Worst Case**: `O(n²)`  
- **Best Case**: `O(n)` (if the list is already sorted).  

### **Example**:  
Sort `[5, 1, 12, -5, 16]`:
1. Compare `5` and `1` → Swap → `[1, 5, 12, -5, 16]`.  
2. Compare `5` and `12` → No swap.  
3. Compare `12` and `-5` → Swap → `[1, 5, -5, 12, 16]`.  
4. Compare `12` and `16` → No swap.  
5. Repeat until sorted.  

---

## **4. Counting Sort**  
### **How It Works**:  
- Counts the occurrences of each element in the input array.  
- Uses these counts to place elements in the correct position in the output array.  

### **Steps**:  
1. Create a count array to store the frequency of each element.  
2. Modify the count array to store cumulative frequencies.  
3. Use the count array to place elements in the output array.  

### **Time Complexity**:  
- `O(n + k)`, where `k` is the range of input values.  

### **Example**:  
Sort `[4, 1, 3, 4, 3]`:  
1. Count array: `[0, 1, 0, 2, 2]`.  
2. Cumulative count: `[0, 1, 1, 3, 5]`.  
3. Output array: `[1, 3, 3, 4, 4]`.  

---

## **5. Radix Sort**  
### **How It Works**:  
- Sorts numbers digit by digit, starting from the least significant digit (rightmost) to the most significant digit (leftmost).  

### **Steps**:  
1. Sort numbers based on the least significant digit.  
2. Repeat for the next significant digit.  
3. Continue until all digits are processed.  

### **Time Complexity**:  
- `O(d(n + k))`, where `d` is the number of digits and `k` is the range of digits (usually 10).  

### **Example**:  
Sort `[742, 748, 54, 688, 412, 230, 935, 116, 161, 434, 385, 666, 31, 13, 365, 173, 16]`:  
1. Sort by ones digit: `[230, 161, 31, 742, 412, 13, 173, 54, 434, 935, 385, 365, 116, 666, 16, 748, 688]`.  
2. Sort by tens digit: `[412, 13, 116, 16, 230, 31, 434, 935, 742, 748, 54, 161, 365, 666, 173, 385, 688]`.  
3. Sort by hundreds digit: `[13, 16, 31, 54, 116, 161, 173, 230, 365, 385, 412, 434, 666, 688, 742, 748, 935]`.  

---

## **6. Bucket Sort**  
### **How It Works**:  
- Divides the input into buckets (ranges) and sorts each bucket individually.  
- Combines the sorted buckets to produce the final sorted array.  

### **Steps**:  
1. Create buckets (e.g., ranges 0-10, 11-20, etc.).  
2. Distribute elements into the appropriate buckets.  
3. Sort each bucket (e.g., using insertion sort).  
4. Concatenate the sorted buckets.  

### **Time Complexity**:  
- **Best Case**: `O(n)` (if elements are uniformly distributed).  
- **Worst Case**: `O(n²)` (if all elements fall into the same bucket).  

### **Example**:  
Sort `[27, 18, 8, 2, 6, 5, 15, 19]`:  
1. Buckets: `[0-10]: [8, 2, 6, 5]`, `[11-20]: [18, 15, 19]`, `[21-30]: [27]`.  
2. Sort each bucket: `[2, 5, 6, 8]`, `[15, 18, 19]`, `[27]`.  
3. Concatenate: `[2, 5, 6, 8, 15, 18, 19, 27]`.  

---

## **7. Shell Sort**  
### **How It Works**:  
- A generalization of insertion sort.  
- Sorts elements that are distant apart and gradually reduces the gap between elements.  

### **Steps**:  
1. Choose a gap size (e.g., `n/2`).  
2. Sort elements at that gap distance.  
3. Reduce the gap and repeat until the gap is 1.  

### **Time Complexity**:  
- Depends on the gap sequence. Typically `O(n log n)` to `O(n²)`.  

### **Example**:  
Sort `[18, 32, 12, 5, 38, 33, 16, 2]`:  
1. Gap = 4 → Sort elements at intervals of 4.  
2. Gap = 2 → Sort elements at intervals of 2.  
3. Gap = 1 → Perform a final insertion sort.  

---

## **8. Key Takeaways**  
1. **Bubble Sort**: Simple but slow (`O(n²)`).  
2. **Counting Sort**: Fast for small ranges (`O(n + k)`).  
3. **Radix Sort**: Efficient for large numbers (`O(d(n + k))`).  
4. **Bucket Sort**: Works well for uniformly distributed data (`O(n)`).  
5. **Shell Sort**: Improves insertion sort by sorting distant elements first.  

---

**Pro Tip**: Practice implementing these sorting algorithms to understand their strengths and weaknesses! 🚀  

--- 

**Next Lecture**: Advanced Sorting Algorithms & Dynamic Programming!
