# Reinforcement Learning 
This repository contains a collection of projects that demonstrate various concepts and algorithms in Reinforcement Learning (RL). The focus is on implementing simple and well-known RL algorithms to solve different environments and problems. Below are the projects included in this repository:

# Projects
## Project 1: [Tic-Tac-Toe](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/tic-tac-toe) Game
This project implements the game of Tic-Tac-Toe using Reinforcement Learning techniques. The goal is to train an agent to play the game optimally using algorithms such as Q-learning or Monte Carlo methods. The agent learns through trial and error, updating its strategy based on the game outcomes.

Key features:

- Implementation of the Tic-Tac-Toe game board.

- Reinforcement Learning agent that plays the game and improves over time.

- Training the agent to achieve optimal strategies.

## Project 2: [Multi-Armed Bandit](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/ten-armed-testbed) Problem
The Ten-Armed Testbed is a classic benchmark problem in Reinforcement Learning. In this project, the environment consists of 10 one-armed bandits, each with a different probability distribution. The goal is to maximize the cumulative reward by selecting the optimal actions (arms) over time.

Key features:

- Simulates the 10-armed bandit problem.

- Implements different action-selection strategies such as epsilon-greedy, UCB, and others.

- Tracks the agent's performance and cumulative reward.

## Project 3:[Gridworld MDP](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/gridworld-mdp) (Markov Decision Process)
This project models a simple Gridworld environment using a Markov Decision Process (MDP). The agent moves through a grid, choosing actions that result in different states, aiming to maximize rewards while avoiding penalties.

Key features:

- Gridworld environment setup with different states and rewards.

- Implementing MDP to find the optimal policy using value iteration or policy iteration algorithms.

- Visual representation of the agent's learning process.

## Project 4: [Gridworld DP](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/gridworld-dp) (Dynamic Programming)
The Gridworld DP project extends the MDP-based Gridworld environment by applying Dynamic Programming (DP) techniques to solve the reinforcement learning problem. This project shows how value iteration and policy iteration can be used to compute optimal policies in a known environment.

Key features:

- Gridworld environment for the agent to navigate.

- Application of Dynamic Programming algorithms (value iteration and policy iteration).

- Comparison of the performance of DP techniques in solving the Gridworld problem.

## Project 5: [Gambler's](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/gambler-problem) Problem
This project explores the Gambler’s Problem, a classic example in Reinforcement Learning modeled as a Markov Decision Process (MDP). In this scenario, a gambler places bets on a series of coin flips, with the objective of reaching a capital of 100 dollars without losing everything. The project applies value iteration to determine the optimal strategy that maximizes the probability of reaching the goal.

Key Features:

- State and Action Modeling: Represents the gambler’s capital as the state space and the amount staked as the action space.

- Value Iteration Algorithm: Uses value iteration to compute the optimal value function and derive the best betting strategy.

- Policy and Value Visualization: Plots the optimal policy and value function across different capital levels to illustrate the decision-making process.

This project demonstrates how dynamic programming techniques can solve decision-making problems under uncertainty, and it offers insights into optimal betting behavior in probabilistic environments.

## Project 6: [Black jack](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/blackjack) 
This project tackles the Blackjack Problem, a foundational example in Reinforcement Learning, where the goal is to learn an optimal policy for playing the game of Blackjack through interaction with the environment. 

Key Features:

- Models the Game State: Represents the state space using the player’s current sum, the dealer’s visible card, and whether the player has a usable ace.

- Implements Policy Iteration or Monte Carlo Methods: Uses Monte Carlo control (or optionally Temporal-Difference methods) to estimate action-value functions and improve the policy iteratively.

- Learns an Optimal Policy: Determines the best action (hit or stick) for each possible game state to maximize the player's chances of winning.

- Visualizes Policy and Value Function: Produces 3D surface plots or heatmaps showing the optimal value function and policy for both usable and non-usable ace scenarios.

This project demonstrates how reinforcement learning techniques can be applied to classic games, providing insights into how agents learn optimal decision-making under uncertainty.

## Project 7: [Infinite Variance](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/infinite-variance)
This project investigates the problem of infinite variance in off-policy Monte Carlo estimation using importance sampling. The environment is intentionally simple to isolate and demonstrate the mathematical instability caused by discrepancies between the behavior and target policies. Specifically, it showcases how repeated sampling under a mismatched policy distribution can lead to an exploding variance in value estimates.

Key Features:

