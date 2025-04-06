# Ten-Armed Bandit Testbed
# Overview
This repository provides an implementation and exploration of the Multi-Armed Bandit (MAB) problem, as introduced in Reinforcement Learning: An Introduction by Sutton and Barto. The MAB problem is a classic example of a reinforcement learning scenario where an agent needs to explore and exploit actions to maximize its cumulative reward over time.

The testbed features a 10-armed bandit problem, allowing for the evaluation of several strategies that balance exploration and exploitation. The project simulates and compares different algorithms such as ε-greedy, UCB, and Gradient Bandit Algorithms.

# Multi-Armed Bandit Problem
In this problem, an agent selects from a set of available actions, each with a different and unknown probability distribution for rewards. The agent’s goal is to choose actions that maximize the total cumulative reward, navigating the trade-off between exploration (testing actions to learn more about their rewards) and exploitation (selecting actions that are known to give high rewards).

# Key Concepts
- k-Armed Bandits
The bandit consists of k different actions (arms), each associated with a reward distribution that is unknown to the agent.

- Exploration vs. Exploitation
The agent must decide whether to select the action that appears to give the best reward (exploitation) or try other actions to learn more about their rewards (exploration).

- Action-Value Methods
Techniques for estimating the expected reward of each action to guide the agent’s decision-making process.

# Project Breakdown
This project consists of five primary sections, each examining different aspects of the Ten-Armed Bandit problem.

# Reward Distribution
Simulates and visualizes the reward distribution of a 10-armed bandit.

Objective: Understand the variability in rewards across different arms.

Visualization: A violin plot (Figure 2.1) is generated to illustrate the variation in rewards for each action.

## Greedy vs. ε-Greedy Action Selection
Compares the performance of Greedy action selection with ε-greedy methods for different values of ε (ε = 0, 0.1, 0.01).

Objective: Evaluate how different ε-greedy strategies balance exploration and exploitation.

Visualization: Plots (Figure 2.2) show the effect of varying ε on average rewards and the percentage of optimal actions selected.

## Optimistic Initial Values vs. Realistic Initial Values
Compares two bandit scenarios: one with optimistic initial values (Q1 = 5) and one with realistic initial values (Q1 = 0).

Objective: Investigate how optimism in initial action-value estimates impacts early exploration.

Visualization: Plots (Figure 2.3) illustrate the impact of optimistic versus realistic initial values on the agent’s performance.

## Upper-Confidence-Bound (UCB) Action Selection
Evaluates the UCB strategy (with confidence level c = 2) against the ε-greedy strategy (ε = 0.1).

Objective: Examine how UCB balances exploration and exploitation by using confidence intervals to prioritize uncertain actions.

Visualization: Plots (Figure 2.4) demonstrate how each algorithm performs in terms of average reward over time.

## Gradient Bandit Algorithms (GBA)
Explores the Gradient Bandit Algorithm (GBA) with and without a baseline for different step sizes (α = 0.1, 0.4).

Objective: Study how the gradient approach dynamically adjusts action preferences over time based on received rewards.

Visualization: Plots (Figure 2.5) show how different step sizes and baseline settings affect the agent’s performance.

# Results and Analysis
The experiments conducted in this project compare different strategies based on the following metrics:

Cumulative Reward: Measures the total reward accumulated by the agent over time for each strategy.

Optimal Action Selection Percentage: Analyzes the proportion of times the agent selects the optimal action over time.

These results are visualized in various plots and are used to compare how different strategies address the exploration-exploitation trade-off.

# Output
After running the simulation, the following plots will be saved:

figure_2_1.png: Reward distribution for different arms.

figure_2_2.png: Comparison of ε-greedy action selection with varying ε values.

figure_2_3.png: Impact of optimistic vs. realistic initial values.

figure_2_4.png: Comparison of UCB vs ε-greedy.

figure_2_5.png: Performance of Gradient Bandit Algorithms (GBA) with different step sizes.
