# Random Walk
This repository contains an implementation of the Random Walk problem, a fundamental reinforcement learning example that illustrates the differences between Temporal-Difference (TD) learning and Monte Carlo (MC) methods for value prediction. The environment is a simple 1D random walk with five non-terminal states, used to study the learning dynamics of value estimation algorithms.

The agent is trained using both TD(0) and Monte Carlo, with comparisons made under both incremental and batch updating conditions.

## Problem Description
In Random Walk:

- The environment consists of seven states: A to G, where A and G are terminal.

- The agent starts at the center (state D) and moves left or right randomly until it reaches a terminal state.

- The reward is 0 for all transitions, except reaching state G, which gives a reward of 1.

- The true value of each non-terminal state is known and used for evaluating learning performance.

### Implementation
Key Concepts:
- States: Represented as a 1D array of 7 positions: A to G. Non-terminal states are B to F.

- Actions: At each state, the agent randomly moves left or right.

- Value Function: The function being learned, which estimates the expected return from each state under the current policy.

- True Values: The theoretical values used to compute RMSE between estimated and actual values.

- TD(0) & MC: Two different learning algorithms used for value prediction.

### Learning Process
1. Incremental Updates
TD(0) and Monte Carlo methods are applied episode-by-episode.

RMSE is tracked after each episode to evaluate learning accuracy.

Multiple runs are averaged to produce smooth curves.

2. Batch Updates
After each episode, all collected episodes are used as a batch.

Updates are repeated until values converge.

TD shows better performance than MC in terms of RMSE.

### Visualization
- Generated plots are saved in the generated_images/ folder:

- example_6_2.png: Shows value estimates after 0, 1, 10, and 100 episodes, and compares TD vs. MC using different step sizes.

- figure_6_2.png: Compares batch TD and MC in terms of RMSE over episodes.
