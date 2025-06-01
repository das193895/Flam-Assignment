# Flam-Assignment

## 🔄 Question - 1 : N-Queens

🧩 The Problem Statement:

The N-Queens puzzle is the problem of placing n queens on an n x n chessboard such that no two queens attack each other. A queen can attack any number of squares vertically, horizontally, or diagonally.

Given: An integer n
Return: All distinct solutions to the N-Queens puzzle. You may return the answer in any order.

Each solution contains a distinct board configuration where 'Q' indicates a queen and '.' indicates an empty space.

🔢 Examples:

Input: n = 4

Output: 
[
 [".Q..",
  "...Q",
  "Q...",
  "..Q."],

 ["..Q.",
  "Q...",
  "...Q",
  ".Q.."]
]


Input: n = 1

Output: [["Q"]]


✅ Constraints
1 <= n <= 9

💡 Approach
-> This solution uses backtracking to try placing queens one column at a time. It:

-> Checks whether the current position is safe using row, column, and diagonal checks.

-> If it’s safe, places a queen and moves to the next column.

-> If a full board is valid, it stores the board as one valid solution.

-> After exploring, it backtracks (removes the queen) to explore other possibilities.


🧪 How to Run
Make sure you have Java installed.

Save the code in a file named Solution.java.

Compile and run using:
 ```bash 
 javac Solution.java 
 ```

## 🔄 Question 2: Detect Circular Dependency in Module Loader
Problem Statement
You are building a module loader for a large software system. Each module may depend on one or more other modules. Before loading, you must ensure that there are no circular dependencies, as they would lead to infinite loading loops.

Function Signature: bool hasCircularDependency(int n, vector<vector<int>>& edges);

📥 Input
n: Number of modules, labeled from 0 to n - 1

edges: List of dependency pairs where edges[i] = {a, b} means module a depends on module b

📤 Output
true if a circular dependency exists

false otherwise

🧠 Constraints
1 ≤ n ≤ 10⁴

0 ≤ edges.length ≤ 10⁵

Dependencies form a directed graph

Self-dependencies like {a, a} are valid and considered cycles

The graph may have disconnected components

🔁 Examples

Input:
n = 4
edges = {{0, 1}, {1, 2}, {2, 3}}

Output:
false


Input:
n = 4
edges = {{0, 1}, {1, 2}, {2, 0}}

Output:
true


💡 Approach
The graph is constructed using an adjacency list, reversing the dependency direction so b → a if a depends on b.

A topological sort is performed using Kahn’s Algorithm, which tracks nodes with 0 in-degree.

If at the end of sorting, not all nodes are processed (topoSort.size() < n), a cycle exists.

Also, self-dependencies (e.g., {a, a}) are checked immediately and flagged as cycles.

🧪 How to Run
Save the Java code as Main.java

Compile and run:

```bash
javac Main.java
java Main
```



