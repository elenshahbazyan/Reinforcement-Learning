# Access Control

This repository implements a server access control system where an agent learns to optimally accept or reject customers with different priorities to maximize long-term average reward. The implementation uses differential semi-gradient SARSA, specifically designed for continuing tasks without episode boundaries.

## Problem Description

In the Access Control environment:
* System has 10 servers that can be busy or free at any time
* Customers arrive with four priority levels (0, 1, 2, 3) with corresponding rewards (1, 2, 4, 8)
* Two actions available: reject (0) or accept (1) the customer
* Accepting a customer: occupies one free server and provides reward equal to customer priority
* Rejecting a customer: provides zero reward regardless of priority
* Server dynamics: each busy server becomes free with probability 0.06 per time step
* State space: (number of free servers, customer priority)
* Continuing task: no episode termination, runs indefinitely

## Implementation

### Key Components:

#### 1. State Representation:
* **Free Servers**: Number of currently available servers (0-10)
* **Customer Priority**: Current customer's priority level (0-3)
* **Continuous State Space**: Requires function approximation for tractable learning

#### 2. Action Space:
* **Reject (0)**: Customer is turned away, no server occupied, zero reward
* **Accept (1)**: Customer is served if servers available, one server becomes busy, reward = 2^priority
* **Constraint**: Cannot accept when no free servers available

#### 3. Tile Coding Function Approximation:
* **Hash Table**: IHT with 2048 maximum indices for memory efficiency
* **Feature Scaling**: Normalizes servers and priorities to tile coordinate system
* **Multiple Tilings**: Configurable number of offset tilings for generalization
* **Action Encoding**: Includes action as integer feature for tile selection

#### 4. Value Function:
* **Differential Values**: Estimates relative to average reward (no discounting)
* **Weight Vector**: Maintains tile weights for state-action value approximation
* **Average Reward**: Tracks and updates long-term average reward estimate
* **State Value**: Maximum Q-value over available actions

### Learning Algorithm:

#### Differential Semi-Gradient SARSA:
* **Continuing Task**: Designed for problems without episode boundaries
* **Average Reward**: Maximizes long-term average reward instead of discounted returns
* **Update Rule**: δ = R - R̄ + Q̂(S', A', w) - Q̂(S, A, w)
* **Weight Update**: w ← w + α × δ × ∇Q̂(S, A, w)
* **Average Reward Update**: R̄ ← R̄ + β × δ
* **On-Policy**: Learns and follows ε-greedy policy simultaneously

#### Hyperparameters:
* **α = 0.01**: Step size for value function learning (divided among tilings)
* **β = 0.01**: Step size for average reward learning
* **ε = 0.1**: Exploration probability for ε-greedy policy
* **p = 0.06**: Probability that busy server becomes free per step

## Key Features

* **Continuing Task Framework**: No episode boundaries or terminal states
* **Average Reward Objective**: Maximizes long-term average rather than discounted sum
* **Priority-Based Rewards**: Exponential reward structure (2^priority)
* **Resource Constraints**: Limited servers create accept/reject trade-offs
* **Probabilistic Dynamics**: Stochastic server availability transitions
* **State Distribution Tracking**: Monitors frequency of different server availability levels

## Analysis Capabilities

* **Server Distribution**: Track steady-state distribution of free servers
* **Policy Visualization**: Display learned accept/reject decisions across state space
* **Average Reward Convergence**: Monitor estimated average reward over time
* **Priority Acceptance Rates**: Analyze which priorities are accepted/rejected
* **Value Function Surfaces**: Visualize learned state-action values

## Theoretical Insights

This implementation demonstrates fundamental concepts in continuing tasks:

* **Average Reward Setting**: Alternative to discounted return formulation for continuing problems
* **Differential Values**: State values relative to average reward baseline
* **Resource Allocation**: Learning optimal policies under capacity constraints
* **Priority Queuing**: Balancing high-value customers with server availability
* **Semi-Gradient Methods**: Practical algorithms for function approximation without true gradients
