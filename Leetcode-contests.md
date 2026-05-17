# Daily study structure

Use this routine every day:

|      Time | Activity                               |
| --------: | -------------------------------------- |
|    15 min | Read topic notes / understand pattern  |
| 30–40 min | Deeply study 1 main problem            |
| 30–40 min | Solve or dry-run 1 optional problem    |
|    20 min | Write mistakes + complexity + Go notes |
|    10 min | Re-code important template from memory |

Your daily goal is not “How many problems did I solve?”

Your daily goal is:

> “Can I recognize this pattern in an unknown contest problem?”

---

# 45-Day LeetCode Contest Plan in Go

## Week 1: Foundations, Go basics, and thinking process

### Day 1 — Contest mindset, Big-O, arrays, constraints

**Practice problems:**

* Two Sum
* Running Sum of 1d Array

**Copy-paste daily prompt:**

```text
Teach me Contest Problem Solving Basics for LeetCode using Go.

Use beginner-friendly language.

Cover:
1. How to read a problem statement carefully
2. How to observe input constraints
3. How constraints help choose an approach
4. Difference between brute force and optimized solution
5. Time and space complexity basics
6. How arrays are usually used in contest problems
7. Step-by-step thought process using Two Sum
8. Dry run with a small example
9. Pseudocode
10. Go code structure
11. Common mistakes beginners make
12. Edge cases to test

Focus more on thinking and reasoning than just the final solution.
```

---

### Day 2 — Hash Map pattern

**Practice problems:**

* Two Sum
* Contains Duplicate

**Copy-paste daily prompt:**

```text
Teach me the Hash Map pattern for LeetCode contests using Go.

Explain in simple language:
1. What problem signals suggest using a hash map
2. Why hash map improves brute force solutions
3. How to identify keywords like frequency, lookup, count, seen before, pair, duplicate
4. How to move from O(n^2) brute force to O(n)
5. Step-by-step thought process for Two Sum
6. Dry run with an easy example
7. Pseudocode
8. Go map syntax and template
9. Common mistakes with Go maps
10. Time and space complexity
11. Edge cases

Also explain how to think during a contest when I see a problem involving counting or quick lookup.
```

---

### Day 3 — Frequency counting

**Practice problems:**

* Valid Anagram
* Majority Element

**Copy-paste daily prompt:**

```text
Teach me Frequency Counting using Hash Maps for LeetCode contests in Go.

Cover:
1. What frequency counting means
2. How to recognize frequency-based problems
3. Difference between storing seen values and storing counts
4. How frequency helps compare strings, arrays, or elements
5. Brute force idea first
6. Optimized approach using map
7. Step-by-step thought process for Valid Anagram
8. Dry run with a simple example
9. Pseudocode
10. Go implementation notes using map[rune]int and map[int]int
11. Common mistakes with characters and strings in Go
12. Time and space complexity
13. Edge cases

Train me to observe repeated elements and convert that observation into a frequency map approach.
```

---

### Day 4 — Sorting as a thinking tool

**Practice problems:**

* Merge Intervals
* Sort Colors

**Copy-paste daily prompt:**

```text
Teach me how Sorting helps solve LeetCode contest problems using Go.

Explain:
1. Why sorting can simplify a problem
2. How sorting changes the way we think about relationships
3. How to recognize sorting clues in problem statements
4. Common clues: intervals, minimum difference, grouping, ordering, greedy
5. Brute force approach before sorting
6. Optimized approach after sorting
7. Step-by-step thought process for Merge Intervals
8. Dry run with an easy example
9. Pseudocode
10. Go sort.Slice syntax and template
11. Common mistakes while sorting slices in Go
12. Time and space complexity
13. Edge cases

Focus on why sorting makes the problem easier, not just how to code it.
```

---

### Day 5 — Two Pointers

**Practice problems:**

* Valid Palindrome
* 3Sum

**Copy-paste daily prompt:**

```text
Teach me the Two Pointers pattern for LeetCode contests using Go.

Explain:
1. What two pointers mean
2. When to use left and right pointers
3. How sorted arrays help two pointers
4. How to identify clues like pair, sum, palindrome, remove duplicates, opposite ends
5. Brute force approach first
6. How two pointers reduce unnecessary checks
7. Step-by-step thought process for Valid Palindrome
8. Step-by-step intuition for 3Sum
9. Dry run with easy examples
10. Pseudocode
11. Go code structure
12. Common mistakes with pointer movement
13. Time and space complexity
14. Edge cases

Focus on how to decide which pointer to move and why.
```

---

### Day 6 — Prefix Sum

**Practice problems:**

* Range Sum Query - Immutable
* Subarray Sum Equals K

**Copy-paste daily prompt:**

