# Infinite Variance
This repository contains an implementation of an example from reinforcement learning that demonstrates the potential for infinite variance in importance sampling. The setup illustrates how certain off-policy evaluation methods, such as ordinary importance sampling, can produce highly unstable estimates when the variance of the estimator is infinite.

## Problem Description
- This problem is designed to highlight instability in off-policy prediction using importance sampling:

- An agent follows a behavior policy that selects left or right actions uniformly at random.

- The target policy always selects left.

- Each episode terminates when the agent reaches a terminal state (either by choosing right or completing a sequence of left actions).

- A reward of 1 is given if the agent reaches the goal under the target policy.

- The key objective is to estimate the value of the starting state under the target policy using ordinary importance sampling.

### Implementation
Key Concepts:
- Importance Sampling: A technique used for estimating values under a target policy using data collected from a different behavior policy.

- Ordinary Importance Sampling: The standard estimator which averages weighted returns using the importance sampling ratio.

- Variance Issues: When the target policy is deterministic and differs significantly from the behavior policy, the importance sampling ratio can explode, leading to high or infinite variance in the estimates.

### Learning Process:
The environment is run for 100,000 episodes, across 10 runs.

### For each episode:

- A trajectory of actions is generated using the behavior policy.

- The reward is multiplied by this weight and accumulated.

- The ordinary importance sampling estimate is computed over episodes.

### Visualization
- Generated plot is saved in the generated_images/ folder:

figure_5_4.png:
- A line plot showing the ordinary importance sampling estimates across episodes (log scale). This plot highlights the instability and variance in the learning curve across multiple runs.



