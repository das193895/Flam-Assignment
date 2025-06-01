# Flam-Assignment

## Question - 1 (N-Queens)

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

Compile and run using: javac Solution.java


