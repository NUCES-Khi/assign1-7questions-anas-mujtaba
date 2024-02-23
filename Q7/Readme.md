# Assignment 1: Question 7

| Std ID   | Name           |
|----------|----------------|
| K22-8709 | Mujtaba Junaid |
| K22-4049 | Anas Soharwardy |

## Q7: Hill Search

```python
import random

# Comments have been made to make code understandable
# As the question has not mentioned the initial state, random numbers have been generated.
# Also, as per instructions in class, the question has been solved using hill search and not backtracking.

# Function to generate a random initial state for the N-Queens problem
def initial_state(n):
    return [random.randint(0, n-1) for _ in range(n)]

# Function to count the number of attacks in a given state for the N-Queens problem
def count_attacks(state):
    n = len(state)
    attacks = 0
    for i in range(n):
        for j in range(i + 1, n):
            # Check if queens in the same row or diagonals
            if state[i] == state[j] or abs(state[i] - state[j]) == abs(i - j):
                attacks += 1
    return attacks

# Function to display the chessboard with queens placed according to the given state
def display_chessboard(state):
    n = len(state)
    for row in range(n):
        line = ""
        for col in range(n):
            line += "Q" if state[col] == row else "."
        print(line)
    print()

# Hill climbing algorithm to solve the N-Queens problem
def hill_climbing_n_queens(n, max_steps=1000):
    current_state = initial_state(n)  # Initialize a random state
    current_attacks = count_attacks(current_state)  # Calculate attacks in the initial state

    for step in range(max_steps):
        if current_attacks == 0:
            print("Solution found:")
            display_chessboard(current_state)
            return current_state  # Return the solution if no attacks are present

        neighbors = []
        # Generate neighboring states by moving one queen at a time to a different row
        for col in range(n):
            for row in range(n):
                if current_state[col] != row:
                    neighbor_state = current_state.copy()
                    neighbor_state[col] = row
                    neighbors.append((neighbor_state, count_attacks(neighbor_state)))

        neighbors.sort(key=lambda x: x[1])  # Sort neighbors based on the number of attacks
        best_neighbor, best_attacks = neighbors[0]

        if best_attacks >= current_attacks:
            print("Local maximum reached. Could not find a solution.")
            return None  # Return None if stuck at a local maximum

        current_state, current_attacks = best_neighbor, best_attacks
        print(f"Iteration {step + 1}:")
        display_chessboard(current_state)

    print("Maximum steps reached. Could not find a solution.")
    return None  # Return None if the maximum steps are reached without finding a solution

n_queens_solution = hill_climbing_n_queens(8)
```
Output:

![image](https://github.com/NUCES-Khi/assign1-7questions-anas-mujtaba/assets/160864816/3b3855aa-048f-4697-98f1-474b858f19e3)

## Explanation:
This Python code solves the N-Queens problem using the hill climbing algorithm. The initial_state function generates a random initial state, and count_attacks calculates the number of queen conflicts in a given state. The display_chessboard function visually represents the chessboard with queens placed according to the given state.

The hill_climbing_n_queens function iteratively explores neighboring states by moving one queen at a time to reduce the number of conflicts. It terminates when a solution with zero conflicts is found or when the maximum number of steps (max_steps) is reached. The algorithm prints the intermediate steps and the final solution or notifies if it reaches a local maximum without finding a solution.

The example provided uses the algorithm to solve the 8-Queens problem, and the resulting solution is stored in the variable n_queens_solution.

## different implementation of the code
```python
#Q7(backtracking)
#comments done to make code understandable.
#ALternatively, use backtracking to solve qn.
def is_safe(board, row, col, n):
    # Check if there is a queen in the same column
    for i in range(row):
        if board[i][col] == 1: #baase case
            return False

    # Check if there is a queen in the left diagonal
    for i, j in zip(range(row, -1, -1), range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    # Check if there is a queen in the right diagonal
    for i, j in zip(range(row, -1, -1), range(col, n)):
        if board[i][j] == 1:
            return False

    return True

def solve_n_queens_util(board, row, n):
    if row == n:
        # All queens are placed, print the solution
        for i in range(n):
            for j in range(n):
                print(board[i][j], end=" ")
            print()
        print()
        return

    for col in range(n):
        if is_safe(board, row, col, n):
            # Place queen and move to the next row
            board[row][col] = 1

            # Recur to place queens in the remaining rows
            solve_n_queens_util(board, row + 1, n)

            # Backtrack: If placing queen in the current position doesn't lead to a solution
            board[row][col] = 0

def solve_n_queens(n):
    # Initialize the chessboard with zeros
    board = [[0 for _ in range(n)] for _ in range(n)]

    solve_n_queens_util(board, 0, n)

n = 4
solve_n_queens(n)
```
Output:

![image](https://github.com/NUCES-Khi/assign1-7questions-anas-mujtaba/assets/160864816/58bea826-99b4-4cfb-97f9-6a8118191018)
  
## Explanation:
The provided Python code solves the N-Queens problem using backtracking. The is_safe function checks whether it's safe to place a queen in a given position on the chessboard, considering the columns and diagonals. The solve_n_queens_util function recursively tries to place queens in each row, and if a solution is found, it prints the chessboard configuration. The main function, solve_n_queens, initializes the chessboard and calls the utility function to solve the N-Queens problem for a given board size n (in this case, n = 4). The final output showing before and after output of chess board

