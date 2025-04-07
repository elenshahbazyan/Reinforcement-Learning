# Gambler's Problem
This repository contains an implementation of the Gambler's Problem, which is a well-known problem in the field of reinforcement learning. The problem is modeled as a Markov Decision Process (MDP), where the goal is to find an optimal policy for a gambler who has a certain amount of capital and makes bets on a sequence of coin flips. The gambler wins if they reach a goal of 100 dollars and loses if they run out of money.

The problem is solved using Value Iteration, an algorithm for finding the optimal policy by iterating over possible states and updating their value estimates until they converge.

# Problem Description
The gambler has the opportunity to bet on the outcome of a coin flip:

- If the coin comes up heads, the gambler wins as many dollars as they staked.

- If the coin comes up tails, they lose their stake.

The gambler can stake any amount of their current capital, and the goal is to determine the optimal stake in each state of the game to maximize the probability of reaching the goal of 100 dollars.

The state of the game is the gambler’s current capital, and the actions are the stakes, i.e., how much the gambler decides to bet. The problem ends when the gambler either reaches their goal or runs out of money.

# Implementation
## Key Concepts:
States: The states represent the gambler's current capital. The set of states is {0, 1, 2, ..., 100}.

Actions: Actions represent the stakes (the amount of money the gambler decides to bet on each flip).

Policy: A policy maps each capital state to a stake, determining the optimal bet to make at each state.

Value Iteration: This algorithm iteratively updates the value function (probability of winning from each state) until convergence.

# The Objective:
Find the optimal policy (the amount to bet in each state) that maximizes the probability of winning (reaching 100 dollars).

The reward is 0 for most transitions except for when the gambler reaches the goal, in which case the reward is +1.

# Visualization:
The solution to the Gambler's Problem is visualized in the following way:

Value Function: The value function graph represents the probability of winning from each state.

Policy: The final policy graph shows the optimal stake for each state to maximize the probability of winning.

# Files in this Repository:
Gambler's Problem.ipynb: A Jupyter Notebook containing the full implementation of the Gambler’s Problem, including:

- Value Iteration algorithm

- Visualization of the value function and optimal policy

- A plot illustrating the change in value function over successive sweeps of value iteration and the final policy.


