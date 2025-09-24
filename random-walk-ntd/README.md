# Random Walk NTD (n-step Temporal Difference)

This repository contains an implementation of the n-step Temporal Difference learning algorithm applied to an extended Random Walk environment. The project demonstrates how n-step methods bridge the gap between Monte Carlo and one-step TD methods, providing a unified framework for value function estimation in reinforcement learning.
The implementation focuses on understanding how different values of n (number of bootstrapping steps) affect learning performance, convergence speed, and estimation accuracy in a well-understood linear environment.

## Problem Description

In the Random Walk NTD problem:

- The agent navigates a linear chain of 19 non-terminal states plus 2 terminal states (21 total states).
- The agent starts in the middle state (state 10) and performs a random walk.
- At each step, the agent moves left or right with equal probability (0.5 each).
- Terminal states provide rewards: -1 for the left terminal state (state 0) and +1 for the right terminal state (state 20).
- All transitions between non-terminal states have zero reward.
- The objective is to accurately estimate the true value function using n-step TD methods.

## Implementation

### Key Concepts:
- **States**: 21 total states (0-20), where states 1-19 are non-terminal and states 0,20 are terminal.
- **Policy**: Fixed random policy with equal probability of moving left or right.
- **Value Function**: True state values are analytically known from the Bellman equation: V(s) = (s-10)/10 for non-terminal states.
- **Discount Factor**: γ = 1.0 (undiscounted episodic task).

### N-step TD Learning:
- **Temporal Difference**: Updates state values using n-step returns that combine observed rewards with bootstrapped estimates.
- **Bootstrapping**: Uses estimated values of states n steps ahead rather than waiting for episode completion.
- **Return Calculation**: Computes n-step returns using the formula: G_t^(n) = R_{t+1} + γR_{t+2} + ... + γ^{n-1}R_{t+n} + γ^n V(S_{t+n}).
- **Value Updates**: Updates occur with a delay of n steps, allowing for more informed estimates than one-step methods.

## Learning Process

- Episodes run from the start state (10) until reaching a terminal state (0 or 20).
- State values are updated using n-step returns with configurable step-size parameters.
- The algorithm tracks complete state sequences and reward trajectories for each episode.
- Updates are performed for states that are n steps in the past, ensuring proper bootstrapping.
- Multiple episodes are run to evaluate convergence and performance across different parameter settings.

## Key Features

- **Configurable n-steps**: Experiment with different values of n to see the effect on learning dynamics.
- **True Value Comparison**: Compare learned estimates against analytically computed true state values.
- **Step-size Analysis**: Evaluate how different learning rates (α) affect convergence and stability.
- **Episode Tracking**: Monitor learning progress through episodic value estimates and error metrics.
- **Performance Metrics**: Calculate Root Mean Squared Error (RMSE) between learned and true values.

## Visualization

The implementation supports various visualizations to analyze learning performance:

- **Value Function Evolution**: Track how state value estimates change over episodes.
- **Learning Curves**: Plot RMSE over episodes for different n values and step sizes.
- **Parameter Sensitivity**: Compare performance across different n-step and α combinations.
- **Convergence Analysis**: Visualize how quickly different methods approach the true value function.

## Theoretical Insights

This implementation demonstrates several key concepts in reinforcement learning:

- **Bias-Variance Trade-off**: Lower n values have higher bias but lower variance, while higher n approaches Monte Carlo with lower bias but higher variance.
- **Computational Efficiency**: n-step methods provide a middle ground between the computational simplicity of TD(0) and the unbiased estimates of Monte Carlo.
- **Bootstrapping Effects**: Shows how using estimated values in updates affects learning speed and accuracy.
- **Parameter Sensitivity**: Illustrates how step-size and n-step parameters interact to influence learning performance.
