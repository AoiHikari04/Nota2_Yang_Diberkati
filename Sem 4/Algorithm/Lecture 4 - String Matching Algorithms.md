
**Summary from DeepSeek:**
# **Algorithm Design & Analysis Notes**  
**Lecture 4: String Matching Algorithms**  

---

## **1. Introduction to String Matching**  
String matching algorithms are used to find occurrences of a pattern `P` within a text `T`. These algorithms are widely used in text processing, search engines, and bioinformatics.  

---

## **2. Brute Force Algorithm**  
### **How It Works**:  
- Compares the pattern `P` with the text `T` for every possible shift of `P` relative to `T`.  
- Shifts the window by exactly 1 position to the right after each comparison.  

### **Time Complexity**:  
- **Worst Case**: `O(nm)`, where `n` is the length of `T` and `m` is the length of `P`.  

### **Example**:  
- **Text (`T`)**: `THIS IS A SIMPLE EXAMPLE`  
- **Pattern (`P`)**: `SIMPLE`  
- **Process**: Compare `P` with every substring of `T` of length `m`.  

---

## **3. Finite Automaton Algorithm**  
### **How It Works**:  
- Constructs a finite automaton (state machine) for the pattern `P`.  
- Uses the automaton to scan the text `T` in a single pass.  

### **Steps**:  
1. **Preprocessing**: Build the automaton for `P`.  
2. **Searching**: Use the automaton to find matches in `T`.  

### **Time Complexity**:  
- **Preprocessing**: `O(m|Σ|)`, where `Σ` is the alphabet size.  
- **Searching**: `O(n)`.  

### **Example**:  
- **Pattern (`P`)**: `ababaca`  
- **Automaton**: Each state represents a prefix of `P`. Transitions are based on characters in `T`.  

---

## **4. Rabin-Karp Algorithm**  
### **How It Works**:  
- Uses hashing to compare the pattern `P` with substrings of `T`.  
- If the hash values match, it performs a full comparison.  

### **Time Complexity**:  
- **Preprocessing**: `O(m)`.  
- **Searching**: `O(nm)` in the worst case, but `O(n + m)` on average.  

### **Example**:  
- **Text (`T`)**: `3141592653589793`  
- **Pattern (`P`)**: `31415`  
- **Process**: Compute hash values for `P` and each substring of `T` of length `m`.  

---

## **5. Knuth-Morris-Pratt (KMP) Algorithm**  
### **How It Works**:  
- Uses a preprocessed prefix function to skip unnecessary comparisons.  
- Shifts the pattern intelligently based on the prefix function.  

### **Time Complexity**:  
- **Preprocessing**: `O(m)`.  
- **Searching**: `O(n)`.  

### **Example**:  
- **Text (`T`)**: `abacababacabacab`  
- **Pattern (`P`)**: `abacab`  
- **Process**: Use the prefix function to avoid re-comparing characters.  

---

## **6. Tries and Suffix Tries**  
### **Tries**:  
- A tree-like data structure for storing strings.  
- Each node represents a character, and each path from the root to a leaf represents a string.  

### **Types of Tries**:  
1. **Standard Tries**: Stores all prefixes of a set of strings.  
2. **Compressed Tries**: Reduces space by merging nodes with single children.  
3. **Suffix Tries**: Stores all suffixes of a string.  

### **Time Complexity**:  
- **Standard Tries**: `O(n)` space, `O(dm)` search time.  
- **Suffix Tries**: `O(n)` space, `O(dm)` search time.  

### **Example**:  
- **Strings**: `{bear, bell, bid, bull, buy, sell, stock, stop}`  
- **Trie**: Each path from the root to a leaf represents a word.  

---

## **7. Key Takeaways**  
4. **Brute Force**: Simple but slow (`O(nm)`).  
5. **Finite Automaton**: Efficient for small alphabets (`O(n)` search time).  
6. **Rabin-Karp**: Uses hashing for average-case efficiency (`O(n + m)`).  
7. **KMP**: Skips unnecessary comparisons using a prefix function (`O(n + m)`).  
8. **Tries**: Efficient for storing and searching strings (`O(n)` space, `O(dm)` search time).  

---

**Pro Tip**: Practice implementing these algorithms to understand their strengths and weaknesses! 🚀  

--- 

**Next Lecture**: Advanced String Matching & Dynamic Programming!