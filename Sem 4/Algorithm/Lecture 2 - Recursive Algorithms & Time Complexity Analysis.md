**Summary from DeepSeek**

# **Algorithm Design & Analysis Notes**  
**Lecture 2: Recursive Algorithms & Time Complexity Analysis**  

---

## **1. What is a Recursive Algorithm?**  
A **recursive algorithm** is a function that calls itself repeatedly until it reaches a **base case** (a simple problem that can be solved directly). It follows the **divide and conquer** approach:  
1. **Divide**: Break the problem into smaller subproblems.  
2. **Conquer**: Solve the subproblems recursively.  
3. **Combine**: Merge the solutions to solve the original problem.  

- **Example**: Factorial calculation, Merge Sort.  

---

## **2. Divide and Conquer Approach**  
This strategy is like breaking a big problem into smaller, manageable pieces, solving them, and then combining the results.  

- **Real-life Example**: Searching for a name in a phone book:  
  1. Open the book in the middle.  
  2. If the name isn’t there, decide whether to search the left or right half.  
  3. Repeat until you find the name.  

---

## **3. Recursive vs Iterative Algorithms**  
- **Iterative**: Uses loops (e.g., `for`, `while`) to repeat steps.  
- **Recursive**: Calls itself to solve smaller subproblems.  

**Key Difference**:  
- Iterative algorithms are often easier to analyze.  
- Recursive algorithms are elegant but harder to analyze due to function calls.  

---

## **4. Analyzing Recursive Algorithms**  
To analyze the **time complexity** of recursive algorithms, we use three methods:  
4. **Substitution Method**  
5. **Recursion Tree Method**  
6. **Master Method**  

---

### **4.1 Substitution Method**  
This method involves:  
7. **Guessing** the form of the solution.  
8. **Proving** it using mathematical induction.  

**Example**: Factorial  
- **Recurrence Relation**:  
  ```  
  T(n) = 1 + T(n-1)  
  ```  
- **Solution**:  
  ```  
  T(n) = O(n)  
  ```  

---

### **4.2 Recursion Tree Method**  
This method visualizes the recursive calls as a tree:  
9. **Nodes**: Represent the cost of subproblems.  
10. **Levels**: Represent the depth of recursion.  
11. **Sum**: Add the costs at each level to get the total time complexity.  

**Example**: Merge Sort  
- **Recurrence Relation**:  
  ```  
  T(n) = 2T(n/2) + n  
  ```  
- **Solution**:  
  ```  
  T(n) = O(n log n)  
  ```  

---

### **4.3 Master Method**  
This is a shortcut for solving recurrences of the form:  
```  
T(n) = aT(n/b) + f(n)  
```  
- **a**: Number of subproblems.  
- **b**: Size reduction factor.  
- **f(n)**: Cost of dividing and combining.  

**Three Cases**:  
12. **Case 1**: If `f(n) = O(n^c)` where `c < log_b(a)`, then `T(n) = O(n^log_b(a))`.  
13. **Case 2**: If `f(n) = Θ(n^c)` where `c = log_b(a)`, then `T(n) = O(n^c log n)`.  
14. **Case 3**: If `f(n) = Ω(n^c)` where `c > log_b(a)`, then `T(n) = O(f(n))`.  

**Example**: Merge Sort  
- **Recurrence Relation**:  
  ```  
  T(n) = 2T(n/2) + n  
  ```  
- **Solution**:  
  ```  
  T(n) = O(n log n)  
  ```  

---

## **5. Examples of Recursive Algorithms**  

### **5.1 Factorial**  
- **Problem**: Compute `n!` (e.g., `3! = 3 × 2 × 1 = 6`).  
- **Recursive Function**:  
  ```python  
  def factorial(n):  
      if n <= 1:  
          return 1  
      else:  
          return n * factorial(n-1)  
  ```  
- **Time Complexity**: `O(n)`  

---

### **5.2 Merge Sort**  
- **Problem**: Sort an array.  
- **Steps**:  
  1. **Divide**: Split the array into two halves.  
  2. **Conquer**: Sort each half recursively.  
  3. **Combine**: Merge the two sorted halves.  
- **Time Complexity**: `O(n log n)`  

---

### **5.3 Finding the Largest Number**  
- **Problem**: Find the largest number in an array.  
- **Recursive Function**:  
  ```python  
  def find_max(arr, n):  
      if n == 1:  
          return arr[0]  
      else:  
          return max(arr[n-1], find_max(arr, n-1))  
  ```  
- **Time Complexity**: `O(n)`  

---

## **6. Why Study Recursive Algorithms?**  
- **Elegance**: Recursive solutions are often simpler and more intuitive.  
- **Divide and Conquer**: Breaks complex problems into smaller, manageable parts.  
- **Wide Applications**: Used in sorting, searching, dynamic programming, and more.  

---

## **7. Key Takeaways**  
15. **Recursive Algorithms**: Solve problems by breaking them into smaller subproblems.  
16. **Time Complexity Analysis**: Use substitution, recursion tree, or master method.  
17. **Efficiency**: Recursive algorithms can be efficient but require careful analysis.  

---

**Pro Tip**: Practice analyzing recursive algorithms using all three methods to get comfortable with them! 🚀  

--- 

**Next Lecture**: Dynamic Programming & Greedy Algorithms!