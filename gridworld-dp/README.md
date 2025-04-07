# Gridworld via Dynamic Programming
# Overview
This project demonstrates the use of Dynamic Programming (DP) methods to solve a gridworld problem, a typical problem in Reinforcement Learning. The gridworld is modeled as a finite Markov Decision Process (MDP), where an agent navigates a grid to reach terminal states while following a policy. This project specifically focuses on implementing Policy Evaluation, Policy Improvement, and Policy Iteration using the gridworld environment.

# Problem Setup
- The environment is represented as a 4x4 grid.

- Each grid cell represents a state in the environment, and the agent can take 4 possible actions: up, down, left, and right.

- Some states are terminal states, meaning the agent cannot move further once it enters them.

- The agent receives a reward of -1 for each non-terminal transition, except when it moves off the grid, where the state remains unchanged.

- The goal is to compute the optimal policy for the agent using dynamic programming methods.
# Key Concepts
## Policy Evaluation (Prediction):

The value function for a given policy is computed iteratively. The value of a state represents the expected reward the agent can obtain by starting at that state and following the given policy.

## Policy Improvement:

Based on the value function from the policy evaluation step, the policy is improved by selecting the action that maximizes the expected return in each state.

## Policy Iteration:

This method combines policy evaluation and policy improvement, iterating until the policy converges to the optimal one. The optimal policy is one that maximizes the expected reward for each state.

# Results and Visualizations
## State-Value Function:

A grid representing the value function of each state, showing the expected reward from starting at that state and following the current policy.

## Optimal Policy:

The final policy, which shows the best action to take from each state to maximize the long-term reward.

## Policy Improvement:

After several iterations of policy evaluation, the policy improves. The progression of these improvements is visualized, showing how the policy becomes optimal.

# Example Output
After running the algorithms, the project will generate:

- State-Value Grid: A visual representation of the value function of the gridworld states, showing the computed values (e.g., the expected reward for each state).

- Optimal Policy Grid: A grid showing the best actions to take from each state (e.g., arrows representing the best actions such as up, down, left, or right).
