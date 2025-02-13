# Dynamic Hedging via Deep Q-Network (DQN)

This repository contains a Python module demonstrating how to:
1. **Simulate asset price paths** using Geometric Brownian Motion (GBM).  
2. **Price options** using the Black-Scholes-Merton (BSM) formula.  
3. **Replicate and hedge options** via delta-hedging and a Deep Q-Network (DQN) agent.  

It includes:

- An `OptionPricer` class for Black-Scholes-Merton calculations (call price and delta).  
- A `GBMSimulator` class for simulating Geometric Brownian Motion (GBM) paths.  
- An `OptionReplicationSimulator` class to demonstrate classical delta-hedging.  
- A `HedgeSimEnv` environment to train a deep RL agent.  
- A `HedgeDQNAgent` for learning hedging strategies using Q-learning.  

## Overview

This code showcases **dynamic hedging** strategies for European call options by combining **option pricing** (Black-Scholes-Merton, Delta-Hedging) with **reinforcement learning** (a Deep Q-Network).  

### Why DQN for Hedging?
- Traditional delta-hedging rebalances based on the Black-Scholes delta at each time step.  
- A **Deep Q-Network** can learn alternative or more nuanced rebalancing strategies under various market conditions or costs, possibly improving hedging performance under certain assumptions.

---

## Structure


**Key Classes/Functions**  
- `OptionPricer`  
- `GBMSimulator`  
- `Plotter`  
- `OptionReplicationSimulator`  
- `HedgeSimEnv`  
- `HedgeDQNAgent`  
- `TestOptionPricer` (Unit Tests)  

---

## Requirements and Installation

1. **Python Version**  
   This code has been tested on Python 3.8+.

2. **Dependencies**  
   - `numpy`
   - `pandas`
   - `scipy`
   - `plotly`
   - `tensorflow` / `keras`
   - `unittest` (part of Python’s standard library)

## Logging and Memory Tracking

- **`@log_execution`** (function decorator)  
  Logs the start and end of each function call with its arguments.
- **`@memory_tracker`** (class decorator)  
  Prints memory cleanup messages upon object deletion (`__del__`).

These decorators showcase Python features for monitoring code execution.


## Results

1. **Classical Delta-Hedging**  
   - Compares the portfolio value vs. the theoretical call price over time.  
   - Provides P&L (difference) and a histogram showing distribution of replication errors.

2. **DQN-Based Hedging**  
   - The agent learns an action policy (what fraction of the asset to hold at each step).  
   - Rewards are negative squared P&L (aiming to minimize hedging error).   
   - After training, the agent is tested for a few episodes, and the resulting P&L is plotted.

---


## License

[MIT License](LICENSE)  
You are free to use, modify, and distribute this code. See [LICENSE](LICENSE) for details.

---

**Happy Hedging!**

---
