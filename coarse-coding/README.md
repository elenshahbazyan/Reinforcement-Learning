# Coarse Coding (Function Approximation)

This repository demonstrates coarse coding as a function approximation technique in reinforcement learning. The project learns to approximate a square wave function using overlapping feature windows, illustrating how linear models with distributed representations can capture non-linear patterns.

## Problem Description

In the Coarse Coding problem:
* Approximate a square wave function defined over the domain [0, 2)
* The target function returns 1 for inputs in (0.5, 1.5) and 0 elsewhere
* Learn from randomly sampled points using overlapping feature windows
* Each point activates multiple features, enabling distributed representation
* Goal is to approximate the discontinuous function using linear combination of features

## Implementation

### Key Components:

#### 1. Interval Class:
* **Boundaries**: Stores left and right bounds of feature windows
* **Containment Check**: Determines if a point falls within the interval
* **Size Calculation**: Computes interval length for feature placement

#### 2. ValueFunction Class:
* **Feature Windows**: Creates overlapping intervals across the domain
* **Active Features**: Identifies which features are activated by each point
* **Value Estimation**: Computes function value as weighted sum of active features
* **Weight Updates**: Adjusts feature weights using gradient descent

### Learning Process:

#### Feature Representation:
* Creates `num_of_features` overlapping intervals with specified `feature_width`
* Features are evenly distributed across the domain with controlled overlap
* Each point typically activates multiple adjacent features
* Distributed representation enables smooth generalization

#### Training:
* Samples random points uniformly from domain [0, 2)
* Evaluates true square wave value at each sampled point
* Computes prediction error (delta) between true and estimated values
* Updates weights of active features proportionally to error
* Update size is normalized by number of active features

## Key Features

* **Configurable Architecture**: Adjustable feature width, count, and learning rate
* **Overlapping Representation**: Multiple features active per point for smooth approximation
* **Gradient Descent**: Stochastic updates based on prediction errors
* **Generalization**: Feature overlap enables interpolation between sampled points
* **Distributed Learning**: Updates affect multiple nearby points through shared features

## Analysis Capabilities

* **Approximation Quality**: Compare learned function to true square wave
* **Feature Visualization**: Display feature window placement and activations
* **Weight Analysis**: Examine learned feature weights after training
* **Convergence Study**: Track approximation error over training samples
* **Parameter Sensitivity**: Test effects of feature width and count on accuracy

## Theoretical Insights

This implementation demonstrates fundamental concepts in function approximation:

* **Coarse Coding**: How overlapping features create distributed representations
* **Linear Function Approximation**: Approximating non-linear functions with linear models
* **Generalization**: Feature overlap enables predictions at unsampled points
* **Basis Functions**: Using simple features to build complex approximations
* **Gradient Descent**: Weight updates following error gradients for convergence
