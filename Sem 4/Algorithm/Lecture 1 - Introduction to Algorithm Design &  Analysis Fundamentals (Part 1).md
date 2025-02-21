<hr>

**Summary From:**

<h1>DeepSeek</h1>
### Summary of WIA2005: Algorithm Design and Analysis (Lecture 1)

#### **Course Overview**
- **Lecturer**: Dr. Hazrina Sofian (HS)
- **Student**: K1
- **Course Learning Outcomes (CLOs)**:
  1. Apply algorithmic paradigms to design efficient algorithms.
  2. Evaluate algorithm efficiency by calculating performance (T(n)).
  3. Use advanced data structures to reduce time complexity (T(n)).
  4. Integrate multiple algorithms to solve real-life problems using Python (group project).

#### **Lecture Topics**
- **Introduction to Algorithm Design & Analysis**:
  - **Learning Objectives**:
    1. Understand the role of algorithms in computing.
    2. Learn iterative algorithms.
    3. Analyze time complexity of iterative algorithms.
    4. Understand the growth of functions.

#### **Key Concepts**
1. **What is an Algorithm?**
   - A set of computational steps to solve a problem.
   - Takes input, processes it, and produces output.
   - Example: Sorting algorithms like Insertion Sort.

2. **Properties of Algorithms**:
   - Correctness: Must produce the correct output for every input.
   - Concrete steps: No ambiguity in execution.
   - Finite steps: Must terminate after a finite number of steps.

3. **Why Study Algorithms?**
   - Efficient algorithms save time and resources.
   - Example: Merge Sort outperforms Insertion Sort for large inputs.
   - Applications: Information retrieval, airline scheduling, election campaigns, internet routing, etc.

4. **Types of Algorithms**:
   - **Iterative**: Uses loops (e.g., for, while).
   - **Recursive**: Calls itself (to be covered in Lecture 2).

5. **Analysis of Algorithms**:
   - **Running Time (T(n))**: Measures the efficiency of an algorithm.
   - **Best Case**: Minimum time (e.g., already sorted input).
   - **Worst Case**: Maximum time (e.g., reverse-sorted input).
   - **Average Case**: Expected time for random input.

6. **Time Complexity**:
   - **Iterative Algorithms**: Analyze loops to determine T(n).
   - Example: A single for-loop has T(n) = O(n).

7. **Growth of Functions**:
   - **Asymptotic Analysis**: Study of how T(n) grows as n approaches infinity.
   - **Big-O Notation (O)**: Upper bound of T(n).
   - **Big-Omega Notation (Ω)**: Lower bound of T(n).
   - **Big-Theta Notation (Θ)**: Tight bound (average case).

8. **Examples of Asymptotic Notation**:
   - **Big-O**: f(n) = 2n + 3 is O(n).
   - **Big-Omega**: f(n) = 2n + 3 is Ω(n).
   - **Big-Theta**: f(n) = 2n + 3 is Θ(n).

#### **Practical Applications**
- Algorithms are used in:
  - Database searching (e.g., Linear Search).
  - Sorting (e.g., Insertion Sort, Merge Sort).
  - Real-world problems (e.g., airline scheduling, election campaigns).

#### **Tips and Ethics**
- Be punctual and respect peers.
- Participate actively in class and group work.
- Read tutorial questions before lectures.
- Start group projects early and be creative in problem-solving.

#### **References**
- Main Text: *Introduction to Algorithms* by Cormen et al. (MIT Press).
- Additional Texts: *Algorithms* by Erickson, *Algorithm Design* by Kleinberg & Tardos, and *Algorithms* by Sedgewick & Wayne.

#### **Conclusion**
- The goal is to design algorithms with lower growth rates (e.g., O(n) vs. O(n²)).
- Asymptotic analysis helps compare algorithm efficiency.
- Understanding iterative algorithms and their time complexity is foundational for advanced topics like recursion and dynamic programming.

---

# **Algorithm Design & Analysis Notes**  
**Lecture 1: Introduction to Algorithms**  

---

## **1. What is an Algorithm?**  
An **algorithm** is like a recipe for solving a problem. It takes **input** (the problem), follows a set of clear steps, and gives **output** (the solution).  

- **Example**: Sorting algorithms like **Insertion Sort** take a messy list of numbers and turn it into a neat, sorted list.  

---

## **2. What Makes a Good Algorithm?**  
For an algorithm to work well, it must have these **key properties**:  

