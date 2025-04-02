# Gridworld as Finite MDP
# Overview
This repository contains an implementation of a Finite Markov Decision Process (MDP) using a simple Gridworld environment. The environment consists of a rectangular grid where each cell represents a state, and the agent can take one of four possible actions: north, south, east, and west. The goal is to explore and understand the optimal policies and value functions for the agent using techniques from reinforcement learning.

The project demonstrates how an agent can solve the MDP using the Bellman equation, computes the state-value functions, and visualizes the corresponding optimal policies for various states in the grid.

# Gridworld Environment
The grid consists of a 5x5 rectangular grid with special states, denoted as A, A', B, and B':

State A: When the agent is in state A, it receives a reward of +10 for all actions and is always moved to A'.

State B: When the agent is in state B, it receives a reward of +5 for all actions and is always moved to B'.

Edge states: When the agent moves outside the grid boundaries, it incurs a penalty of -1, and its state does not change.

Other states: In all other cells, the agent receives a reward of 0, except when moving off the grid.

The agent follows a random policy where all four actions are selected with equal probability (i.e., action probability = 0.25) for each state. The discount factor is set to 0.9.

# Key Concepts
- State-Value Function: The expected return for being in a given state and following a particular policy.

- Optimal Policy: The policy that yields the highest expected return from any given state.

- Bellman Equation: A recursive relationship used to calculate the state-value function for a policy. It expresses the value of a state as the expected sum of the rewards from taking an action and transitioning to the next state.

- Discount Factor: The factor that determines the importance of future rewards compared to immediate rewards.

# Project Breakdown

# State-Value Function Computation
In this part, the state-value function for a random policy is computed using the Bellman equation for a finite MDP.

Objective: Estimate the value of each state under the random policy and visualize the state-value function on the grid.

Visualization: The state-value function is plotted and saved as figure_3_2.png. The figure shows the value function for the gridworld, with negative values near the edges due to the likelihood of hitting grid boundaries.

# Optimal Policies and Value Functions
In this part, the optimal state-value function is computed using the Bellman optimality equation and the optimal policy is determined for the gridworld environment.

Objective: Calculate the optimal value function by solving the Bellman optimality equation and derive the optimal policy.

Visualization: The optimal state-value function is saved as figure_3_5.png, and the optimal policy is visualized and saved as figure_3_5_policy.png. The optimal policy shows arrows indicating the best action to take from each state.

# Results and Analysis
State-Value Function: The state-value function for the random policy shows how the agent's expected reward evolves over time. The negative values near the edges of the grid are due to the higher probability of hitting the grid's boundary.

Optimal Policy: The optimal policy maximizes the agent’s long-term reward by guiding it towards states with higher values (such as A and B).

# Generated Images
figure_3_2.png: A visualization of the state-value function for the random policy.

figure_3_5.png: A visualization of the optimal state-value function.

figure_3_5_policy.png: A visualization of the optimal policy, showing arrows for the best actions in each state.

# Directory Structure

/gridworld_mdp
│
├── src/
│   ├── grid_world.py        # Core gridworld MDP logic
│   └── gridworld_mdp.py     # Script to run the simulations
│
├── book_images/             # Images from the book for reference
│   └── Figure_3_2.PNG       # Example image of the gridworld layout
│
├── generated_images/        # Generated plots
│   ├── figure_3_2.png       # State-value function for random policy
│   ├── figure_3_5.png       # Optimal state-value function
│   └── figure_3_5_policy.png # Optimal policy visualization
│
└── README.md                # This readme file