```text
Teach me Prefix Sum for LeetCode contests using Go.

Explain:
1. What prefix sum means in simple words
2. Why repeated range sum queries become faster
3. How to recognize prefix sum problems
4. Clues: subarray sum, range sum, sum equals k, continuous segment
5. Brute force solution first
6. How prefix sum removes repeated work
7. Step-by-step thought process for Subarray Sum Equals K
8. Dry run with an easy example
9. Pseudocode
10. Go code structure using slices and maps
11. Common mistakes with prefix sum initialization
12. Time and space complexity
13. Edge cases

Focus on how to convert a subarray question into a prefix sum relationship.
```

---

### Day 7 — Weekly revision day

**Practice:**

* Revisit 2 problems from Days 1–6
* Do not solve new problems unless revision is complete

**Copy-paste daily prompt:**

```text
Help me revise my Week 1 LeetCode contest preparation topics in Go.

Topics:
- Big-O and constraints
- Hash map
- Frequency counting
- Sorting
- Two pointers
- Prefix sum

For each topic, explain:
1. What the pattern is
2. How to recognize it in a problem statement
3. What brute force usually looks like
4. How the optimized idea works
5. One easy dry run
6. Go implementation notes
7. Common mistakes
8. Important edge cases

Also give me a self-check quiz to test whether I can identify the right pattern.
```

---

## Week 2: Sliding window, stack, binary search, greedy

### Day 8 — Sliding Window basics

**Practice problems:**

* Maximum Average Subarray I
* Longest Substring Without Repeating Characters

**Copy-paste daily prompt:**

```text
Teach me the Sliding Window pattern for LeetCode contests using Go.

Explain:
1. What a window means
2. Difference between fixed-size and variable-size window
3. How to recognize sliding window problems
4. Clues: contiguous subarray, substring, longest, shortest, at most, at least
5. Brute force approach first
6. How sliding window avoids recalculating
7. Step-by-step thought process for Longest Substring Without Repeating Characters
8. Dry run with an easy example
9. Pseudocode
10. Go implementation using two pointers and map
11. Common mistakes when shrinking the window
12. Time and space complexity
13. Edge cases

Focus on when to expand the right pointer and when to shrink the left pointer.
```

---

### Day 9 — Stack pattern

**Practice problems:**

* Valid Parentheses
* Min Stack

**Copy-paste daily prompt:**

```text
Teach me the Stack pattern for LeetCode contests using Go.

Explain:
1. What stack means: last in, first out
2. How stack helps remember previous elements
3. How to recognize stack problems
4. Clues: parentheses, undo, previous greater/smaller, nested structure
5. Brute force thinking first
6. Optimized stack approach
7. Step-by-step thought process for Valid Parentheses
8. Dry run with an easy example
9. Pseudocode
10. Go slice-based stack template
11. Common mistakes with empty stack checks
12. Time and space complexity
13. Edge cases

Focus on why the most recent unmatched element matters.
```

---

### Day 10 — Monotonic Stack

**Practice problems:**

* Daily Temperatures
* Next Greater Element I

**Copy-paste daily prompt:**

```text
Teach me Monotonic Stack for LeetCode contests using Go.

Explain:
1. What a monotonic stack is
2. Difference between normal stack and monotonic stack
3. How to recognize next greater / next smaller problems
4. Clues: next warmer day, next greater element, nearest smaller, previous greater
5. Brute force solution first
6. Why monotonic stack avoids repeated scanning
7. Step-by-step thought process for Daily Temperatures
8. Dry run with a simple array
9. Pseudocode
10. Go code template using indexes in stack
11. Common mistakes with storing values vs indexes
12. Time and space complexity
13. Edge cases

Focus on why each element is pushed and popped at most once.
```

---

### Day 11 — Binary Search basics

**Practice problems:**

* Binary Search
* Search Insert Position

**Copy-paste daily prompt:**

```text
Teach me Binary Search basics for LeetCode contests using Go.

Explain:
1. What binary search means
2. Why it requires a sorted or monotonic search space
3. How to recognize binary search problems
4. Clues: sorted array, find position, minimum possible, maximum possible
5. Brute force linear search first
6. How binary search cuts the search space
7. Step-by-step thought process for Search Insert Position
8. Dry run with an easy example
9. Pseudocode
10. Go binary search template
11. Common mistakes with left, right, mid
12. Infinite loop mistakes
13. Time and space complexity
14. Edge cases

Focus on how to update left and right correctly.
```

---

### Day 12 — Binary Search on Answer

**Practice problems:**

* Koko Eating Bananas
* Capacity To Ship Packages Within D Days

**Copy-paste daily prompt:**

