# 1 Introduction

On June 10, 2019, the Toronto Raptors played the Golden State Warriors in Game 5 of the NBA Finals...
**IMAGE**

# 2 Literature Review

The seminal paper on the topic by Thomas Gilovich, Robert Vallone, and Amos Tversky titled *“The Hot Hand in Basketball: On the Misperception of Random Sequences”* has inspired a slew of literature...
**IMAGE**

# 3 Methodology

To determine whether scores in basketball are clumpier...

**IMAGE**

Let \( t \) represent game-time where:

\[
t \in [0, T]
\]

...

\[
\dot{M}_g = 
\begin{bmatrix}
P_{HH}^g & 1 - P_{HH}^g \\
1 - P_{AA}^g & P_{AA}^g
\end{bmatrix}
\]

**IMAGE**

# 4 Parameter Estimation

We plotted each team’s \( p_s \) values against total home wins...

Maximum likelihood estimation for \( \lambda \):

\[
\ln(L(\lambda)) = \sum_{g=1}^{G} \ln(L_g(\lambda)) = \sum_{g=1}^{G} \left[ 
N_{HH}^g \ln(P_{HH}^g) + 
N_{HA}^g \ln(P_{HA}^g) + 
N_{AH}^g \ln(P_{AH}^g) + 
N_{AA}^g \ln(P_{AA}^g)
\right]
\]

Optimize:

\[
\lambda^* = \arg \max_{\lambda} \ln(L(\lambda))
\]

Estimated \( \lambda^* = 0.249 \)

# 5 Analysis

Using entropy, we assessed all 2019–20 games...
**IMAGE**

Mann-Whitney U Test:

- U-statistic: 970.0  
- P-value: 0.4337

# 6 Discussion and Results

With the rise of analytics and persistent myths...

Future directions:

- Assessing if blowouts or timeouts affect entropy  
- Midgame entropy tracking for managerial decisions  
- Comparing momentum across seasons

# Bibliography

- Albright, S. C. (1993)...  
- Arkes, J., & Martinez, J. (2011)...  
- Avugos, S. et al. (2013)...  
- Bar-Eli, M. et al. (2006)...  
- Bocskocsky, A. et al. (2014)...  
- David, F. N. (1949)...  
- Gilovich, T. et al. (1985)...  
- Reifman, A. (2011)...  
- Schilling, M. (2019)...  
- Steeger, G. M. et al. (2021)...  
- Wolfowitz, J. (1943)...  
- Zhang, Y. et al. (2013)...
