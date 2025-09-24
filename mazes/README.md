# Mazes 
## Problem Description
In the Dyna Maze environment:

- The agent navigates through grid-based mazes with obstacles, aiming to reach goal states from start positions.
  
- Actions include moving up, down, left, or right within the grid boundaries.
  
- The environment can be static or dynamic, with obstacles that may change during learning.
  
- The agent receives rewards upon reaching goal states and must learn optimal policies through experience.
  
- The challenge is to minimize the number of real environment interactions needed to learn effective navigation strategies.

## Implementation

### Key Concepts:

- States: Each grid cell represents a state, identified by row and column coordinates.
  
- Actions: Four discrete actions (up, down, left, right) available in each state.
  
- Model Learning: The agent builds and maintains models of the environment dynamics.
  
- Planning: Uses learned models to simulate additional experiences beyond real interactions.

## Algorithm Components:
1. Dyna-Q:

- Direct Learning: Updates Q-values using real environmental experiences through standard Q-learning.
- Model Updates: Feeds observed transitions into environmental models (TrivialModel or TimeModel).
- Planning Steps: Performs additional Q-value updates using simulated experiences from the learned model.
- Integration: Seamlessly combines real and simulated experiences for accelerated learning.

2. Changing Maze:

- Environment Dynamics: Tests algorithm performance when maze obstacles change during learning.
- Adaptation Speed: Compares how TrivialModel and TimeModel handle environmental changes.
- Time-weighted Model: Uses recency weighting to prioritize recent experiences over outdated ones.
- Performance Tracking: Monitors cumulative rewards across different adaptation strategies.

3. Prioritized Sweeping:

- Priority Queue: Maintains state-action pairs ordered by the magnitude of potential value updates.
- Threshold-based Updates: Only processes updates that exceed a minimum significance threshold.
- Predecessor Tracking: Updates states that lead to recently updated states, propagating value changes backward.
- Efficient Planning: Focuses computational resources on the most impactful value updates.

## Learning Process
### Dyna-Q Algorithm:

- Episodes run from start states until goal states are reached or step limits are exceeded.
- Each real step triggers both direct Q-learning updates and model feeding.
- Planning phases sample from learned models to perform additional Q-value updates.
- The balance between real steps and planning steps is configurable through parameters.

### Prioritized Sweeping:

- Maintains priority queues of state-action pairs based on update magnitudes.
- Processes high-priority updates first, maximizing learning impact per computation.
- Tracks predecessor relationships to propagate value changes through the state space.
- Continues planning until priority queues are empty or step limits are reached.

### Key Features

- Action Selection: ε-greedy exploration strategy balancing exploration and exploitation.
  
- Model Types: Support for different model architectures including time-weighted models.
  
- Dynamic Environments: Handles changing obstacle configurations during learning.
  
- Priority Management: Efficient priority queue implementation for focused planning.
  
- Performance Metrics: Tracks steps per episode, cumulative rewards, and planning efficiency.
  
- Convergence Checking: Automated detection of optimal policy discovery using path validation.

## Visualization
The implementation supports comprehensive analysis through various metrics:

- Learning Curves: Episode length reduction over time showing learning progress.
  
- Planning Efficiency: Comparison of algorithms based on real vs. simulated experience ratios.
  
- Adaptation Performance: Response speed to environmental changes in dynamic scenarios.
  
- Priority Distribution: Analysis of which state-action pairs receive planning focus.
  
Computational Cost: Tracking of backups and planning steps required for convergence.

## Theoretical Insights
This implementation demonstrates several fundamental concepts in model-based reinforcement learning:

- Sample Efficiency: How planning with learned models reduces the number of real environmental interactions needed.
  
- Model Accuracy: The trade-off between model complexity and learning speed in dynamic environments.
  
- Planning Focus: How prioritization schemes can dramatically improve computational efficiency.
  
- Exploration Integration: The interaction between exploration strategies and model-based planning.
  
- Adaptation Mechanisms: How different model architectures handle environmental changes.