```text
Teach me Binary Search on Answer for LeetCode contests using Go.

Explain:
1. What binary search on answer means
2. How it differs from normal binary search
3. How to recognize monotonic answer problems
4. Clues: minimum possible maximum, maximum possible minimum, can we do it with x
5. Brute force over answer first
6. How the check function works
7. Step-by-step thought process for Koko Eating Bananas
8. Dry run with a small example
9. Pseudocode
10. Go code structure with helper function can()
11. Common mistakes in choosing low and high
12. Time and space complexity
13. Edge cases

Focus on how to build the condition: if x works, what happens for bigger or smaller x?
```

---

### Day 13 — Greedy basics

**Practice problems:**

* Jump Game
* Assign Cookies

**Copy-paste daily prompt:**

```text
Teach me the Greedy pattern for LeetCode contests using Go.

Explain:
1. What greedy means in simple words
2. Why greedy chooses the best local decision
3. How to recognize greedy problems
4. Clues: minimum, maximum, earliest, farthest, choose optimally step by step
5. Why greedy is not always correct
6. How to reason whether greedy works
7. Step-by-step thought process for Jump Game
8. Dry run with an easy example
9. Pseudocode
10. Go code structure
11. Common mistakes in greedy reasoning
12. Time and space complexity
13. Edge cases

Focus on how to justify the greedy choice, not just code it.
```

---

### Day 14 — Weekly revision + mini contest

**Practice:**

* Pick 2 old easy/medium problems
* Solve with a 60-minute timer
* Spend another 60 minutes reviewing

**Copy-paste daily prompt:**

```text
Help me revise Week 2 LeetCode contest topics in Go.

Topics:
- Sliding window
- Stack
- Monotonic stack
- Binary search
- Binary search on answer
- Greedy

For each topic, explain:
1. Pattern recognition clues
2. Brute force idea
3. Optimized idea
4. One simple dry run
5. Pseudocode
6. Go implementation template
7. Common mistakes
8. Edge cases
9. Time and space complexity

Then give me a 60-minute mini contest strategy for solving 2 problems and reviewing mistakes.
```

---

## Week 3: Graphs, recursion, BFS/DFS, heap, union find

### Day 15 — Recursion thinking

**Practice problems:**

* Subsets
* Generate Parentheses

**Copy-paste daily prompt:**

```text
Teach me Recursion and Backtracking thinking for LeetCode contests using Go.

Explain:
1. What recursion means
2. How to think in terms of choices
3. How to identify backtracking problems
4. Clues: generate all, all combinations, all subsets, all valid ways
5. Brute force tree of choices
6. How backtracking explores and then undoes choices
7. Step-by-step thought process for Subsets
8. Dry run with nums = [1,2,3]
9. Pseudocode
10. Go code structure using recursive function
11. Common mistakes with slices in Go
12. Time and space complexity
13. Edge cases

Focus on decision trees and how to break a problem into choices.
```

---

### Day 16 — BFS on grids

**Practice problems:**

* Number of Islands
* Rotting Oranges

**Copy-paste daily prompt:**

```text
Teach me BFS on Grid problems for LeetCode contests using Go.

Explain:
1. What BFS means
2. Why BFS explores level by level
3. How to recognize grid BFS problems
4. Clues: shortest distance, spreading, nearest, level, minutes
5. How to represent directions
6. Step-by-step thought process for Rotting Oranges
7. Dry run with a small grid
8. Pseudocode
9. Go queue implementation using slices
10. Common mistakes with visited marking
11. Time and space complexity
12. Edge cases

Focus on why BFS is useful when each step has equal cost.
```

---

### Day 17 — DFS on grids and graphs

**Practice problems:**

* Number of Islands
* Flood Fill

**Copy-paste daily prompt:**

```text
Teach me DFS for Grid and Graph problems in LeetCode contests using Go.

Explain:
1. What DFS means
2. Difference between DFS and BFS
3. How to recognize DFS problems
4. Clues: connected components, island, region, path exists
5. Recursive DFS thought process
6. Iterative DFS idea
7. Step-by-step thought process for Number of Islands
8. Dry run with a small grid
9. Pseudocode
10. Go recursive DFS template
11. Common mistakes with boundaries and visited
12. Time and space complexity
13. Edge cases

Focus on how DFS marks one full connected component.
```

---

### Day 18 — Graph adjacency list

**Practice problems:**

* Find if Path Exists in Graph
* Clone Graph

**Copy-paste daily prompt:**

