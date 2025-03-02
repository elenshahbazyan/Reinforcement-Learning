# Multi-Armed Bandit Problem Simulation - Reinforcement Learning
This project simulates the Multi-Armed Bandit (MAB) problem using various epsilon-greedy strategies to explore how different exploration-exploitation balances affect performance. It generates insightful plots that illustrate how the average reward and percentage of optimal actions evolve over time, depending on the epsilon values used in the algorithm.

The Multi-Armed Bandit problem is a classic reinforcement learning task that simulates the challenge of choosing the best action from a set of options with unknown rewards. This project models the problem using an epsilon-greedy algorithm to strike a balance between exploration (trying new actions) and exploitation (choosing the best-known action). By tweaking the epsilon (ε) value, we observe how it influences long-term performance across multiple runs of the bandit problem.

# Features
Simulates multi-armed bandit problems with adjustable epsilon values.
Uses epsilon-greedy strategies to control exploration and exploitation trade-offs.
Supports two types of action-value estimation: Sample-Averages and Constant Step-Size methods.
Plots the average reward and percentage of optimal actions for various epsilon values.
Provides detailed performance analysis through visualizations that compare exploration vs. exploitation.
How It Works
1. Bandit Class:
The core of the project is the Bandit class, which implements the epsilon-greedy algorithm for selecting actions. It maintains action-value estimates, chooses actions based on epsilon, and updates action values based on the received rewards.

2. Simulation:
The simulation runs several independent trials (or episodes) for each epsilon value. It tracks how the reward and optimal action percentages evolve over time and aggregates the results.

3. Plotting:
After running the simulation, we generate high-quality plots that represent the performance over time. These plots include:

Average Reward: Tracks the cumulative reward per time step.
Percentage of Optimal Actions: Shows how often the optimal action was selected.
The results are saved as high-resolution images for further analysis.



