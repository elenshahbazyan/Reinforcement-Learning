# Counter Examples

This repository implements Baird's counter example, a carefully designed MDP that demonstrates the divergence of semi-gradient off-policy TD methods with linear function approximation. The project compares various learning algorithms to illustrate fundamental stability issues and their solutions in off-policy reinforcement learning.

## Problem Description

In Baird's Counter Examples:
* Seven-state MDP: six upper states (0-5) and one lower state (6)
* Two actions: dashed (transitions to random upper state) and solid (transitions to lower state)
* All rewards are 0, making true value function V(s) = 0 for all states
* Linear function approximation: V̂(s,w) = w^T · x(s) with 8-dimensional feature vectors
* Behavior policy: selects solid action with probability 1/7, dashed with probability 6/7
* Target policy: always selects solid action (deterministic)
* Discount factor γ = 0.99
* Uniform state distribution under behavior policy (μ(s) = 1/7 for all states)

### Feature Representation:
* **Upper states (0-5)**: x_i(s) = [0,0,...,2,...,0,1] (2 at position i, 1 at last position)
* **Lower state (6)**: x(s) = [0,0,0,0,0,0,1,2] (1 at second-to-last, 2 at last position)

## Implementation

### Key Algorithms:

#### 1. Semi-Gradient Off-Policy TD:
* **Update Rule**: w ← w + α · ρ · δ · ∇V̂(S,w)
* **TD Error**: δ = R + γV̂(S',w) - V̂(S,w)
* **Importance Sampling**: ρ = π(A|S) / b(A|S)
* **Known Issue**: Can diverge under off-policy learning with function approximation

#### 2. Semi-Gradient DP:
* **Synchronous Updates**: Updates all states simultaneously using expected returns
* **Bellman Error**: For each state, computes error from expected next-state values
* **No Sampling**: Uses full model knowledge for exact expectation computation
* **Stability**: More stable than TD but still semi-gradient method

#### 3. TDC (Temporal-Difference with Gradient Correction):
* **True Gradient**: Follows true gradient of Mean Square Projected Bellman Error
* **Two-Timescale**: Maintains primary weights w and auxiliary weights v
* **Update Rules**:
  - w ← w + α · ρ · (δ · x(S) - γ · x(S') · (x(S)^T · v))
  - v ← v + β · ρ · (δ - x(S)^T · v) · x(S)
* **Convergence Guarantee**: Provably converges to TD fixed point

#### 4. Expected TDC:
* **Model-Based**: Uses full knowledge of transition dynamics
* **Expected Updates**: Computes expectations over all possible transitions
* **Faster Convergence**: No sampling variance compared to sample-based TDC

#### 5. Emphatic-TD:
* **Emphasis Mechanism**: Weights updates by emphasis trace M_t
* **Update Rule**: w ← w + α · M_t · ρ_t · δ_t · x(S)
* **Emphasis Update**: M_t = γ · ρ_{t-1} · M_{t-1} + I_t
* **Convergence**: Provably stable under off-policy learning

### Error Metrics:

#### Root Mean Square Value Error (RMS-VE):
* **Definition**: √(Σ_s μ(s)[V̂(s,w) - V_π(s)]²)
* **Interpretation**: Average distance between approximate and true values
* **Weighted**: Uses state distribution μ(s) from behavior policy

#### Root Mean Square Projected Bellman Error (RMS-PBE):
* **Definition**: √(Σ_s μ(s)[Π(Bellman_Error(s))]²)
* **Projection**: Projects Bellman errors onto representable space
* **Optimization Target**: TDC minimizes this objective
* **Fixed Point**: Zero PBE indicates TD fixed point

## Key Features

* **Divergence Demonstration**: Shows semi-gradient TD divergence with concrete example
* **Stability Comparison**: Contrasts unstable and stable off-policy methods
* **Linear Function Approximation**: Uses explicit feature vectors for transparency
* **Multiple Algorithms**: Implements TD, DP, TDC, and emphatic methods
* **Error Tracking**: Computes both RMS-VE and RMS-PBE over learning
* **Expected Updates**: Includes model-based variants for theoretical analysis

## Analysis Capabilities

* **Weight Trajectories**: Track how weights evolve over learning iterations
* **Error Curves**: Plot RMS-VE and RMS-PBE over time for each algorithm
* **Convergence Analysis**: Identify which methods converge and which diverge
* **Importance Sampling Ratios**: Examine ρ values throughout learning
* **Feature Matrix Analysis**: Study representational capacity and projection matrix

## Theoretical Insights

This implementation demonstrates fundamental concepts in off-policy learning:

* **Deadly Triad**: Combination of function approximation, bootstrapping, and off-policy learning can cause divergence
* **Semi-Gradient Limitations**: Semi-gradient methods don't follow true gradient, enabling instability
* **True Gradient Solutions**: TDC and related algorithms achieve stability by following true gradients
* **Emphatic Approach**: Emphasis reweighting provides alternative path to stability
* **Projected Bellman Error**: Understanding PBE as proper optimization objective for off-policy learning
