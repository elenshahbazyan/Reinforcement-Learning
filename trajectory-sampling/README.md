# Trajectory Sampling

This repository compares different sampling distributions for value function updates in reinforcement learning. The project analyzes how uniform sampling versus on-policy sampling affects learning efficiency in randomly generated MDPs with configurable complexity.

## Problem Description

In Trajectory Sampling experiments:

- Agents learn value functions in random MDPs with configurable states and branching factors
  
- Two sampling strategies are compared: uniform state-action coverage vs. on-policy visitation
  
- Each MDP has random transition dynamics and reward structures for controlled experimentation
  
- Episodes can terminate with probability 0.1 at any step, creating stochastic episode lengths
  
- Goal is to understand how sampling distribution affects value function learning speed and accuracy

## Implementation

### Key Components:
* **Random MDP Generation**: Creates tasks with specified state counts and branching factors using random transitions and rewards
* **Expected Updates**: Uses model-based value iteration with full transition expectations rather than sample-based learning
* **Policy Evaluation**: Monte Carlo evaluation of learned policies to measure performance
* **Parallel Processing**: Multi-core execution for efficient experimentation across multiple random tasks

### Sampling Methods:

#### 1. Uniform Sampling:
* **State-Action Coverage**: Systematically cycles through all state-action pairs with equal frequency
* **Update Rule**: Uses expected transitions: `Q(s,a) = (1-p_term) * E[R + max_a' Q(s',a')]`
* **Distribution**: Uniform visitation regardless of policy or state transitions

#### 2. On-Policy Sampling:
* **Policy Following**: Generates state visitations by following ε-greedy policy in the environment
* **Behavioral Distribution**: State frequencies match those that would occur under the current policy
* **ε-Greedy Exploration**: Balances exploitation with random action selection

## Learning Process

### Update Mechanism:
* Both methods use expected updates rather than sample-based temporal difference learning
* Value updates incorporate full branching factor information: average over all possible next states
* Termination probability is factored into expected returns calculation
* Updates occur at every step with periodic policy evaluation for performance tracking

### Evaluation Process:
* Monte Carlo policy evaluation runs 1000 episodes under the greedy policy
* Starting from state 0, follows greedy actions until termination or step limit
* Tracks average cumulative reward as performance metric
* Evaluations occur at regular intervals throughout learning

## Key Features

* **Configurable Complexity**: Adjustable state space size and branching factors
* **Statistical Reliability**: Multiple random tasks averaged for robust results
* **Efficient Implementation**: Vectorized operations and pre-computed random values
* **Performance Tracking**: Regular evaluation points throughout learning process
* **Parallel Execution**: Multi-core processing for faster experimentation

## Analysis Capabilities

* **Learning Curves**: Compare convergence speed between sampling methods
* **Parameter Sensitivity**: Study effects of state space size and branching factor
* **Distribution Impact**: Analyze how visitation frequency affects learning efficiency
* **Statistical Significance**: Average results across multiple random MDPs

## Theoretical Insights

This implementation demonstrates key concepts in reinforcement learning theory:

* **Sampling Distribution Effects**: How state visitation frequencies influence learning speed
* **Expected vs. Sample Updates**: Benefits of model-based learning when transition models are available
* **Policy-Dependent Learning**: How on-policy sampling can focus learning on relevant states
* **Exploration-Exploitation**: Trade-offs in ε-greedy action selection during learning
