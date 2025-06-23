---
layout: post
title: "Momentum in Basketball: A Statistical Entropy Analysis"
subtitle: "Do Runs Actually Exist in the NBA?"
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [basketball, analytics, entropy, statistics]
comments: true
mathjax: true
author: Harrison Waddell, Ismail Abdelmalek, and Charles Johnson
---

{: .box-success}
This post explores whether momentum exists in professional basketball through a novel entropy-based statistical analysis. Based on the 2019–20 NBA season, we apply a clumpiness measure to scoring sequences and simulate expected distributions under different assumptions.

## Introduction

**IMAGE**

On June 10, 2019, the Toronto Raptors played the Golden State Warriors in Game 5 of the NBA Finals...<br/><br/>
> **Note:** "Basketball is a game of runs." — A common sentiment explored in this paper.

## Literature Review

**IMAGE**

The idea of momentum in sports is not new. The seminal paper by Gilovich, Vallone, and Tversky (1985) titled *“The Hot Hand in Basketball”* questioned whether perceived streaks were merely illusions...<br/><br/>

## Methodology

**IMAGE**

We use a scaled entropy measure from Zhang et al. (2014). This requires two transformations:<br/>
1. Convert game-time to **score-time**<br/>
2. Convert score margin changes to binary outcomes<br/><br/>

### Definitions

Let \( t \in [0, T] \) be game time. Define:

$$
S(t) = H(t) - A(t)
$$

Indicator function:

$$
\mathbf{1}_{\Delta S(t)} =
\begin{cases}
1, & S(t) \neq S(t - 1) \\
0, & S(t) = S(t - 1)
\end{cases}
$$

Score-time:

$$
\tau = N(t) = \sum_{i=1}^{t} \mathbf{1}_{\Delta S(i)}
$$

Inter-event times \( x_i \):

$$
x_i =
\begin{cases}
\tau_1, & i = 1 \\
\tau_i - \tau_{i-1}, & 2 \leq i \leq n \\
N + 1 - \tau_n, & i = n+1
\end{cases}
$$

Normalized:

$$
\tilde{x}_i = \frac{x_i}{N + 1}, \quad \sum_{i=1}^{n+1} \tilde{x}_i = 1
$$

Entropy:

$$
H_p = \frac{\sum_{i=1}^{n+1} \tilde{x}_i \log(\tilde{x}_i)}{\log(n + 1)}
$$

### Simulation Approaches

- **Frequency-based**:  
  $$ p_s^g = \frac{S_h^g}{S_h^g + S_a^g} $$

- **Markovian ("loser's ball")**:

  $$
  p_h = P(S_h | H), \quad p_a = P(S_a | A)
  $$

  Transition matrix:

  $$
  M =
  \begin{bmatrix}
  p_h & 1 - p_h \\
  1 - p_a & p_a
  \end{bmatrix}
  $$

Blended approach:

$$
P_{HH}^g = \lambda p_s^g + (1 - \lambda)p_h
$$

$$
P_{AA}^g = \lambda (1 - p_s^g) + (1 - \lambda)p_a
$$

**IMAGE**

## Parameter Estimation

Maximum likelihood estimation for \( \lambda \):

$$
\ln(L(\lambda)) = \sum_{g=1}^{G} \ln(L_g(\lambda)) =
\sum_{g=1}^{G} \left[
N_{HH}^g \ln(P_{HH}^g) +
N_{HA}^g \ln(P_{HA}^g) +
N_{AH}^g \ln(P_{AH}^g) +
N_{AA}^g \ln(P_{AA}^g)
\right]
$$

Result:

$$
\lambda^* = \arg\max_{\lambda} \ln(L(\lambda)) = 0.249
$$

## Analysis

We applied the entropy measure to all games in the 2019–20 season. Out of 1230 games, only 50 were statistically significant.<br/><br/>

### Mann-Whitney U Test

- **U-statistic:** 970.0  
- **P-value:** 0.4337

> {: .box-warning}
> No season-level evidence for momentum exists.

## Discussion and Results

**IMAGE**

Despite the persistent fan belief, statistical evidence for momentum remains elusive...<br/><br/>

<details markdown="1">
<summary>Further Questions</summary><br/>
- Are blowouts correlated with statistical entropy?  
- Do timeouts affect momentum (as fans often claim)?  
- What can be learned midgame from entropy tracking?
</details>

## Bibliography

See original sources including:<br/>
- Gilovich et al. (1985), *The Hot Hand in Basketball*<br/>
- Bocskocsky et al. (2014), *Heat Check*<br/>
- Zhang et al. (2013), *New Measures of Clumpiness*<br/>
- Steeger et al. (2021), *Entropy in NHL*<br/>
- And many more...
