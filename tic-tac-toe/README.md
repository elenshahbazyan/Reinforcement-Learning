# Tic Tac Toe with Reinforcement Learning
This project implements a Tic Tac Toe game where two players (RL players) compete and train against each other. The goal is to train the RL players to play optimally and then compete against each other or a human player.

# Project Structure
The project consists of the following files:

--state.py: Contains functions related to the game state (e.g., generating all possible board configurations).
--judge.py: Defines the Judge class which manages the game logic, such as determining winners and resetting the board.
--player.py: Contains the RLPlayer and HumanPlayer classes. The RLPlayer uses Q-learning to learn the best strategy, and the HumanPlayer allows human input for playing against the AI.

# Installation
Clone the repository:

bash
git clone https://github.com/yourusername/tic_tac_toe.git
cd tic_tac_toe
Ensure you have Python 3.6+ installed. You can check this by running:

python --version
(Optional) Create a virtual environment and activate it:

python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
Install the required dependencies (if any):

pip install -r requirements.txt  # Create this file if you have dependencies
# How to Use
1. Train the RL Players
You can train two RL players using Q-learning. The training involves the players playing against each other for a specified number of epochs. During each epoch, their strategies are updated based on the outcome of the game.

To train the players, run the following command:

python tic_tac_toe.py
This will train the RL players for 100,000 epochs by default.

2. Compete the Trained Players
Once the RL players are trained, you can test how well they compete against each other by running the following function, which will have them compete for a specified number of turns:

compete(turns=1000)
This will allow you to see how well the players perform after training. The win rates will be displayed after every 500 turns.

4. Play Against the RL Player
You can also play against one of the trained RL players. The game will be a 0-sum game, and if both players play optimally, the game will always end in a tie. You can start the game against the RL player by running:
play()
You will take turns entering moves for the human player, and the RL player will respond using its trained policy.

# Code Overview
state.py
get_all_states(): Generates all possible board configurations for a Tic Tac Toe game.
judge.py
Judge: Manages the game logic, determining the winner and resetting the game state.
player.py
RLPlayer: Implements a reinforcement learning agent that learns the optimal strategy using Q-learning.
HumanPlayer: Allows the user to input moves when playing against the RL player
