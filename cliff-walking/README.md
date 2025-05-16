# Cliff Walking
This repository contains an implementation of the Cliff Walking environment from reinforcement learning. It is used to compare the performance of SARSA, Expected SARSA, and Q-learning algorithms in a grid-based navigation task with dangerous cliff edges.

The environment emphasizes the difference between on-policy and off-policy learning, and how various algorithms handle the exploration vs. exploitation trade-off.

## Problem Description
In Cliff Walking:

- The agent moves in a grid world aiming to reach a goal while avoiding the cliff.

- Falling off the cliff results in a large negative reward (−100) and resets the episode.

- Valid actions include moving up, down, left, or right.

- The objective is to learn an optimal policy that reaches the goal with minimum penalty.

### Implementation
Key Concepts:
- States: Each grid cell is a state identified by its row and column.

- Actions: The agent chooses from 4 actions per state.

- Reward Function: −1 per step, −100 for falling into the cliff.

##3 Policy Learning:

- SARSA: On-policy temporal difference learning.

- Q-learning: Off-policy learning with maximization.

- Expected SARSA: A smoother variant using expected values under the current policy.

### Learning Process
- The environment is run over multiple episodes and independent runs.

- Average reward per episode is tracked for each method.

- Two metrics are visualized:

  - Learning performance over time (episodic rewards).

  - Effect of step-size (α) on both interim (first 100 episodes) and asymptotic performance.

### Visualization
Generated plots are saved in the generated_images/ folder:

- example_6_6.png:
Compares SARSA and Q-learning in terms of total reward per episode.
SARSA tends to find safer paths, while Q-learning converges to the optimal (but riskier) path.

- figure_6_3.png:
Shows performance of SARSA, Expected SARSA, and Q-learning under different step-size settings.
Includes both interim and asymptotic reward curves.
