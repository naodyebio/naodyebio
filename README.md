# Statistical Simulation Engine

A Python and NumPy project investigating the behaviour of Bernoulli trials through simulation, with a focus on the **Law of Large Numbers (LLN)** and **Central Limit Theorem (CLT)**.

## Overview

This project uses simulation to investigate how the estimated probability of obtaining a head behaves when repeatedly tossing a fair coin.

For a fair coin,

$$
P(X=1)=0.5
$$

where \(X=1\) represents a head and \(X=0\) represents a tail.

Rather than only simulating coin tosses, the project compares the empirical results with the corresponding theoretical results from probability and statistics.

## Experiments

### 1. Convergence of the estimated probability

The first experiment investigates whether the proportion of heads approaches \(0.5\) as the number of tosses increases.

For \(n\) tosses, define

$$
\hat{p}_n = \frac{1}{n}\sum_{i=1}^{n}X_i.
$$

The Law of Large Numbers tells us that

$$
\hat{p}_n \rightarrow 0.5
$$

as \(n\) becomes large.

The simulation investigates this behaviour by plotting the estimated probability of heads against the number of tosses.

### 2. Sampling distribution

The second experiment fixes the number of tosses and repeats the experiment many times.

This allows the distribution of \(\hat p_n\) to be investigated rather than looking at only one sequence of coin tosses.

For a Bernoulli random variable with \(p=0.5\),

$$
E[X]=0.5
$$

and

$$
\operatorname{Var}(X)=p(1-p)=0.25.
$$

Since \(\hat p_n\) is the sample mean,

$$
E[\hat p_n]=0.5
$$

and

$$
\operatorname{Var}(\hat p_n)=\frac{0.25}{n}.
$$

The simulation compares these theoretical quantities with the empirical mean and variance.

### 3. Effect of sample size on variance

The third experiment investigates how the variability of the estimated probability changes as \(n\) increases.

The theoretical relationship is

$$
\operatorname{Var}(\hat p_n)=\frac{0.25}{n}.
$$

Therefore, increasing the number of observations reduces the variance of the estimator.

The simulation compares the empirical variance with this theoretical relationship for several values of \(n\).

### 4. Central Limit Theorem

The final experiment investigates the distribution of the standardised estimator.

The standardised statistic is

$$
Z_n =
\frac{\hat p_n-0.5}
{\sqrt{0.25/n}}.
$$

The Central Limit Theorem predicts that, for sufficiently large \(n\),

$$
Z_n \xrightarrow{d} N(0,1).
$$

The simulation therefore compares the empirical distribution of \(Z_n\) with the standard normal distribution.

## Computational Approach

The project initially used direct simulation of individual coin tosses before moving towards vectorised NumPy operations.

The vectorised implementation represents multiple experiments as a two-dimensional NumPy array. Each row represents one independent experiment, allowing the sample proportion for many experiments to be calculated simultaneously.

This avoids unnecessary Python-level loops and makes the simulation more computationally efficient.

## Mathematical Concepts

The project currently uses:

* Bernoulli random variables
* Expected value
* Variance
* Sample means
* Sampling distributions
* Law of Large Numbers
* Central Limit Theorem
* Standardisation
* Monte Carlo simulation
* NumPy vectorisation

## Results

The simulations show behaviour consistent with the theoretical predictions:

* The estimated probability of heads approaches \(0.5\) as the sample size increases.
* The empirical mean of the estimated probability is close to \(0.5\).
* The empirical variance decreases as \(n\) increases.
* The empirical variance is consistent with the theoretical relationship \(0.25/n\).
* The standardised sampling distribution becomes increasingly similar to a standard normal distribution as \(n\) increases.

The simulations provide numerical evidence consistent with the theoretical results; they do not constitute proofs of the LLN or CLT.

## Future Development

Planned extensions include:

* Benchmarking Python loops against NumPy vectorisation.
* Investigating biased coins with different values of \(p\).
* Comparing empirical results with the theoretical variance \(p(1-p)/n\).
* Adding reproducible random seeds.
* Organising the simulation into reusable functions.
* Expanding the statistical analysis and visualisations.
* Improving the project documentation and presentation.