```text
Teach me Graph Representation using adjacency list for LeetCode contests in Go.

Explain:
1. What a graph is
2. What nodes and edges mean
3. Directed vs undirected graph
4. How to build adjacency list in Go
5. How to recognize graph problems from statements
6. Clues: cities, roads, connections, courses, dependencies, network
7. BFS/DFS approach for path existence
8. Step-by-step thought process for Find if Path Exists in Graph
9. Dry run with a small graph
10. Pseudocode
11. Go map/slice adjacency template
12. Common mistakes
13. Time and space complexity
14. Edge cases

Focus on converting a story problem into nodes and edges.
```

---

### Day 19 — Topological Sort

**Practice problems:**

* Course Schedule
* Course Schedule II

**Copy-paste daily prompt:**

```text
Teach me Topological Sort for LeetCode contests using Go.

Explain:
1. What dependency order means
2. When topological sort is needed
3. How to recognize it
4. Clues: prerequisites, tasks before tasks, dependency, ordering
5. What indegree means
6. BFS Kahn's Algorithm intuition
7. Step-by-step thought process for Course Schedule
8. Dry run with a small example
9. Pseudocode
10. Go implementation using queue and adjacency list
11. Common mistakes with edge direction
12. Time and space complexity
13. Edge cases

Focus on how to detect cycles using indegree.
```

---

### Day 20 — Heap / Priority Queue

**Practice problems:**

* Kth Largest Element in an Array
* Top K Frequent Elements

**Copy-paste daily prompt:**

```text
Teach me Heap and Priority Queue for LeetCode contests using Go.

Explain:
1. What a heap is
2. Min heap vs max heap
3. How to recognize heap problems
4. Clues: kth largest, top k, smallest, largest, repeatedly get best element
5. Brute force using sorting first
6. Why heap can be better
7. Step-by-step thought process for Kth Largest Element
8. Dry run with a small example
9. Pseudocode
10. Go container/heap template
11. Common mistakes with Less function
12. Time and space complexity
13. Edge cases

Focus on when heap is better than sorting and when sorting is enough.
```

---

### Day 21 — Weekly revision day

**Practice:**

* Revisit 1 graph problem
* Revisit 1 recursion/backtracking problem

**Copy-paste daily prompt:**

```text
Help me revise Week 3 LeetCode contest topics in Go.

Topics:
- Recursion
- Backtracking
- BFS on grids
- DFS on grids
- Graph adjacency list
- Topological sort
- Heap

For each topic, explain:
1. How to recognize the pattern
2. What the brute force idea is
3. Why the optimized method works
4. One easy dry run
5. Pseudocode
6. Go implementation notes
7. Common mistakes
8. Edge cases
9. Time and space complexity

Also give me a pattern-recognition quiz using short problem statements.
```

---

## Week 4: Dynamic programming foundations

### Day 22 — DP basics: 1D DP

**Practice problems:**

* Climbing Stairs
* Min Cost Climbing Stairs

**Copy-paste daily prompt:**

```text
Teach me Dynamic Programming basics for LeetCode contests using Go.

Explain:
1. What DP means in simple language
2. What overlapping subproblems mean
3. What optimal substructure means
4. How to recognize DP problems
5. Clues: count ways, minimum cost, maximum profit, choices at each step
6. Brute force recursion first
7. How memoization improves recursion
8. How tabulation works
9. Step-by-step thought process for Climbing Stairs
10. Dry run with small n
11. Pseudocode
12. Go code structure for memoization and tabulation
13. Common DP mistakes
14. Time and space complexity
15. Edge cases

Focus on how to define dp[i] clearly.
```

---

### Day 23 — Take / Not Take DP

**Practice problems:**

* House Robber
* Delete and Earn

**Copy-paste daily prompt:**

```text
Teach me Take / Not Take Dynamic Programming for LeetCode contests using Go.

Explain:
1. What take/not take means
2. How to recognize this DP pattern
3. Clues: choose or skip, cannot take adjacent, maximize value
4. Brute force recursion decision tree
5. How to convert recursion to DP
6. Step-by-step thought process for House Robber
7. Dry run with a small array
8. Pseudocode
9. Go implementation
10. Common mistakes in state definition
11. Time and space complexity
12. Edge cases

Focus on how each index gives two choices: take current or skip current.
```

---

### Day 24 — Grid DP

**Practice problems:**

* Unique Paths
* Minimum Path Sum

**Copy-paste daily prompt:**

```text
Teach me Grid Dynamic Programming for LeetCode contests using Go.

Explain:
1. What grid DP means
2. How movement constraints create DP states
3. How to recognize grid DP problems
4. Clues: move right/down, path count, minimum path, matrix
5. Brute force recursion first
6. How DP avoids recalculating paths
7. Step-by-step thought process for Unique Paths
8. Dry run with a small grid
9. Pseudocode
10. Go 2D slice implementation
11. Common mistakes with first row and first column
12. Time and space complexity
13. Edge cases

Focus on how dp[row][col] depends on previous cells.
```

