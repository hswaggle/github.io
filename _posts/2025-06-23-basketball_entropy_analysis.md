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
This paper explores whether momentum exists in professional basketball through a novel entropy-based statistical analysis. Based on the 2019–20 NBA season play-by-play dataset, we apply a clumpiness measure to scoring sequences and simulate expected distributions under different assumptions.

## 1 Introduction

**IMAGE**

On June 10, 2019, the Toronto Raptors played the Golden State Warriors in Game 5 of the NBA Finals. The Raptors lead the series 3-1 and were looking to raise the Larry O’Brien Championship trophy in front of a home crowd for the first time ever on Canadian soil. The Raptors trailed most of the game, and at the beginning of the fourth quarter, they were down by 6 points. After a back-and-forth exchange of baskets in the first 5 and a half minutes of the quarter, the Raptors click into gear. Kawhi Leonard scored 4 straight baskets interrupted only once by a Draymond two-pointer to take a 6 point lead, the Raptors' first lead since the first quarter. With 3:28 left on the clock, all of Canada can taste its first championship. After a missed three-point attempt by Steph Curry, the Raptors regain possession with 3:12 to go. Suddenly, with the ball in Kawhi’s hands, the unthinkable: Raptors’ floor general Kyle Lowry calls a full timeout. Fans and pundits alike groan. You simply don’t call a timeout when you are hot. When the Raptors return to the floor, the energy is different. Kawhi misses an 11-footer, Klay drains a three, Lowry misses the retribution three, Curry hits another three, Kawhi misses a three, Klay hits another three, Nurse calls another timeout, presumably to stop the Warriors' run. The score is now 106-103. When they return to the floor, Lowry scores the Raptors' final basket of the game a goaltended layup. The Warriors survive game 5. 
“Basketball is a game of runs”. Those familiar with the sport will have heard this before, and not just from fans, but coaches and announcers. The truth of the statement has been a matter of academic discourse since at least 1985, when Thomas Gilovich, Robert Vallone and Amos Tversky published the first evidence for the opposition. In the 4 decades since, many academics have chimed in with their own evidence for and against. 
The majority of the literature has been in opposition to statistical momentum, and in fact the rules are specifically designed to increase parity. For instance, all of soccer, American football and basketball award possession of the ball to the team which has just allowed a score, in a process commonly known as “loser’s ball”. Given that ball possession is generally required to score in these sports, preventing a dominant team from immediately capitalizing on their success should make it harder for teams to score consecutively and hence gain momentum.
Yet the sentiment of the opening paragraph prevails time and again. Why? Analyzing the score margins for a few games, the general game pattern seems to empirically align with this sentiment. Of course, this is not a statistical approach, but it provides a visual intuition for why we as humans so often perceive momentum, despite both the mean reverting nature of the game and the long-standing literature disproving this notion. 



This question has resurged in importance as analytics have become more popular in professional sports. The impact of better decision making could be making the game more momentum driven or less; either way, one thing is sure, the basketball of today's NBA is not the same as that of Gilovich, Vallone, and Tversky’s NBA. 
This paper employs a somewhat novel entropy measure of team wide momentum to test scoring event runs in the course of the game. Our innovation is a novel approach to bootstrapping the null hypothesis distribution of hyper-parameter values, which is a MLE weighted combination of the traditional frequency method, and a Markovian transition approach we call the Loser’s ball effect.

> **Note:** "Basketball is a game of runs." — A common sentiment explored in this paper.

## 2 Literature Review

