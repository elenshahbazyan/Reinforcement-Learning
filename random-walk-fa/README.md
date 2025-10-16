# Function Approximation (Random Walk)

This repository explores various function approximation methods for value estimation in reinforcement learning. The project implements and compares multiple representation schemes applied to a large-scale random walk environment with 1000 states, demonstrating how function approximation enables learning when tabular methods become impractical.

## Problem Description

In this Function Approximation environment:
* Agent navigates 1000 non-terminal states in a linear chain with terminal states at each end
* Starts from the central state (500) and follows a random policy
* Actions move left (-1) or right (+1) with random step sizes between 1 and 100
* Terminal rewards: -1 for reaching the left boundary (state 0), +1 for the right boundary (state 1001)
* All non-terminal transitions have zero reward
* Goal is to accurately estimate state values using function approximation with limited parameters

## Implementation

### Function Approximation Methods:

#### 1. State Aggregation:
* **Grouping**: Divides states into fixed-size groups with shared parameters
* **Value Estimation**: All states in a group share the same value estimate
* **Updates**: Modifies the group parameter when any state in the group is visited
* **Simplicity**: Simplest form of function approximation with minimal computation

#### 2. Polynomial Bases:
* **Basis Functions**: Uses polynomial features: 1, s, s², s³, ..., s^n
* **Linear Combination**: State value is weighted sum of polynomial features
* **Order Parameter**: Configurable polynomial degree controlling approximation power
* **Smooth Approximation**: Provides smooth value function across state space

#### 3. Fourier Bases:
* **Basis Functions**: Uses cosine features: cos(0πs), cos(1πs), cos(2πs), ..., cos(nπs)
* **Periodic Properties**: Leverages orthogonal Fourier basis for efficient representation
* **Order Parameter**: Number of Fourier terms controlling approximation quality
* **Fast Convergence**: Often converges faster than polynomial bases

#### 4. Tile Coding:
* **Multiple Tilings**: Uses overlapping tilings offset from each other
* **Binary Features**: Each state activates one tile per tiling
* **Distributed Representation**: State value is sum of activated tile weights
* **Local Generalization**: Updates affect nearby states through shared tiles
* **Configurable**: Adjustable number of tilings, tile width, and tiling offset

### Learning Algorithms:

#### Gradient Monte Carlo:
* **Full Episodes**: Waits for episode completion to compute returns
* **Unbiased Targets**: Uses actual returns without bootstrapping
* **Parameter Updates**: Adjusts weights using gradient of squared error
* **Update Rule**: θ ← θ + α[G_t - v̂(S_t, θ)]∇v̂(S_t, θ)

#### Semi-Gradient n-step TD:
* **Bootstrapping**: Uses n-step returns combining rewards and estimated values
* **Partial Episodes**: Updates can occur before episode completion
* **Biased but Lower Variance**: Trades some bias for reduced variance
* **Update Rule**: θ ← θ + α[G_t:t+n - v̂(S_t, θ)]∇v̂(S_t, θ)

## Key Features

* **True Value Computation**: Dynamic programming calculates exact state values for evaluation
* **Multiple Representations**: Compares four distinct function approximation schemes
* **Algorithm Comparison**: Tests both MC and TD learning approaches
* **Large State Space**: 1000 states demonstrating need for generalization
* **Variable Step Sizes**: Random steps (1-100) create complex transition dynamics
* **Configurable Parameters**: Adjustable orders, tile widths, and learning rates

## Analysis Capabilities

* **Approximation Quality**: Measure error between learned and true values
* **Convergence Speed**: Compare learning rates across methods and algorithms
* **Representation Power**: Analyze how basis order/complexity affects accuracy
* **Computational Efficiency**: Evaluate update costs for different methods
* **Generalization**: Study how well methods interpolate between visited states

## Theoretical Insights

This implementation demonstrates fundamental concepts in function approximation:

* **Curse of Dimensionality**: Why tabular methods fail in large state spaces
* **Bias-Variance Trade-off**: How representation choice affects approximation error
* **Feature Engineering**: Impact of basis function selection on learning performance
* **Bootstrapping Effects**: Differences between MC and TD with function approximation
* **Generalization**: How function approximation enables learning from limited experience