---

### Day 25 — Subsequence DP

**Practice problems:**

* Longest Increasing Subsequence
* Is Subsequence

**Copy-paste daily prompt:**

```text
Teach me Subsequence-based thinking for LeetCode contests using Go.

Explain:
1. What a subsequence is
2. Difference between subarray, substring, and subsequence
3. How to recognize subsequence problems
4. Clues: keep order but not necessarily continuous
5. Brute force idea first
6. DP or greedy approach depending on problem
7. Step-by-step thought process for Longest Increasing Subsequence
8. Dry run with a small example
9. Pseudocode
10. Go implementation notes
11. Common mistakes
12. Time and space complexity
13. Edge cases

Focus on how to understand the relationship between current element and previous choices.
```

---

### Day 26 — Knapsack-style DP

**Practice problems:**

* Partition Equal Subset Sum
* Coin Change

**Copy-paste daily prompt:**

```text
Teach me Knapsack-style Dynamic Programming for LeetCode contests using Go.

Explain:
1. What knapsack-style DP means
2. How to recognize it
3. Clues: target sum, choose items, subset, minimum coins, possible or not
4. Brute force recursion first
5. State definition using index and target
6. Step-by-step thought process for Partition Equal Subset Sum
7. Dry run with a small example
8. Pseudocode
9. Go implementation using 2D DP and optimized 1D DP
10. Common mistakes with loop direction
11. Time and space complexity
12. Edge cases

Focus on how choosing or skipping an item changes the remaining target.
```

---

### Day 27 — String DP basics

**Practice problems:**

* Longest Common Subsequence
* Edit Distance, optional only

**Copy-paste daily prompt:**

```text
Teach me String Dynamic Programming for LeetCode contests using Go.

Explain:
1. When string problems need DP
2. How to compare two strings using indexes
3. How to recognize string DP
4. Clues: longest common, minimum operations, match characters, transform one string to another
5. Brute force recursion first
6. How dp[i][j] represents smaller string prefixes
7. Step-by-step thought process for Longest Common Subsequence
8. Dry run with small strings
9. Pseudocode
10. Go 2D DP implementation
11. Common mistakes with indexes
12. Time and space complexity
13. Edge cases

Focus on how to define dp[i][j] clearly.
```

---

### Day 28 — Weekly revision day: DP

**Practice:**

* Revisit 2 DP problems from Days 22–27
* Write only state, transition, base case, complexity

**Copy-paste daily prompt:**

```text
Help me revise Dynamic Programming for LeetCode contests using Go.

Topics:
- 1D DP
- Take/not take DP
- Grid DP
- Subsequence DP
- Knapsack-style DP
- String DP

For each topic, explain:
1. How to recognize it
2. How to define the DP state
3. How to find the transition
4. How to set base cases
5. How to dry run
6. Pseudocode
7. Go implementation notes
8. Common mistakes
9. Time and space complexity

Also give me a DP thinking checklist that I can use during contests.
```

---

## Week 5: Contest-heavy patterns

### Day 29 — Linked List basics

**Practice problems:**

* Reverse Linked List
* Linked List Cycle

**Copy-paste daily prompt:**

```text
Teach me Linked List patterns for LeetCode contests using Go.

Explain:
1. What linked lists are
2. How pointers work in linked list problems
3. How to recognize linked list problems
4. Clues: node, next pointer, cycle, reverse, middle
5. Step-by-step thought process for Reverse Linked List
6. Dry run with a small list
7. Pseudocode
8. Go struct and pointer implementation
9. Common mistakes with nil pointers
10. Time and space complexity
11. Edge cases

Focus on pointer movement and how to avoid losing the rest of the list.
```

---

### Day 30 — Fast and Slow Pointers

**Practice problems:**

* Linked List Cycle
* Middle of the Linked List

**Copy-paste daily prompt:**

```text
Teach me Fast and Slow Pointer pattern for LeetCode contests using Go.

Explain:
1. What fast and slow pointers mean
2. Why one pointer moves faster
3. How to recognize this pattern
4. Clues: cycle, middle, repeated movement, linked list
5. Step-by-step thought process for Linked List Cycle
6. Dry run with a small example
7. Pseudocode
8. Go implementation
9. Common mistakes with nil checks
10. Time and space complexity
11. Edge cases

Focus on why fast pointer eventually meets slow pointer in a cycle.
```

---

### Day 31 — Intervals

**Practice problems:**

* Merge Intervals
* Non-overlapping Intervals

**Copy-paste daily prompt:**

