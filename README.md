# Geometric brownian motion solution for Example 17.8 
per the lecture notes by Professor Michael Kozdron, University of Regina. 

# Background
<img width="697" height="657" alt="problem1" src="https://github.com/user-attachments/assets/60300d84-5cf9-4863-93da-14d813e94eaf" />

Note, there was an error in the lecture notes, and my solution:

<img width="681" height="719" alt="1pt" src="https://github.com/user-attachments/assets/7a67d882-7b7d-465f-ac7a-ff0a8deab711" />
<img width="687" height="859" alt="2pt" src="https://github.com/user-attachments/assets/c08453a5-52ba-4b4b-83d1-43d5086c3ea4" />
<img width="723" height="402" alt="3pt" src="https://github.com/user-attachments/assets/323e9672-54d7-4d7c-8cd3-0a39a86ebf68" />

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











