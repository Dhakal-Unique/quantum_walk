# quantum_walk
## Quantum Walks and Monte Carlo
### Auther
Name : Unique Dhakal     

Enrolled Id : gst-vqdADzObPErh7wD

## Executive summery 

This project explores quantum walk simulations using Galton-style circuits to emulate classical and non-classical distributions. The goal is to generalize the quantum Galton board algorithm, experiment with multiple target distributions, and evaluate performance under realistic noise
### Generalization of Quantum Galton Board
Starting from 1- and 2-layer circuits, I developed a scalable function that generates quantum Galton boards for any number of layers. The circuit uses Hadamard and CNOT gates to simulate superposition and entanglement, with CSWAP gates (later decomposed) for interference-based routing. The output distribution was analyzed using Hamming weight histograms and validated against a Gaussian target using R² regression.

- Gaussian behavior confirmed up to 10 layers

- R² ≥ 0.998 for layers 2–8, showing strong fidelity
### Exploration of Alternative Distributions
**Exponential Distribution**
- Replaced Hadamard with RX(π/4) to bias the coin flip

- Used CSWAP routing to preserve conditional logic

- Evaluated exponential decay via log-transformed R² regression

**Hadamard Quantum Walk**
- Initialized coin in (|0⟩ + i|1⟩)/√2 for symmetric superposition

- Defined increment() and decrement() functions for binary position updates

- Achieved balanced, symmetric distributions centered around initial position
## Noise Model Simulation
To simulate real-world conditions, I used the ibm_brisbane noise model in AerSimulator. CSWAP gates were decomposed due to hardware constraints. I tested circuit depth from 2 to 10 layers and measured fidelity using Gaussian R² scores.

- Layer 9: R² = 0.9935 (slight degradation)

-  Layer 10: R² = 0.9679 (still above threshold of 0.85)

-  No CX gates used after transpilation, confirming optimization
## Distance Metrics and Uncertainty
To quantify how close the noisy output matched the ideal distribution, I computed the Hellinger distance between measured and target probabilities. I also accounted for stochastic uncertainty from finite sampling (5000 shots) using binomial standard errors.

✅ Final result: Hellinger distance = 0.0231 ± 0.0158

This confirms high fidelity and statistical robustness of the quantum walk circuit under realistic noise.