```text
Teach me Interval problems for LeetCode contests using Go.

Explain:
1. What interval problems are
2. How sorting helps intervals
3. How to recognize interval problems
4. Clues: start time, end time, meetings, overlapping ranges
5. Brute force comparison first
6. Optimized approach after sorting
7. Step-by-step thought process for Merge Intervals
8. Dry run with easy intervals
9. Pseudocode
10. Go sort.Slice implementation
11. Common mistakes with overlap condition
12. Time and space complexity
13. Edge cases

Focus on how to decide if two intervals overlap.
```

---

### Day 32 — Difference Array / Sweep Line

**Practice problems:**

* Car Pooling
* Corporate Flight Bookings

**Copy-paste daily prompt:**

```text
Teach me Difference Array and Sweep Line for LeetCode contests using Go.

Explain:
1. What difference array means
2. Why it helps with range updates
3. How sweep line works
4. How to recognize these problems
5. Clues: add value to range, bookings, passengers over time, intervals with counts
6. Brute force update each index first
7. Optimized difference array approach
8. Step-by-step thought process for Car Pooling
9. Dry run with an easy example
10. Pseudocode
11. Go implementation
12. Common mistakes with start and end indexes
13. Time and space complexity
14. Edge cases

Focus on how a range update can be represented using only two changes.
```

---

### Day 33 — Bit Manipulation basics

**Practice problems:**

* Single Number
* Counting Bits

**Copy-paste daily prompt:**

```text
Teach me Bit Manipulation basics for LeetCode contests using Go.

Explain:
1. What bits are
2. Common bit operations: AND, OR, XOR, shift
3. How to recognize bit problems
4. Clues: XOR, unique number, power of two, binary, bit count
5. Why XOR works for Single Number
6. Step-by-step thought process for Single Number
7. Dry run with a small example
8. Pseudocode
9. Go bit operation syntax
10. Common mistakes
11. Time and space complexity
12. Edge cases

Focus on intuition, especially why a XOR a = 0 and a XOR 0 = a.
```

---

### Day 34 — Math and modular arithmetic

**Practice problems:**

* Pow(x, n)
* Count Primes, optional

**Copy-paste daily prompt:**

```text
Teach me Math patterns for LeetCode contests using Go.

Explain:
1. Common math patterns in contests
2. How to recognize math problems
3. Clues: modulo, large numbers, powers, divisibility, prime, gcd
4. Brute force idea first
5. Optimized thinking for fast power
6. Step-by-step thought process for Pow(x, n)
7. Dry run with a small example
8. Pseudocode
9. Go implementation notes with int, int64, float64
10. Common mistakes with overflow and negative powers
11. Time and space complexity
12. Edge cases

Focus on how to reduce repeated multiplication using divide and conquer.
```

---

### Day 35 — Weekly revision day

**Practice:**

* Revisit intervals
* Revisit difference array
* Revisit bit manipulation

**Copy-paste daily prompt:**

```text
Help me revise Week 5 LeetCode contest topics in Go.

Topics:
- Linked list
- Fast and slow pointers
- Intervals
- Difference array
- Sweep line
- Bit manipulation
- Math patterns

For each topic, explain:
1. Recognition clues
2. Brute force approach
3. Optimized approach
4. Dry run
5. Pseudocode
6. Go implementation notes
7. Common mistakes
8. Edge cases
9. Time and space complexity

Also give me a contest pattern checklist for these topics.
```

---

## Week 6: Contest simulation and speed building

### Day 36 — Q1 contest speed: simple implementation

**Practice problems:**

* Pick any 2 recent easy contest problems

**Copy-paste daily prompt:**

```text
Train me for LeetCode Contest Q1 problems using Go.

Explain:
1. What Q1 problems usually test
2. How to avoid overthinking easy problems
3. How to read the statement quickly but carefully
4. How to identify direct simulation, counting, sorting, or simple loops
5. How to write clean Go code fast
6. How to test edge cases quickly
7. Step-by-step thought process using one easy contest-style problem
8. Dry run
9. Pseudocode
10. Go code structure
11. Common mistakes that waste time
12. Time and space complexity

Focus on speed with accuracy.
```

---

### Day 37 — Q2 contest pattern recognition

**Practice problems:**

* One medium sliding window/hashmap problem
* One medium binary search/greedy problem

**Copy-paste daily prompt:**

```text
Train me for LeetCode Contest Q2 problems using Go.

Explain:
1. What Q2 problems usually test
2. How to identify the hidden pattern quickly
3. How to compare brute force and optimized approaches
4. How constraints reveal the expected complexity
5. How to choose between hashmap, sorting, sliding window, prefix sum, greedy, or binary search
6. Step-by-step thought process using a medium contest-style problem
7. Dry run
8. Pseudocode
9. Go code structure
10. Common contest mistakes
11. Time and space complexity
12. Edge cases

Focus on recognizing the right pattern, not memorizing solutions.
```

