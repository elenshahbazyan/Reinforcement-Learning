# Updates Comparison (Value Estimation Analysis)

This repository analyzes how environmental complexity affects value estimation accuracy in reinforcement learning. The project studies how branching factor (number of successor states) influences estimation error and convergence properties.

## Problem Description

In the Updates Comparison analysis:

- States have a branching factor `b` representing the number of possible successor states
  
-  Successor state values follow a Gaussian distribution
  
- The true state value is the mean of the successor distribution
  
- The agent estimates this by sampling successors and computing running averages
  
- Goal is to minimize estimation error and understand convergence behavior

## Implementation

### Key Components:
- **Branching Factor (b)**: Number of successor states, controlling environmental complexity
- **True Value**: Analytical mean of the Gaussian successor distribution
- **Sequential Sampling**: Random sampling from successors with running average updates
- **Error Tracking**: Records absolute difference between estimates and true values

### Process:
- Generate random Gaussian distribution for `b` successor states
- Calculate analytical true value (distribution mean)
- Sample successors iteratively and update running estimates
- Track estimation error after each sample for `2 * branching_factor` iterations

## Key Features

- **Complexity Control**: Adjustable branching factor for different environments
- **Ground Truth**: Analytical true values for accurate error measurement
- **Convergence Analysis**: Error tracking over increasing sample sizes
- **Sample Efficiency**: Studies relationship between samples and accuracy

## Analysis Capabilities

- **Convergence Curves**: Plot error reduction over sample iterations
- **Branching Factor Impact**: Compare estimation difficulty across different complexity levels
- **Sample Complexity**: Determine required samples for target accuracy

## Theoretical Insights

Demonstrates fundamental concepts:

- **Law of Large Numbers**: Sample averages converge to true expected values
- **Environmental Complexity**: Branching factor affects estimation difficulty
- **Sample Efficiency**: Trade-offs between computational cost and accuracy
