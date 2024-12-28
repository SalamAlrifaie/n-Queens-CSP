# n-Queens-CSP
**General Description:**
*An implementation of the MIN-CONFLICTS heuristic to solve a CSP representation of the n-Queens problem, for up to n = 100,000 Queens.
The n-Queens problem can be represented as a Constraint Satisfaction Problem (CSP) where the objective is to place NxN queens on an NxN chessboard such that no two queens can attack each other.*

## Approach
### Variables- 
Each row on the NN chessboard represents a variable, and the column position of a queen on that row is the value that the variable can be assigned. For an NxN chessboard, there are N variables X1 - XN where each variable Xi corresponds to the queen’s column in the row i.

### Domains- 
The domain of each variable Xi is the set of possible positions for a queen on her row, that is, the set of column indices {1, 2, …,  N}.

### Constraints- 
The constraints of the CSP n-queens problem ensure that no two queens are attacking each other, meaning, no two queens exist in the same row, column, or diagonally.

Row constraints: satisfied inherently since every queen is placed in her own row (each variable represents a different row).
Column constraints- for any two variables Xi and Xj, Xi   Xj
Diagonal constraints- For any two variables Xi and Xj, the following must hold:
	|Xi-Xj|  | i-j |

There are two types of diagonals:
Major Diagonals: Diagonal from top-left to bottom-right
Minor Diagonals: Diagonal from top-right to bottom-left

### Goal State- 
A solution to the n-queens CSP is an assignment of column indices to all queens on the board (N variables X1 - XN) such that all constraints are satisfied—no pair of queens are threatening each other.

## The MIN-CONFLICTS Heuristic
The Min-Conflicts heuristic selects the next value for a variable in a local search algorithm based on the number of violated constraints. Min-conflicts heuristic selects the value that results in the fewest constraints violated. In the context of the n-queens problem, the Min-Conflicts algorithm chooses the queen position on the board such that the fewest queens attack each other. Similar to hill‐climbing, for min-conflict h(n) = total number of violated constraints.


The min-conflict function uses a for loop to check if the current configuration of queens is a valid solution.
