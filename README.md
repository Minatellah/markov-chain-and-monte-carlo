## markov-chain-and-monte-carlo

## Traffic Modeling with Markov Chains

This project models traffic state transitions (`light`, `heavy`, `blocked`) using **Markov chains**.  
It is inspired by [K2AAM's GitHub repository](https://github.com/K2AAM/Modeling-Traffic-with-Markov-Chains), with some modifications (initial state) and monte carlo method.

# Transition matrices:
**Early Period (8 am - 4 pm):** Light traffic, transitions likely to remain less congested.
**Rush Hour (4 pm - 6 pm):** Increased likelihood of moving to "Heavy" or "Blocked".
**Late Period (6 pm - 8 pm):** Traffic eases up as the evening progresses.

For the **late** and **rush hour** transition matrices, we notica that the state **blocked** is quasi absorbant

- **Custom Initial State:**  
  The initial traffic state probabilities were changed from `[1, 0, 0]` (as in the original repo) to `[0.7, 0.2, 0.1]` to explore different starting conditions.  
  **Note:** This does **not affect the steady-state probabilities** of the Markov chains, because steady states depend only on the transition matrices, not the initial state, because the stady probabilitiesdepend only on the transition matrix and not the intial state: πP=π

## Monte Carlo
# Early:
Green (light), orange (heavy), red (blocked)

The blocked state (red solid line) rises quickly and stabilizes around 0.65, meaning that in the early period, traffic has a high probability of being blocked in the long run.

light (green) and heavy (orange) decrease over time, stabilizing around 0.1–0.2.

Interpretation: early traffic is prone to congestion, and once blocked, it tends to stay blocked (quasi-absorbing behavior in the transition matrix).

---

# Rush hour
Green (light), orange (heavy), red (blocked) dashed

blocked (red dashed) stabilizes around 0.85, higher than early traffic, which is expected for rush hour.

light drops very low (~0.0–0.05), meaning free-flow traffic is almost impossible.

heavy is moderate (~0.1–0.15), but most transitions end up blocked.

Interpretation: rush hour is the most congested period, with high persistence of blocked traffic. The quasi-absorbing nature of blocked is strongest here.

# Late
Green (light), orange (heavy), red (blocked) dotted

light (green dotted) is now highest (~0.45), blocked (red dotted) is lower (~0.2), heavy around 0.35.

Interpretation: traffic is lighter late in the day, more free-flowing, and blocked states are less frequent. The system is more balanced.

# General interpretation
The Monte Carlo simulations show that during early hours, traffic tends to stabilize with a high probability of blocked states (~66%), while light and moderate states decrease. During rush hour, congestion is even more pronounced, with blocked states reaching ~85%. In contrast, late hours show lighter traffic, with a higher probability of free-flow (~45%) and lower probability of blockage (~20%). These results are consistent with the steady-state distributions and reflect the quasi-absorbing nature of the blocked state.



