# Mountain Car ET (Eligibility Traces)

This repository implements the Mountain Car problem with eligibility traces, extending the classic continuous control task with SARSA(λ) using multiple trace update mechanisms. The project demonstrates how different eligibility trace types affect learning performance and credit assignment in environments requiring long action sequences.

## Problem Description

In the Mountain Car ET environment:
* Continuous state space: position ∈ [-1.2, 0.5], velocity ∈ [-0.07, 0.07]
* Three discrete actions: reverse (-1), neutral (0), forward (+1)
* Physics dynamics: velocity = velocity + 0.001×action - 0.0025×cos(3×position)
* Starting position: random in [-0.6, -0.4] with zero velocity
* Goal: reach position ≥ 0.5 (right hill peak)
* Reward: -1 on every time step until goal reached
* Episode termination: goal reached or 5000 steps exceeded
* Discount factor: γ = 1.0 (undiscounted)

## Implementation

### SARSA(λ) with Eligibility Traces:

#### Core Algorithm:
* **On-Policy Learning**: Follows and improves ε-greedy policy (ε=0 with optimistic initialization)
* **TD Update**: δ_t = R_{t+1} + γQ̂(S_{t+1},A_{t+1},w) - Q̂(S_t,A_t,w)
* **Weight Update**: w ← w + αδ_t z_t
* **Trace Mechanism**: Multiple update rules controlled by λ parameter

### Eligibility Trace Types:

#### 1. Accumulating Trace:
* **Update Rule**: z_t = γλz_{t-1} + ∇Q̂(S_t,A_t,w)
* **Equation**: z_t = γλz_{t-1} + 1 (for active tiles)
* **Properties**: Accumulates credit for repeatedly visited states
* **Use Case**: Standard eligibility trace for most applications

#### 2. Dutch Trace:
* **Update Rule**: z_t = γλz_{t-1} + (1 - αγλz_{t-1}^T x_t)x_t
* **Coefficient**: 1 - αγλΣ(z[active_tiles])
* **Properties**: Compensates for overlap in tile coding
* **Use Case**: True online TD(λ) for better convergence

#### 3. Replacing Trace:
* **Update Rule**: 
  - z_t[i] = 1 if feature i is active
  - z_t[i] = γλz_{t-1}[i] if feature i is inactive
* **Properties**: Replaces rather than accumulates trace for active features
* **Use Case**: Prevents trace from growing unboundedly

#### 4. Replacing Trace with Clearing:
* **Update Rule**: Same as replacing, but clears traces for non-selected actions
* **Clearing**: Sets z_t[tiles of other actions] = 0
* **Properties**: Only maintains traces for selected action's tiles
* **Use Case**: Action-value methods to prevent interference between actions

### Tile Coding:
* **8 Tilings**: Default configuration for feature representation
* **Hash Table**: IHT with 2048 maximum indices
* **Feature Scaling**: Position and velocity normalized to tile coordinates
* **Action Encoding**: Included as integer feature for action-specific tiles

## Key Features

* **Multiple Trace Types**: Comparative study of four eligibility trace mechanisms
* **Continuous Control**: Demonstrates traces in continuous state spaces
* **Tile Coding**: Efficient function approximation for 2D continuous states
* **Step Limit**: 5000-step cutoff prevents infinite episodes
* **Episode Tracking**: Monitors steps to goal for performance evaluation
* **Cost-to-Go**: Value function visualization across state space

## Analysis Capabilities

* **Trace Comparison**: Evaluate learning speed across different trace types
* **λ Parameter Study**: Analyze impact of trace-decay parameter on performance
* **Convergence Speed**: Measure episodes and steps needed to learn
* **Episode Length Curves**: Track learning progress over episodes
* **Value Function Visualization**: Display learned cost-to-go surfaces

## Theoretical Insights

This implementation demonstrates fundamental concepts in eligibility traces for control:

* **Credit Assignment**: How traces distribute credit to earlier state-action pairs
* **Trace Types**: Differences between accumulating, dutch, replacing mechanisms
* **Action Interference**: Why clearing traces prevents cross-action contamination
* **λ Trade-off**: Balance between fast learning (high λ) and stability (low λ)
* **Continuous Control**: Eligibility traces' effectiveness in long action sequences
* **Tile Coding Interaction**: How dutch traces compensate for feature overlap
