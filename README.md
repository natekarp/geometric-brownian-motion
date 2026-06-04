# Geometric brownian motion solution for Example 17.8 
per the lecture notes by Professor Michael Kozdron, University of Regina. 

# Background
<img width="697" height="657" alt="problem1" src="https://github.com/user-attachments/assets/60300d84-5cf9-4863-93da-14d813e94eaf" />

Note, there was an error in the lecture notes, and my solution:

<img width="723" height="402" alt="3pt" src="https://github.com/user-attachments/assets/323e9672-54d7-4d7c-8cd3-0a39a86ebf68" />
<img width="687" height="859" alt="2pt" src="https://github.com/user-attachments/assets/c08453a5-52ba-4b4b-83d1-43d5086c3ea4" />
<img width="681" height="719" alt="1pt" src="https://github.com/user-attachments/assets/7a67d882-7b7d-465f-ac7a-ff0a8deab711" />

# Method

```
import numpy as np

T = 1.0 
N = 1000        # no. of out steps t (time) reduced for speed of code output
dt = T / N
nbSim = 10000   # no. of our simulations
Ito_sum = 0.0

# our time grid at the left endpoints here
t = np.linspace(0, T - dt, N) 

for j in range(nbSim):
    # now, we generate the brownian increments 
    dW = np.sqrt(dt) * np.random.randn(N)
    # now, we compute the brownian motion paths, starting at 0
    W = np.cumsum(dW)
    
    # now, we use 0 to get the value of W at the left endpoints here
    # and drop the last element
    W_left = np.insert(W, 0, 0)[:-1]
    
    # now, the itô integral is therefore: sum of (t_i * W_i * dW_i)
    ito_trajectory = np.sum(t * W_left * dW)
    
    # now, we accumulate the square of the integral here
    Ito_sum += ito_trajectory ** 2

# now, we calculate the expected value 
E_Ito_squared = Ito_sum / nbSim
print("Expected value of the squared Itô integral is: {:.6f}".format(E_Ito_squared))
## Expected value of the squared Itô integral is: 0.236472
```

Then, to simulate the paths:

```
import numpy as np
import matplotlib.pyplot as plt

T = 1.0 
N = 1000        
dt = T / N
nbSim = 10     

# our time grid 
t = np.linspace(0, T - dt, N) 

plt.figure(figsize=(10, 6))

for j in range(nbSim):
    dW = np.sqrt(dt) * np.random.randn(N)
    W = np.cumsum(dW)
    W_left = np.insert(W, 0, 0)[:-1]
    
    # now, we calculate our running integral over time using cumsum
    # which gives us the value of the integral at every single time step
    ito_path = np.cumsum(t * W_left * dW)
    
    # now, we plot our simulation's path
    plt.plot(np.linspace(0, T, N), ito_path, label=f'Path {j+1}')

plt.title(r'Simulated Paths of the Itô Integral $\int_0^t s W_s \, dW_s$', fontsize=14)
plt.xlabel('Time (t)', fontsize=12)
plt.ylabel('Integral Value', fontsize=12)
plt.grid(True, linestyle='--', alpha=0.6)
plt.axhline(0, color='black', lw=1) # Adds our baseline at 0
plt.savefig('simulateditointegral.png', dpi=300, bbox_inches='tight')
plt.show()
```
# Final result
<img width="636" height="413" alt="itointegral" src="https://github.com/user-attachments/assets/4138dacf-cebe-48fe-8a0f-941dbae340ce" />







