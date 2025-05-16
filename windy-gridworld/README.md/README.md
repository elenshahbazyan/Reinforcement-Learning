# Windy Grid World
This repository contains an implementation of the Windy Grid World problem, a classic reinforcement learning environment. The environment features a grid-based world with wind that affects the agent’s movement, introducing a layer of complexity to the control problem.

The agent is trained using temporal-difference learning, and an optimal policy is derived from the learned action-value estimates.

## Problem Description
In Windy Grid World:

- The agent starts at a fixed position and aims to reach a defined goal state.

- Each column in the grid may have a wind strength that pushes the agent upward after every action.

- The agent can move in four directions: up, down, left, right.

- The objective is to reach the goal in the fewest number of time steps, despite the wind’s influence.

## Implementation
Key Concepts:
- States: Each grid cell corresponds to a state, represented by its (row, column) coordinates.

- Actions: The agent can choose one of four actions—up, down, left, or right.

- Policy: A policy maps each state to the best action the agent should take to minimize steps to the goal.

- Temporal-Difference Learning: The agent improves its action-value estimates over episodes by learning from interactions with the environment.

### Learning Process:
- The agent initializes with zero action-value estimates.

- Through repeated episodes using the play() function, it updates its estimates based on outcomes.

- An optimal policy is extracted by choosing the highest-valued action in each state.

### Objective
Find the optimal policy—a mapping from each state to the best action—that minimizes the number of steps required to reach the goal state from the starting position, while factoring in the wind dynamics.

### Visualization
Two visualizations are generated as part of the training process:
- Episodes vs. Time Steps Plot
This plot shows how many time steps have been taken cumulatively across episodes, demonstrating how the agent improves its path-finding over time.

## Optimal Policy Grid
After training, a grid displays the best action to take at each state using arrow symbols:

↑ = up

↓ = down

← = left

→ = right

G = goal state

