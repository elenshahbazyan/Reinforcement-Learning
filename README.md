# Reinforcement Learning 
This repository contains a collection of projects that demonstrate various concepts and algorithms in Reinforcement Learning (RL). The focus is on implementing simple and well-known RL algorithms to solve different environments and problems. Below are the projects included in this repository:

# Projects
## Project 1: [Tic-Tac-Toe](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/tic-tac-toe) Game
This project implements the game of Tic-Tac-Toe using Reinforcement Learning techniques. The goal is to train an agent to play the game optimally using algorithms such as Q-learning or Monte Carlo methods. The agent learns through trial and error, updating its strategy based on the game outcomes.

Key features:

-Implementation of the Tic-Tac-Toe game board.

-Reinforcement Learning agent that plays the game and improves over time.

-Training the agent to achieve optimal strategies.

## Project 2: [Multi-Armed Bandit](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/ten-armed-testbed) Problem
The Ten-Armed Testbed is a classic benchmark problem in Reinforcement Learning. In this project, the environment consists of 10 one-armed bandits, each with a different probability distribution. The goal is to maximize the cumulative reward by selecting the optimal actions (arms) over time.

Key features:

-Simulates the 10-armed bandit problem.

-Implements different action-selection strategies such as epsilon-greedy, UCB, and others.

-Tracks the agent's performance and cumulative reward.

## Project 3:[Gridworld MDP](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/gridworld-mdp) (Markov Decision Process)
This project models a simple Gridworld environment using a Markov Decision Process (MDP). The agent moves through a grid, choosing actions that result in different states, aiming to maximize rewards while avoiding penalties.

Key features:

-Gridworld environment setup with different states and rewards.

-Implementing MDP to find the optimal policy using value iteration or policy iteration algorithms.

-Visual representation of the agent's learning process.

## Project 4: [Gridworld DP](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/gridworld-dp) (Dynamic Programming)
The Gridworld DP project extends the MDP-based Gridworld environment by applying Dynamic Programming (DP) techniques to solve the reinforcement learning problem. This project shows how value iteration and policy iteration can be used to compute optimal policies in a known environment.

Key features:

-Gridworld environment for the agent to navigate.

-Application of Dynamic Programming algorithms (value iteration and policy iteration).

-Comparison of the performance of DP techniques in solving the Gridworld problem.

## Project 5: [Gambler's](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/gambler-problem) Problem
This project explores the Gambler’s Problem, a classic example in Reinforcement Learning modeled as a Markov Decision Process (MDP). In this scenario, a gambler places bets on a series of coin flips, with the objective of reaching a capital of 100 dollars without losing everything. The project applies value iteration to determine the optimal strategy that maximizes the probability of reaching the goal.

Key Features:

State and Action Modeling: Represents the gambler’s capital as the state space and the amount staked as the action space.

Value Iteration Algorithm: Uses value iteration to compute the optimal value function and derive the best betting strategy.

Policy and Value Visualization: Plots the optimal policy and value function across different capital levels to illustrate the decision-making process.

This project demonstrates how dynamic programming techniques can solve decision-making problems under uncertainty, and it offers insights into optimal betting behavior in probabilistic environments.

## Project 5: [Black jack](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/blackjack) 
This project tackles the Blackjack Problem, a foundational example in Reinforcement Learning, where the goal is to learn an optimal policy for playing the game of Blackjack through interaction with the environment. 

Key Features:

- Models the Game State: Represents the state space using the player’s current sum, the dealer’s visible card, and whether the player has a usable ace.

- Implements Policy Iteration or Monte Carlo Methods: Uses Monte Carlo control (or optionally Temporal-Difference methods) to estimate action-value functions and improve the policy iteratively.

- Learns an Optimal Policy: Determines the best action (hit or stick) for each possible game state to maximize the player's chances of winning.

- Visualizes Policy and Value Function: Produces 3D surface plots or heatmaps showing the optimal value function and policy for both usable and non-usable ace scenarios.

This project demonstrates how reinforcement learning techniques can be applied to classic games, providing insights into how agents learn optimal decision-making under uncertainty.

## Project 6: [Infinite Variance](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/infinite-variance)
This project investigates the problem of infinite variance in off-policy Monte Carlo estimation using importance sampling. The environment is intentionally simple to isolate and demonstrate the mathematical instability caused by discrepancies between the behavior and target policies. Specifically, it showcases how repeated sampling under a mismatched policy distribution can lead to an exploding variance in value estimates.

Key Features:

- Defines a Clear Policy Mismatch: The target policy always selects the action 'left', while the behavior policy randomly selects between 'left' and 'right' with equal probability.

- Simulates Episodic Trajectories: Simulates complete episodes where rewards are only achieved under specific transitions, leading to highly variable returns.

- Tracks Action Trajectories for Importance Sampling: Records the sequence of actions to compute importance sampling ratios, which are key to estimating expected returns under the target policy.

- Demonstrates Variance Explosion: By accumulating episodes where actions rarely align with the target policy, the code reveals how importance sampling weights can grow exponentially, illustrating the infinite variance problem.

- Foundational for Safe Off-Policy Learning: This simulation highlights the critical need for variance reduction techniques when learning from off-policy data.

- This project serves as a conceptual and practical illustration of why naive off-policy learning with importance sampling can be unstable and why alternative techniques like weighted importance sampling or per-decision corrections are often necessary.


# Reference
Sutton R.S., Barto A.G. - Reinforcement Learning: An Introduction (2nd edition) https://archive.org/details/rlbook2018/mode/2up
