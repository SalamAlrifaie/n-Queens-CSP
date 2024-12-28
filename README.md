# n-Queens-CSP
**General Description:**
*An implementation of the MIN-CONFLICTS heuristic to solve a CSP representation of the n-Queens problem, for up to n = 100,000 Queens.
The n-Queens problem can be represented as a Constraint Satisfaction Problem (CSP) where the objective is to place NxN queens on an NxN chessboard such that no two queens can attack each other.*

## Approach
### Variables- 
Each row on the NxN chessboard represents a variable, and the column position of a queen on that row is the value that the variable can be assigned. For an NxN chessboard, there are N variables X1 - XN where each variable Xi corresponds to the queen’s column in row i.

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

## Error Handling
The error handling of the code is done in the Main function via a for-loop statement. It ensures that invalid inputs or unsolvable cases for the N-queens problem are managed easily and provides feedback to the user. It covers several scenarios to prevent runtime errors and any invalid input:

1. Non-integer Input: ValueError is raised if the user provides a value for N that isn’t an integer. The program catches the error and prints a statement to the user to enter a valid value, preventing the program from crashing.

2. Non-positive Integer Values: The program identifies any zero or negative integer, displaying an error message while prompting the user to input a positive number since it exits early. This guarantees that only acceptable chessboard sizes are handled, as a chessboard with zero or negative dimensions is insignificant.

3. Unsolvable board size: Certain chess board sizes, specifically N=2 and N=3, have no solution to the n-Queens problem due to the board's small size that won’t satisfy the problem constraints. For these cases, the program outputs a message informing the user that this problem doesn’t have any solution.

4. Failure to Solve: Even with valid inputs, there is a chance that the algorithm may not solve the problem due to an unanticipated issue. To handle this, the program uses the is_valid function to verify if the solution found by the min_conflict algorithm satisfies all constraints. If it does not, the program outputs: "N-Queens not solved." and exits, ensuring the user is informed about the failure without proceeding with invalid results.

**For general cases with valid inputs and solvable board sizes:** The program executes the MIN-CONFLICTS algorithm and provides detailed feedback to the user. This includes a start notification indicating that the algorithm has begun, details of the solution process such as the number of steps taken, and the time required to find a solution for the given N value. It also visualizes the solution using a scatter plot and confirms that the solution has been saved to a text file, as discussed earlier in the document.

## Installation and Execution
To install and run this code, you simply need the term_project.py file downloaded in your files. Then, open a command terminal and run the following command:
*python <filepath_to_termproject.py> <N as int>*

N should be an integer representing the size of the puzzle. For best results, fill in the file path by right-clicking term_project.py and clicking “Copy as Path”. 

## Output
The scatter plot visualizes the N-queens problem for the given N. Each red dot represents a queen's position on the chessboard, where the x-axis corresponds to the column and the y-axis to the row. You can hover over a red dot which will reveal the exact row and column of the queen, showing their exact positions and ensuring no two queens threaten each other.

### Example output for N = 10
Starting MIN-CONFLICTS algorithm...
Initial number of conflicts: 34
Final number of conflicts: 0
N-Queens solved for N = 10 in 58 steps.
Time taken = 0.0005 => 0 minutes and 0.001 seconds
Solution saved to nqueens_solution_10.txt

Text file:

![Screenshot 2024-12-28 165052](https://github.com/user-attachments/assets/b99167d1-2295-4c8e-a5f7-1ebb6b37fe73)

Scatterplot:
![Figure_1](https://github.com/user-attachments/assets/28d62d81-13cf-492d-b579-a832b2e052cd)

Scatterplot for large N:
![100000queens](https://github.com/user-attachments/assets/0107b2b9-f9bc-4f20-bd86-c6f2435270a4)

## Solving Time Graphical Representation
The code in time1.py is for generating the time taken to solve each n-queens problem.
![Screenshot 2024-12-28 165657](https://github.com/user-attachments/assets/19151193-163f-4bd0-ac26-1077c48c7f42)