The seminal paper on the topic by Thomas Gilovich and Robert Vallone and Amos Tversky titled “The Hot Hand in Basketball: On the Misperception of Random Sequences” has inspired a slew of literature on the subject of momentum in basketball and sports generally.  In their paper, Gilovich et al. (1985) explore the common belief of a player's hot hand in basketball. The belief holds that when a player hits a shot, they are more likely to hit their next shot, and similarly when they miss the cooling effect decreases their probability of scoring the next shot. The paper looks at both the psychology behind the belief, and the statistics of its validity. The authors studied data from 48 games of the 76ers 1980-81 season, looking at consecutive free throw shooting. Gilovich et al. (1985) use conditional probabilities, Wald-Wolfowitz run tests, a test of stationarity, and an analysis on inter-game stability using Lexis ratio, a method from David (1949). Part of the discussion of the paper is that the players themselves believed in the hot hand, and later papers like Reifman (2011) discuss how player and coach behavior may inhibit streaks from occurring.
Bocskocsky et al (2014) challenged the assumption of independent shot selection and provide evidence for the hot hand in basketball. Bocskocsky et al (2014) make reference to Gilovich et al. (1985) and their key assumption of independence (emphasis added). 
>“It may seem unreasonable to compare basketball shooting to coin tossing because a player’s chances of hitting a basket are not the same on every shot. Lay-ups are easier than 3-point field goals and slam dunks have a higher hit rate than turnaround jumpers. Nevertheless, the simple binomial model is equivalent to a more complicated process with the following characteristics: Each player has an ensemble of shots that vary in difficulty (depending, for example, on the distance from the basket and on defensive pressure), and each shot is randomly selected from this ensemble” (Gilovich, Vallone and Tversky, 1985)
Using data from 83,000 shots taken during the 2012-13 season, as well as optical tracking data, the authors provide evidence for the non-independence of a player outperforming their usual percentage (a hot handed player), suggesting that these players tend to shoot from farther away, face tighter defense leading to more difficult shots. They use OLS regression for a model of shot difficulty. The authors use this predictive model to establish a complex heat which is a definition of heat corrected for difficulty. With these corrections for difficulty and complex heat they once again run an OLS regression, and find a positive and significant coefficient, which roughly translates to a 1.2% increase in shooting percentage for a hot player when controlling for shot difficulty. The key discussion in Bocskocsky et al (2014) relies on the importance of accurately defining heat. 
>“Concluding that the hot hand exists is contingent on defining “hot” correctly. A player who makes three out of his past four layups is not hot, but a player who makes three out of his past four three-point attempts is. In other words, being hot is not about the absolute number of shots a player has previously made, but rather is about how much he has outperformed, conditional on the types of shots he has taken.”
Both papers were focused on individual player performance. This is distinct from team momentum, especially in the context of correcting for shot difficulty, where to increase the difficulty for the individually hot player, given a finite set of defensive resources, the opposing team must decrease the defense difficulty for the not-hot subset. Reifman (2011) discusses this exact challenge, of the difficulty of measuring streakiness in team performance. Arkes and Martinez (2011) use a correlation test to demonstrate positive momentum between wins. The authors correct for strength of opponents, where again the definition of a hot team is defined to mean outperformance above expectation in the past games rather than simply winning the last few games. 
Steeger et al. (2021) use an entropy model for NHL hockey to suggest that team momentum over the course of a season at a game-by-game granularity does not exist. The entropy model looks at the interarrival time between wins for each team and bootstraps a statistical significance level from a random binomial draw. The advantage of this method is it does not require stationarity, in essence allowing for a team get better (or worse) throughout the season. Steeger et al. (2021) make no corrections for difficulty of opponent, rather the bootstrapped hyperparameter is calculated based on each team's individual end of season winning percentage. 
The entropy measure used in Steeger et al. (2021), was developed in Zhang et al. (2013). The intent of that paper was to develop a non-parametric measure for clumpiness in data. Clumpiness is defined as irregular clusters of data together. Part of the motivation of the Zhang et al. (2013) paper was to create a more powerful statistical measure of clumpiness, in response to the measurement used by Gilovich et al. (1985). One of the advantages in our view of the measure developed by Zhang et al. (2013) is the continuity property. Small changes in the timing of an event have limited effects on the measure. This stands in contrast to a Wald-Wolfowitz run tests which focuses on consecutive sequences of data. For our purposes, the continuity process is important, because in our view the difference between an 8-0 run and a 10-2 run is negligible. 

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
