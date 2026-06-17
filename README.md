# Geometric brownian motion solution for Example 17.8 
per the lecture notes by Professor Michael Kozdron, University of Regina. 

# Background

**Example 17.8** (Assignment #4, problem #2). Suppose that the price of a stock $\{X_t, t \geq 0\}$ follows geometric Brownian motion with drift $0.05$ and volatility $0.3$ so that it satisfies the stochastic differential equation

$$dX_t = 0.3X_t dB_t + 0.05X_t dt.$$

If the price of the stock at time $2$ is $30$, determine the probability that the price of the stock at time $2.5$ is between $30$ and $33$.

**Solution.** Since the price of the stock is given by geometric Brownian motion

$$dX_t = 0.3X_t dB_t + 0.05X_t dt,$$

we can read off the solution, namely

$$X_t = X_0 \exp \left[ 0.3B_t + \left(0.05 - \frac{0.3^2}{2}\right) t \right] = X_0 \exp [0.30B_t + 0.005t].$$

Therefore,

$$\mathbf{P}\Big[ 30 \leq X_{2.5} \leq 33 \;\Big|\; X_2 = 30 \Big]$$

$$= \mathbf{P}\left[ \frac{\log \left(\frac{30}{X_0}\right) - 0.0125}{0.30} \leq B_{2.5} \leq \frac{\log \left(\frac{33}{X_0}\right) - 0.0125}{0.30} \;\Bigg|\; B_2 = \frac{\log \left(\frac{30}{X_0}\right) - 0.01}{0.30} \right]$$

$$= \mathbf{P}\left[ \frac{\log \left(\frac{30}{X_0}\right) - 0.0125}{0.30} - \frac{\log \left(\frac{30}{X_0}\right) - 0.01}{0.30} \leq B_{0.5} \leq \frac{\log \left(\frac{33}{X_0}\right) - 0.0125}{0.30} - \frac{\log \left(\frac{30}{X_0}\right) - 0.01}{0.30} \right]$$

$$= \mathbf{P}\left[ -\frac{0.0025}{0.30} \leq B_{0.5} \leq \frac{\log \left(\frac{33}{30}\right) - 0.0025}{0.30} \right]$$

using the stationarity of Brownian increments. If $Z \sim \mathcal{N}(0, 1)$ so that $B_{0.5} \sim \sqrt{0.5}\,Z$, then

$$\mathbf{P}\{-0.00833 \leq B_{0.5} \leq 0.3094\} = \mathbf{P}\{-0.0118 \leq Z \leq 0.4375\} = 0$$

# My Correction

Note, there was an error in the lecture notes, and my solution:

**Example 4.** (Stock price). Suppose that the price of a stock $\{X\_t,t\ge0\}$ follows a geometric Brownian motion with drift $0.05$ and volatility $0.3$ so that it satisfies the stochastic differential equation

$$dX_t = 0.3X_t dB_t + 0.05X_t dt.$$ 

If the stock price at time $2$ is $30$, determine the probability that the price of the stock at time $2.5$ is between $30$ and $33$.

**Solution.** Since the price of the stock is given by geometric Brownian motion

$$dX_t = 0.3X_t dB_t + 0.05X_t dt.$$ 

we can read off the solution, namely

$$
X_t = X_0 \exp \left[ 0.3 B_t + \left(0.05 - \frac{0.3^2}{2}\right)t \right] \quad \text{(1)}
$$
$$
= X_0 \exp \left[ 0.3 B_t + 0.005t \right]
$$

Therefore, using (1) for the RHS of the numerator for time 2 and 2.5

$$
\mathbb{P}\Big[ 30 \leq X_{2.5} \leq 33 \;\Big|\; X_2 = 30 \Big]
$$
$$
= \mathbb{P}\left[ \frac{\log\left(\frac{30}{X_0}\right)-\left(0.05-\frac{0.3^2}{2}\right) 2.5}{0.30}\leq B_{2.5} \leq \frac{\log\left(\frac{33}{X_0}\right)-\left(0.05-\frac{0.3^2}{2}\right) 2.5}{0.30} \;\Bigg|\; B_2=\frac{\log\left(\frac{30}{X_0}\right)-\left(0.05-\frac{0.3^2}{2}\right) 2}{0.30} \right]
$$
$$
= \mathbb{P}\left[ \frac{\log\left(\frac{30}{X_0}\right)-0.0125}{0.30}\leq B_{2.5} \leq \frac{\log\left(\frac{33}{X_0}\right)-0.0125}{0.30} \;\Bigg|\; B_2=\frac{\log\left(\frac{30}{X_0}\right)-0.01}{0.30} \right]
$$
$$
= \mathbb{P}\left[ \frac{\log\left(\frac{30}{X_0}\right)-0.0125}{0.30} - \frac{\log\left(\frac{30}{X_0}\right)-0.01}{0.30} \leq B_{0.5} \leq \frac{\log\left(\frac{33}{X_0}\right)-0.0125}{0.30}-\frac{\log\left(\frac{30}{X_0}\right)-0.01}{0.30} \right]
$$
$$
= \mathbb{P}\left[ \frac{-0.0125+0.01}{0.30}\leq B_{0.5} \leq \frac{\log\left(\frac{33}{X_0}\right)-0.0125-\log\left(\frac{30}{X_0}\right)+0.01}{0.30} \right]
$$
$$
= \mathbb{P}\left[ -\frac{0.0025}{0.30}\leq B_{0.5} \leq \frac{\log\left(\frac{33}{30}\right)-0.0025}{0.30} \right]
$$
$$
= \mathbb{P}\left[ -0.0083\leq B_{0.5}\leq 0.3093 \right]
$$

using the stationary of Brownian increments. If $X\sim\mathcal{N}(0,1)$ so that $B\_{0.5}\sim\sqrt{0.5}Z$, then

$$
\begin{align*}
\mathbb{P}\{30\leq X_{2.5}\leq 33 \mid X_2=30\} &=\mathbb{P}\{-0.0083\leq B_{0.5} \leq 0.3093\}\\
&=\mathbb{P}(-0.0083\leq \sqrt{0.5}Z \leq 0.3093)\\
&=\mathbb{P}\left(\frac{-0.0083}{\sqrt{0.5}}\leq Z \leq \frac{0.3093}{\sqrt{0.5}}\right)\\
&=\mathbb{P}(-0.0118\leq Z \leq 0.4375)\\
&=\Phi(0.4375) - \Phi(-0.0118) && \text{(1)}\\
&=0.669126-0.495283\\
&\approx 0.1738
\end{align*}
$$

where step (1) is calculated by the normal distribution function:

$$
\begin{align*}
1-\frac{1}{\sqrt{2\pi}}\int^{0.0118}_{-\infty} e^{-\frac{1}{2}t^2}dt \equiv \frac{1}{\sqrt{2\pi}}\int^{-0.0118}_{-\infty} e^{-\frac{1}{2}t^2}dt&=0.495293\\
\frac{1}{\sqrt{2\pi}}\int^{0.4375}_{-\infty} e^{-\frac{1}{2}t^2}dt&=0.669126\\
\end{align*}
$$

```r
pnorm(0.4375) - pnorm(-0.0118)
# [1] 0.173833

pnorm(-0.0118)
# [1] 0.4952926

pnorm(0.4375)
# [1] 0.6691256
```

# Method

```
import numpy as np

# 1. the parameters given in the problem
X_2 = 30.0        # condition: price at time 2 is 30
mu = 0.05         # drift
sigma = 0.3       # volatility
dt = 0.5          # time step from t=2 to t=2.5 (2.5 - 2.0)
nbSim = 1000000   # no. of monte carlo simulation pathways

# 2. now, generate the standard normal random variables 
# $\text{Z}\sim \text{N}(0, 1)$ and this represents the random shock 
# for each pathway
Z = np.random.randn(nbSim)

# 3. now, simulate the price at t=2.5 using the exact geometric brownian motion
# solution formula:
# X_t = X_0 * exp((mu - 0.5 * sigma^2) * dt + sigma * sqrt(dt) * Z)
# our starting point $X_0$ is physically $X_2$
X_25 = X_2 * np.exp((mu - 0.5 * sigma**2) * dt + sigma * np.sqrt(dt) * Z)

# 4. now, count how many pathways resulting between 30 and 33 and 
# this creates a boolean array of (1) T and (0) F
success_paths = (X_25 >= 30.0) & (X_25 <= 33.0)

# 5. now, calculate the empirical probability (the mean of the 1s and 0s)
simulated_prob = np.mean(success_paths)

print(f"The simulated Probability: {simulated_prob:.4f}")
print("The theoretical Probability: 0.1587")
## The simulated Probability: 0.1742
## The theoretical Probability: 0.1587
```
# Final result
The final output of the code matches my simulated probability of 0.173.











