# Blackjack 
## Overview
This repository contains an implementation of the Blackjack environment from reinforcement learning. The goal of the project is to apply Monte Carlo methods for policy evaluation, Monte Carlo Exploring Starts for control, and Off-policy Prediction via Importance Sampling to optimize an agent's performance in a game of Blackjack. This project includes both policy evaluation and control to help the agent learn optimal decision-making strategies for the game.

### Problem Description
In Blackjack, the agent must make decisions based on its current state and a policy to maximize the expected return.

### Environment Details:
- States: The state of the game is represented by:

- The sum of the player's cards.

- The dealer’s visible card.

- Whether the player has a usable ace.

- Actions: The player has two possible actions:

- Hit: Draw another card.

- Stick: Keep the current cards and end the turn.

### Rewards:
+1 for winning a round.

0 for a draw.

-1 for losing a round.

The objective is for the agent to learn an optimal policy, maximizing the long-term expected reward.

Key Concepts
- Monte Carlo Prediction: The Monte Carlo method is used for estimating the value of a policy by averaging the returns from multiple episodes.

- Monte Carlo Exploring Starts (MC ES): A control method that starts each episode from a random state-action pair, ensuring exploration of all actions in all states.

- Off-policy Prediction via Importance Sampling: Estimating the value of a target policy using data generated from a behavior policy. This method helps the agent learn off-policy.

### Key Methods Implemented:
- Monte Carlo On-policy: Evaluates the policy by averaging the return for each state-action pair.

- Monte Carlo ES: Uses exploring starts to improve the learning process, ensuring that all actions are visited in all states.

- Off-policy Importance Sampling: Uses importance sampling techniques to evaluate the value of a state under a target policy using data from a behavior policy.

### Learning Process
- The agent's performance is evaluated using Monte Carlo methods with different configurations:

- Monte Carlo On-policy: The agent learns by following a specific policy.

- Monte Carlo Exploring Starts: The agent explores all possible actions and learns an optimal policy based on its experiences.

- Off-policy Importance Sampling: The agent estimates the value of a target policy using data generated from a different policy.

### Key Metrics:
- State-action values: The expected return for taking a specific action in a particular state.

- State values: The maximum value over all possible actions for each state.

### Visualization
Generated plots are saved in the generated_images/ folder:

- figure_5_1.png: Heatmaps showing state-action values for "Usable Ace" and "No Usable Ace" after different numbers of episodes.

- figure_5_2.png: The optimal policy and state-value function for Blackjack found by MC ES.

- figure_5_3.png: A comparison of ordinary and weighted importance sampling, showing the squared error of value estimates.