- Defines a Clear Policy Mismatch: The target policy always selects the action 'left', while the behavior policy randomly selects between 'left' and 'right' with equal probability.

- Simulates Episodic Trajectories: Simulates complete episodes where rewards are only achieved under specific transitions, leading to highly variable returns.

- Tracks Action Trajectories for Importance Sampling: Records the sequence of actions to compute importance sampling ratios, which are key to estimating expected returns under the target policy.

- Demonstrates Variance Explosion: By accumulating episodes where actions rarely align with the target policy, the code reveals how importance sampling weights can grow exponentially, illustrating the infinite variance problem.

- Foundational for Safe Off-Policy Learning: This simulation highlights the critical need for variance reduction techniques when learning from off-policy data.

- This project serves as a conceptual and practical illustration of why naive off-policy learning with importance sampling can be unstable and why alternative techniques like weighted importance sampling or per-decision corrections are often necessary.

## Project 8: [Random Walk](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/random-walk)
This project explores the Random Walk Problem, a classic example in Reinforcement Learning that demonstrates the differences between prediction algorithms under a fixed policy. The environment consists of five non-terminal states (A–E) and two terminal states at each end. An agent starts in the middle and moves randomly left or right until reaching a terminal state. The project evaluates how well different methods estimate the state values through experience.

Key Features:

- Models a Linear Environment: Represents a symmetric random walk with terminal states and a uniform random policy.

- Implements Value Prediction Algorithms: Uses Temporal-Difference (TD(0)) and Monte Carlo (MC) methods to estimate the value function of each non-terminal state.

- Tracks Learning Performance: Calculates and visualizes Root Mean Squared Error (RMSE) between learned values and true state values over multiple episodes.

- Compares Step-Size Effects: Runs experiments with various learning rates to analyze the convergence and stability of TD and MC methods.

- Includes Batch Learning: Demonstrates how batch updating affects learning performance for both methods in terms of convergence speed and accuracy.

- Visualizes Results: Produces detailed plots showing learning curves, estimated state values at different episodes, and error trends across episodes and learning rates.

This project highlights the key differences in learning dynamics between TD and MC algorithms and illustrates how both perform under online and batch learning scenarios in a simple yet effective environment.

## Project 9: [Windy](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/windy-gridworld) Grid World
This project tackles the Windy Grid World problem, where an agent navigates a grid with wind effects that push it off course. The goal is for the agent to learn the optimal policy to reach the goal state efficiently by considering the wind's impact and the available actions.

Key Features:

- Grid Environment: A 7x10 grid with wind pushing the agent in specific columns. The goal is located in the top-right corner.

- Action-Value Estimation: Uses a 3D tensor to store action-value estimates for each state-action pair.

- Learning Process: The agent interacts with the grid for up to 170 episodes, learning from each experience.

- Time Step Tracking: Tracks the number of time steps taken per episode and plots cumulative time steps across episodes.

- Optimal Policy Visualization: Displays the optimal policy (arrows for up, down, left, right, and goal state marked as 'G') after learning.

- Wind Effects: Considers wind strength in different columns, affecting the agent's movement in the grid.

This project demonstrates how an agent can learn to navigate an environment with dynamic factors like wind and learn an optimal path to the goal using reinforcement learning.

## Project 10: [Cliff Walking](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/cliff-walking)
This project explores the Cliff Walking problem, where an agent navigates a grid from a start state to a goal while avoiding a cliff that results in a large penalty. The agent learns to find the optimal path using SARSA and Q-learning algorithms.

Key Features:

- Grid Environment: A 4x12 grid with a goal at the bottom-right and a cliff at the top.

- Algorithms Implemented: SARSA and Q-learning to learn optimal policies.

- Multiple Runs: 50 independent runs with 500 episodes each to compute average rewards.

- Reward Tracking: Sum of rewards across episodes to evaluate learning progress.

- Policy Visualization: Displays optimal policies for both algorithms.

- Step-Size Comparison: Experiments with different step sizes to analyze performance and convergence.

This project demonstrates how SARSA and Q-learning perform in environments with risky states, focusing on the impact of exploration and step-size parameters on convergence.

## Project 11: [Random Walk NTD](https://github.com/elenshahbazyan/Reinforcement-Learning/tree/main/random-walk-ntd)


# Reference
Sutton R.S., Barto A.G. - [Reinforcement Learning](http://incompleteideas.net/book/the-book.html): An Introduction (2nd edition)
