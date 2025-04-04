# Tic-Tac-Toe

- [Introduction](#introduction)
- [Distinctiveness and Complexity](#distinctiveness-and-complexity)
- [How To Run](#how-to-run)

-----------------------------------------------------------------------------
## Introduction

Tic-Tac-Toe or X&O game is a two players board game. The board is devided to 9 empty part like **#** shape. each player (one as **X** and another as **O**) marks in one empty space in their turn by **X** or **O**. The player who succeeds in placing three of their marks in a horizontal, vertical, or diagonal row first is the winner.

-----------------------------------------------------------------------------
## Distinctiveness and Complexity

There are two main files in this project:

- `runner.py` contains all of the code to run the graphical interface for the game.

- `tictactoe.py` contains all of the logic for playing the game, and for making optimal moves. 

    - At first, we define three variables: **X**, **O**, and **EMPTY**, to represent possible moves of the board.
   
    - Each state is represented the board as a list of three lists (representing the three rows of the board), where each internal list contains three values that are either **X**, **O**, or **EMPTY**.
   
    - The function initial_state returns the starting state of the board, which all the values are **EMPTY**.
   
    - **X** gets the first move. Subsequently, the player alternates with each additional move.
  
    - In each state, the `player` function counts the number of **X**s and **O**s to determine who's turn it is. If the count of **X** is more than the count of **O**, it returns **O** (because **X** started the game). Else it returns **X**.
  
    - The `actions` function returns set of all possible actions, available on the board. Using nested for loop, it counts, adds and returns the set of **EMPTY**s.
  
    - The `result` function Returns the board that results from making a move on the board. At first it checks if the action is possible by calling the `actions` function. Then it returns a new board on which the action is marked.
  
    - The `winner` function checkes all the states in which **X** or **O** placed in a horizontal, vertical, or diagonal row. Then returns the winner of the game.
  
    - The `terminal` function returns True if game is over or False otherwise. It calls `winner` function, if `winner` returns one of **X** or **O**, the `terminal` function returns True, otherwise it checks all rows, if there is an **EMPTY**, the `terminal` function returns False, otherwise return True.
  
    - The `utility` function calls the `winner` function and returns the utility of the board. If **X** has won the game, the utility is 1. If **O** has won the game, the utility is -1. If the game has ended in a tie, the utility is 0.
  
    - The `minimax` function implements the **Minimax algorithm with Alpha-Beta pruning** to find the optimal move for the current player. According to the utility scores, if it is **X**'s turn, it calls `maximizer` to maximize the score. If it is **O**'s turn, it calls `minimizer` to minimize the score. Alpha must be the highest value the maximizing player **X** can guarantee and Beta must be the lowest value the minimizing player **O** can guarantee. If at any point Alpha ≥ Beta, it is not the optimal action because it means the opponent will never let us reach that move.
  
    - The `maximizer` function starts on the current board, calls `actions` function and try each action, calls `minimizer` recursively to see how **O** would respond, updates Alpha, the maximum score **X** can force,  If Alpha >= Beta it stops searching further and returns the best move.
  
    - The `minimizer` function starts on the current board, calls `actions` function and try each action, calls `maximizer` recursively to see how **X** would respond, updates Beta, the minimum score **O** can force,  If Alpha >= Beta it stops searching further and returns the best move.

-----------------------------------------------------------------------------
## How To Run

Follow these steps to set up and run the degrees.py:

- Navigate to the project directory: cd /workspaces/Tic-Tac-Toe/tictactoe
- Run `pip3 install -r requirements.txt` to install the required Python package **pygame**
- Run the program: python tictactoe.py
- Play Tic-Tac-Toe against your AI opponent!