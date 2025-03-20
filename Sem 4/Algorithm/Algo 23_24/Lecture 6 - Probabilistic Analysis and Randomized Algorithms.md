**Summarise By Gemini**
## WIA2005 Lecture 6: Probabilistic Analysis and Randomized Algorithms

This lecture dives into two important concepts in algorithm analysis: Probabilistic Analysis and Randomized Algorithms.  We'll explore how to analyze algorithms when input conditions are uncertain and how to incorporate randomness into algorithms themselves.

---

### Part 1: Probabilistic Analysis - When Input is Uncertain

**Overview of Running Time (Revision):**

Running time depends on:

1.  Number of steps executed.
2.  Time per step.
3.  **Condition of the input.**

Input size and condition significantly impact running time.  Consider sorting:

*   **Sorted Input (Best Case):** Fastest, skips many comparisons.
*   **Reverse Sorted Input (Worst Case):** Slowest, requires maximum comparisons.
*   **Nearly Sorted Input (Average Case):**  Performance falls between best and worst cases.

Probabilistic analysis helps us understand the *average-case* running time when the input distribution is known or can be assumed.

**The Hiring Problem:**

Imagine hiring an office assistant through an agency.  Each day, you interview a candidate and decide to hire or not. Hiring is more expensive than interviewing.  Your goal is to always have the best assistant.

*   **Cost:** Interviewing (Ci), Hiring (Ch)
*   **Goal:** Estimate the total cost.

**Probabilistic Analysis - The Four Steps:**

4.  **Declare an indicator random variable:**  Connect probabilities to expectations.  For example, if we flip a coin, the indicator variable for heads is 1 if heads, 0 if tails.
5.  **Determine the probability of the event:** What's the chance of getting heads? 1/2.
6.  **Determine the expectation of the event:** The expected value of the indicator variable.  For the coin flip: (1 * 1/2) + (0 * 1/2) = 1/2.
7.  **Determine the expected value in *n* trials:** What if we flip the coin *n* times?  The expected number of heads is n * 1/2.

**Two Conditions for Probabilistic Analysis:**

8.  **Known Input Distribution:** We need some knowledge or assumptions about how the input is distributed.
9.  **Random Input Sequence:** The input order must be random.

**Back to the Hiring Problem:**

*   **Worst-Case:** Candidates arrive in increasing order of quality.  No probabilistic analysis needed; we know the cost is high.
*   **Best-Case:** The best candidate is first. No probabilistic analysis needed; we know the cost is low.
*   **Average-Case:** Candidates arrive in random order.  *This* is where probabilistic analysis shines. We assume a random order for the candidates.

**Controlling the Input Order:**

To ensure randomness, we can change the hiring process: The agency sends a list of candidates, and *you* randomly choose who to interview each day.  This gives you control over the order.

**Indicator Random Variables for Hiring:**

Let Xi = 1 if the i-th candidate is hired, and 0 otherwise.

**Probability of Hiring the i-th Candidate:**

The probability of hiring the *i*-th candidate is 1/i.  (See Tutorial 6 for more details).

**Expected Hiring Cost (Lemma 1):**

The expected hiring cost is O(Ch ln n). This is significantly better than the worst-case cost of O(nCh).

**Flipping a Coin - Example:**

Method X() flips a coin. Heads take 1 second, tails take 3 seconds. What's the expected running time?

E[X] = (1 * 1/2) + (3 * 1/2) = 2 seconds.

---

### Part 2: Randomized Algorithms - Incorporating Randomness

Randomized algorithms use randomness as part of their logic.

**The Hiring Problem (Revisited):**

Instead of relying on the agency's order, the algorithm *itself* randomly permutes the candidate list.

**Key Idea:** Randomization is within the *algorithm*, not just the input.

**Randomized-Hire-Assistant:**

This algorithm randomly rearranges the candidate list before interviewing.  Even with the same input, different runs of the algorithm may result in a different number of hires. However, the *expected* hiring cost remains O(Ch ln n).

**Lemma 2:** Randomized-Hire-Assistant achieves the same performance as the manual randomization method.

**Randomly Permuting Arrays:**

Two common methods:

10.  **Permute by Sorting:** Assign random priorities to each element and sort based on those priorities.
11.  **Randomize in Place:**  For each position *i*, randomly swap the element at *i* with an element from *i* to *n*.

**Order Statistics - Finding the i-th Smallest Element:**

*   **Formal Definition:** The *i*-th order statistic is the *i*-th smallest element.
*   **Minimum:** *i* = 1
*   **Maximum:** *i* = *n*
*   **Median:** *i* = *n*/2 (or *n*/2 and *n*/2 + 1 for even *n*)

**Randomized-Select:**

This algorithm efficiently finds the *i*-th smallest element in expected linear time (O(n)).  It's based on the partitioning idea from Quicksort, but it only recurses on one side of the partition.

**Key Points of Randomized-Select:**

12.  Randomly choose a pivot.
13.  Partition the array around the pivot.
14.  Recursively search either the left or right subarray.

**SELECT (Deterministic Algorithm):**

This algorithm *guarantees* finding the *i*-th smallest element in O(n) time, but it's more complex than Randomized-Select. It uses a "median-of-medians" approach to choose a good pivot.  (See Appendix B for details).

---

### Key Takeaways

*   Probabilistic analysis helps analyze algorithms when input is uncertain, focusing on average-case performance.
*   Randomized algorithms incorporate randomness into their steps, often leading to simpler or more efficient solutions.
*   Randomized-Select finds the *i*-th smallest element in expected linear time.
*   Order statistics help define and find minimum, maximum, and median elements.
