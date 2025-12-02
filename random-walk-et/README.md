# Random Walk ET (Eligibility Traces)

This repository explores eligibility traces through implementations of three λ-based algorithms applied to the 19-state random walk environment. The project demonstrates how the trace-decay parameter λ controls the trade-off between Monte Carlo and temporal difference learning, creating a spectrum of algorithms with different convergence properties.

## Problem Description

In the Random Walk ET environment:
* Linear chain of 19 non-terminal states with terminal states at each end
* Agent starts from the central state (state 10) and moves randomly
* Actions: move left (-1) or right (+1) with equal probability (0.5 each)
* Terminal rewards: -1 for reaching left boundary (state 0), +1 for right boundary (state 20)
* All non-terminal transitions have zero reward
* True state values known analytically: V(s) = (s-10)/10 for states 1-19
* Goal: learn accurate value function using eligibility traces with various λ values

## Implementation

### Eligibility Trace Algorithms:

#### 1. Off-line λ-return:
* **Learning Mode**: Updates occur at episode end using complete trajectory
* **λ-return Calculation**: G_t^λ = (1-λ) Σ_n λ^(n-1) G_{t:t+n} + λ^(T-t-1) G_t
* **Combines n-step Returns**: Weights different-length returns by powers of λ
* **Update Rule**: w ← w + α[G_t^λ - V̂(S_t,w)]∇V̂(S_t,w)
* **Truncation**: Stops summing when λ^n < 10^-3 for computational efficiency

#### 2. TD(λ) with Accumulating Traces:
* **Online Learning**: Updates occur at every time step within episodes
* **Accumulating Trace**: z_t = γλz_{t-1} + ∇V̂(S_t,w)
* **TD Error**: δ_t = R_{t+1} + V̂(S_{t+1},w) - V̂(S_t,w)
* **Update Rule**: w ← w + αδ_t z_t
* **Memory**: Eligibility vector tracks credit assignment across states
* **Special Cases**: λ=0 gives TD(0), λ=1 approaches Monte Carlo

#### 3. True Online TD(λ) with Dutch Traces:
* **Online λ-return**: Approximates exact online λ-return algorithm
* **Dutch Trace**: z_t = γλz_{t-1} + (1 - αγλz_{t-1}^T x_t)x_t
* **Enhanced Update**: w ← w + α[δ_t + V̂(S_t,w) - V̂_old]z_t - α[V̂(S_t,w) - V̂_old]x_t
* **Correction Term**: Additional update for improved online performance
* **Better Convergence**: More accurate than standard TD(λ)

### Function Approximation:
* **State Aggregation**: Simplest linear approximation with one weight per state
* **Feature Vector**: Binary features where x_i(s) = 1 if s=i, else 0
* **Weight Vector**: w with 21 elements (19 states + 2 terminals)
* **Value Estimate**: V̂(s,w) = w_s (weight equals state value directly)

## Key Features

* **Three Algorithms**: Comparative study of off-line λ-return, TD(λ), and true online TD(λ)
* **Parameter Sweep**: Systematic analysis across λ ∈ [0,1] and various α values
* **True Values**: Known ground truth enables accurate error measurement
* **RMS Error Tracking**: Computes root mean square error against true values
* **Episode-Based Analysis**: Evaluates performance over first 10 episodes
* **Multiple Runs**: Averages results over many independent runs for statistical reliability

## Analysis Capabilities

* **λ Parameter Study**: Compare performance across different trace-decay values
* **Step Size Sensitivity**: Analyze impact of learning rate on convergence
* **Algorithm Comparison**: Contrast off-line, standard TD(λ), and true online approaches
* **Error Curves**: Plot RMS error versus step size for different λ values
* **Convergence Speed**: Measure episodes needed to reach low error
* **Stability Analysis**: Identify stable step size ranges for each algorithm

## Theoretical Insights

This implementation demonstrates fundamental concepts in eligibility traces:

* **λ Spectrum**: How λ=0 gives pure TD, λ=1 gives Monte Carlo, intermediate values interpolate
* **Bias-Variance Trade-off**: Lower λ has more bias but lower variance; higher λ vice versa
* **Credit Assignment**: Eligibility traces distribute updates to recently visited states
* **Online vs. Off-line**: Trade-offs between within-episode and end-of-episode learning
* **Dutch Traces**: Improvements offered by true online TD(λ) over standard TD(λ)
* **Convergence Properties**: How λ and α interact to determine learning stability and speed