1. **Correctness**: It always gives the right answer for any valid input.  
2. **Clear Steps**: Each step is easy to understand and follow.  
3. **Finiteness**: It doesn’t run forever—it stops after a certain number of steps.  
4. **Efficiency**: It uses resources (time and memory) wisely.  

---

## **3. Types of Algorithms**  
Algorithms come in two main flavors:  

1. **Iterative Algorithms**: Use loops (like `for` or `while`) to repeat steps until the job is done.  
   - **Example**: A `for` loop that prints "Hello World" 10 times.  

2. **Recursive Algorithms**: Break problems into smaller pieces and solve them by calling themselves.  
   - **Example**: **Merge Sort** splits a list into smaller parts, sorts them, and merges them back together.  

---

## **4. Analyzing Algorithms**  
We measure how good an algorithm is by its **running time (T(n))**, which depends on:  
- **Input Size (n)**: Bigger inputs take more time.  
- **Input Condition**: How the input is arranged affects performance.  
   - **Best Case**: Fastest running time (e.g., input is already sorted).  
   - **Worst Case**: Slowest running time (e.g., input is reverse-sorted).  
   - **Average Case**: Expected running time for random input.  

---

## **5. Time Complexity**  
Time complexity tells us how fast an algorithm’s running time grows as the input size increases. We use **asymptotic notation** to describe it:  

- **Big-O (O)**: The **worst-case** scenario. It’s the upper limit of running time.  
  - **Example**: If T(n) = 2n + 3, the time complexity is **O(n)**.  

- **Big-Omega (Ω)**: The **best-case** scenario. It’s the lower limit of running time.  
  - **Example**: If T(n) = 2n + 3, the time complexity is **Ω(n)**.  

- **Big-Theta (Θ)**: The **average-case** scenario. It’s the tight bound of running time.  
  - **Example**: If T(n) = 2n + 3, the time complexity is **Θ(n)**.  

---

## **6. Growth of Functions**  
The **growth rate** of a function shows how quickly the running time increases as the input size grows. Here are some common growth rates:  

- **O(1)**: Constant time (super fast, like accessing an array element).  
- **O(log n)**: Logarithmic time (fast, like binary search).  
- **O(n)**: Linear time (fair, like looping through an array).  
- **O(n log n)**: Linearithmic time (decent, like Merge Sort).  
- **O(n²)**: Quadratic time (slow, like Insertion Sort in the worst case).  
- **O(2ⁿ)**: Exponential time (super slow, like solving the Tower of Hanoi).  

**Goal**: Design algorithms with **lower growth rates** (e.g., O(n) is better than O(n²)).  

---

## **7. Real-World Applications**  
Algorithms are everywhere! Here’s where they’re used:  
- **Sorting**: Organizing data (e.g., sorting a playlist by song title).  
- **Searching**: Finding stuff (e.g., searching for a friend on social media).  
- **Optimization**: Solving tough problems efficiently (e.g., scheduling flights for an airline).  
- **Data Processing**: Handling big data (e.g., recommending movies on Netflix).  

---

## **8. Asymptotic Notation**  
Asymptotic notation helps us compare how efficient algorithms are by looking at their growth rates as the input size gets huge:  

- **Big-O (O)**: The **upper bound** (worst-case).  
  - **Example**: f(n) = 2n + 3 is **O(n)** because it grows linearly.  

- **Big-Omega (Ω)**: The **lower bound** (best-case).  
  - **Example**: f(n) = 2n + 3 is **Ω(n)** because it grows at least linearly.  

- **Big-Theta (Θ)**: The **tight bound** (average-case).  
  - **Example**: f(n) = 2n + 3 is **Θ(n)** because it grows exactly linearly.  

---

## **9. Why Study Algorithms?**  
- **Efficiency**: Faster algorithms save time and resources.  
- **Scalability**: Good algorithms can handle bigger problems.  
- **Problem-Solving**: They help you tackle real-world challenges.  
- **Innovation**: New algorithms can solve problems we couldn’t before.  

---

## **Conclusion**  
This lecture covers the **basics of algorithms**:  
- What they are and what makes them good.  
- How to measure their efficiency using **time complexity** and **asymptotic notation**.  
- Why designing algorithms with **lower growth rates** is key.  
- How algorithms are used in **real-world applications**.  

By mastering these concepts, you’ll be able to design, analyze, and compare algorithms to solve problems like a pro!  

--- 

**Pro Tip**: Keep practicing with examples (like sorting and searching) to get comfortable with these ideas! 🚀