---

### Day 38 — Q3 contest approach: brute force to optimized

**Practice problems:**

* One harder medium problem only

**Copy-paste daily prompt:**

```text
Train me for LeetCode Contest Q3 problems using Go.

Explain:
1. Why Q3 feels harder
2. How to start with brute force without panic
3. How to use constraints to reject brute force
4. How to search for hidden structure
5. How to move from brute force to optimized solution
6. How to identify patterns like DP, greedy, graph, binary search on answer, or heap
7. Step-by-step thought process using one harder medium problem
8. Dry run with a small example
9. Pseudocode
10. Go implementation strategy
11. Common mistakes
12. Time and space complexity
13. Edge cases

Focus on how to think when the solution is not obvious.
```

---

### Day 39 — Debugging in Go

**Practice problems:**

* Re-code 2 previously solved problems without looking

**Copy-paste daily prompt:**

```text
Teach me how to debug LeetCode contest solutions written in Go.

Explain:
1. Common Go mistakes in contests
2. Off-by-one errors
3. Nil pointer errors
4. Slice bounds errors
5. Map default value mistakes
6. Integer overflow and int vs int64 issues
7. Wrong loop direction in DP
8. Incorrect binary search boundaries
9. How to create small test cases
10. How to dry run code manually
11. How to debug without wasting contest time
12. A debugging checklist before submission

Use beginner-friendly language and give Go-specific examples.
```

---

### Day 40 — Complexity analysis and proof

**Practice problems:**

* Analyze 3 old solved problems, no new problem needed

**Copy-paste daily prompt:**

```text
Teach me how to analyze Time and Space Complexity for LeetCode contest problems.

Explain:
1. How to count operations
2. How loops affect time complexity
3. How nested loops affect complexity
4. How sorting affects complexity
5. How maps, heaps, BFS, DFS, and DP affect complexity
6. How to analyze space complexity
7. How to use constraints to check if complexity is acceptable
8. Examples using hashmap, sorting, binary search, BFS, and DP
9. Common mistakes in complexity analysis
10. A simple checklist I can use after solving each problem

Use Go-based examples where helpful.
```

---

### Day 41 — Virtual contest simulation

**Practice:**

* Take one old Weekly or Biweekly contest
* Attempt only first 3 problems
* Spend more time reviewing than solving

**Copy-paste daily prompt:**

```text
Help me simulate and review a LeetCode Weekly or Biweekly Contest using Go.

I attempted the first 3 problems.

Guide me through:
1. How to review each problem
2. How to identify the intended pattern
3. How to compare my approach with the optimal approach
4. How to find where I lost time
5. How to analyze wrong submissions
6. How to write better dry runs
7. How to improve Go implementation speed
8. How to record mistakes in a mistake journal
9. What I should revise before the next contest

Focus on learning from the contest, not just getting accepted.
```

---

### Day 42 — Weekly revision day

**Practice:**

* Review all mistake notes
* Re-code 2 templates from memory

**Copy-paste daily prompt:**

```text
Help me revise my contest simulation week for LeetCode using Go.

Topics:
- Q1 speed
- Q2 pattern recognition
- Q3 brute force to optimized thinking
- Debugging
- Complexity analysis
- Contest review

For each area, explain:
1. What I should improve
2. How to practice it
3. Common mistakes
4. Go-specific tips
5. A checklist for future contests

Also help me create a personal contest strategy for the next Weekly or Biweekly Contest.
```

---

## Final 3 days: Consolidation

### Day 43 — Mixed pattern recognition

**Practice:**

* Pick 5 problem statements
* Do not code immediately
* Only identify pattern + approach first

**Copy-paste daily prompt:**

```text
Train me in mixed pattern recognition for LeetCode contests using Go.

Give me short problem-statement style examples and help me identify whether the pattern is:
- Hash map
- Sorting
- Two pointers
- Sliding window
- Prefix sum
- Binary search
- Greedy
- Stack
- Heap
- BFS/DFS
- DP
- Difference array

For each example, explain:
1. What clues reveal the pattern
2. What brute force would be
3. Why brute force is too slow
4. What optimized idea should come to mind
5. What Go implementation structure I should prepare

Focus on training my observation skill.
```

---

### Day 44 — Full contest simulation

**Practice:**

* Attempt one full old contest
* Time yourself strictly
* Review all problems afterward

**Copy-paste daily prompt:**

```text
Help me review a full LeetCode contest simulation in Go.

For each problem, guide me through:
1. What I understood from the statement
2. What constraints suggested
3. What brute force approach I considered
4. What pattern was actually needed
5. Why the optimized solution works
6. Where I lost time
7. What edge cases I missed
8. What Go implementation mistakes I made
9. Time and space complexity
10. What lesson I should write in my mistake journal

Also help me decide what to do differently in the next live Weekly or Biweekly Contest.
```

