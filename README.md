# Proximity-Game
The goal of this project is to implement a player for the Proximity game. The player receives a number and the current state of the game board at each turn, evaluates the available empty positions, and intelligently selects the optimal position to place the given number.


Proximity Game Player

Description
  This project implements an intelligent player for the Proximity board game. 
  At each turn, the player:
  - Receives a number
  - Analyzes the current state of the board
  - Evaluates all available positions
  - Selects the optimal move based on a scoring strategy
  - Places the number in the chosen cell

  The goal is to maximize the player’s score by making strategic decisions based on neighboring cells.

How It Works
  The player uses a heuristic scoring algorithm:
  - It examines all possible empty cells near already occupied ones
  - For each candidate cell, it calculates a score
  - The score depends on:
  - Friendly neighboring cells (+1 each)
  - Opponent cells with smaller values (adds their value)
  - The position with the highest score is selected

If the board is empty (start of the game), the player chooses a central position.

Project Structure
  Cell Class
    Represents each cell of the board:
    - value: the number placed in the cell
    - owner: the player who owns the cell
    - 0 → empty
    - 1 → player 1
    - 2 → player 2
  
  Proximity2 Class
    Implements the player logic:
    - Main Methods
    - placeTile(number, board)
    - Chooses the best position for the given number
    - applyChanges(number, board)
    - Places the number and updates neighboring cells
    - findNeighbours(board)
    - Finds candidate positions near occupied cells
    - findMyNeighbours(cell)
    - Returns neighbors of a specific cell

Game Logic
  After placing a number:
  - Adjacent friendly cells increase their value by +1
  - Adjacent enemy cells:
  - Are captured if their value is smaller than the placed number
  - Otherwise remain unchanged

Example Usage
  from Proximity2_Player import Proximity2, Cell

  # Create empty board (8x6)
  board = [Cell() for _ in range(48)]
  
  # Create player
  player = Proximity2(pid=2, length_X=8, length_Y=6)
  
  # Place number
  board = player.applyChanges(20, board)

print(board)

Team
  Pelagia Kourti
  Panagiotis Spartalis
  Panagiota Christodoulidou

Notes
- The implementation uses a 1D list to represent the board
- Neighbor calculations handle edge and corner cases explicitly
- The algorithm prioritizes local optimal decisions

Future Improvements
- Implement Minimax or more advanced AI strategies
- Add visualization (GUI or web interface)
- Optimize performance for larger boards