---

### Day 45 — Final review and personal playbook

**Practice:**

* No new problems
* Build your personal contest checklist

**Copy-paste daily prompt:**

```text
Help me create my personal LeetCode Weekly and Biweekly Contest Playbook using Go.

Include:
1. My pre-contest checklist
2. My first 10 minutes strategy
3. How to choose which problem to solve first
4. How long to spend before switching
5. How to read constraints
6. How to identify common patterns
7. How to move from brute force to optimized
8. Go templates I should remember
9. Debugging checklist
10. Edge case checklist
11. Time and space complexity checklist
12. Post-contest mistake analysis method
13. A weekly revision routine after these 45 days

Write it in simple language and make it practical for live contests.
```

---

# Weekly revision system

Use every revision day like this:

## Step 1: Pattern recall

For each pattern, answer without looking:

* When do I use this?
* What clues appear in the statement?
* What is the brute force?
* Why is brute force slow?
* What is the optimized idea?
* What is the time complexity?

## Step 2: Re-code templates

Re-code from memory:

* hashmap frequency
* two pointers
* sliding window
* binary search
* BFS queue
* DFS recursion
* heap template
* DP table

## Step 3: Revisit mistakes

For each mistake, write:

```text
Problem:
Pattern:
My wrong thought:
Correct thought:
Constraint clue I missed:
Bug I made:
Edge case I missed:
Lesson:
```

---

# How to analyze mistakes after each contest

After every Weekly or Biweekly Contest, do this:

## 1. Classify the mistake

Use these categories:

| Mistake type            | Meaning                                      |
| ----------------------- | -------------------------------------------- |
| Understanding mistake   | You misunderstood the problem                |
| Pattern mistake         | You did not recognize the right DSA pattern  |
| Constraint mistake      | You ignored input size                       |
| Implementation mistake  | Your idea was correct but code failed        |
| Edge case mistake       | You missed empty/small/duplicate/large cases |
| Time management mistake | You spent too long on one problem            |
| Debugging mistake       | You could not find the bug quickly           |

---

## 2. Ask these questions

For every unsolved or wrong problem:

```text
What was the brute force solution?
Why was it too slow?
What constraint gave the clue?
What pattern was hidden?
What observation unlocks the solution?
What edge case did I miss?
What Go mistake did I make?
How can I recognize this faster next time?
```

---

## 3. Create a mistake journal

Use this format:

```text
Date:
Contest:
Problem:
Difficulty:
Pattern:
My approach:
Correct approach:
Main observation:
Mistake:
Go-specific issue:
Edge case:
Time complexity:
Space complexity:
Lesson:
Review after 7 days:
```

This journal is more valuable than solving 20 random problems.

---

# Go-specific contest tips

## 1. Know these Go tools well

You should be comfortable with:

```go
map[int]int
map[string]int
map[byte]int
sort.Ints(nums)
sort.Slice(arr, func(i, j int) bool { return arr[i][0] < arr[j][0] })
container/heap
slices
2D slices
recursive functions
```

## 2. Avoid common Go mistakes

Watch for:

* using `=` instead of `:=` incorrectly
* forgetting map initialization: `m := make(map[int]int)`
* slice index out of range
* modifying slices accidentally in recursion
* forgetting to copy slice in backtracking
* wrong integer type for large values
* binary search infinite loops
* wrong heap `Less()` logic

## 3. Keep helper functions ready

Practice writing:

```go
func max(a, b int) int
func min(a, b int) int
func abs(x int) int
```

LeetCode Go does not always provide these for integers.

---

# Contest strategy

## First 10 minutes

Read all problems quickly.

For each problem, ask:

```text
Is this direct simulation?
Is this counting?
Is this sorting?
Is this prefix sum?
Is this sliding window?
Is this binary search?
Is this graph?
Is this DP?
```

## Time split

For a 90-minute contest:

|       Time | Action            |
| ---------: | ----------------- |
|   0–10 min | Read all problems |
|  10–25 min | Solve Q1          |
|  25–55 min | Solve Q2          |
|  55–85 min | Attempt Q3        |
| Last 5 min | Test and submit   |

At the beginning, do not worry about Q4. Your first target is to solve **Q1 + Q2 consistently**, then slowly improve Q3.

---

# Final advice

For the next 45 days, your main focus should be:

> Observe constraints → find brute force → detect pattern → optimize → dry run → code cleanly in Go → debug → analyze mistakes.

That cycle will make you much stronger in contests than simply solving many problems randomly.
