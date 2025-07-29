# Quantum Galton Board (My Understaning & Project Summary)
> Based on paper : *"Universal Statistical Simulator"* by Mark Carney & Ben Varcoe
## What is a Galton Board Anyway?
So the classical Galton board or quincunx is this tringle of pegs where you drop a ball from top. It bounces left or right randomly at each peg. If you drop enough balls, they stack up into bin and form a bell shaped curve commonly known as Gaussian distribution at the bottom.
Each path of a ball take is like a binary decision sequence. The counts in each @bin relate to binomial coefficient Pascal triangle on action.You can even play around with the board to get different distributions. 
In simulations, it's like a Monte Carlo machine i.e you run it many times to buid up a distribution.

---
## Quantum Version (Why it's cool)
In Quantum version , insted of repeating trials, we build a **quantum circuit** that simulates *all possible path on superposition*.One run = exponential power.
### Here's the idea:
- Use a **Hadmard gate** or **Rx(theta)** (if you want bais) to create superpostion at each peg.
- Use **controlled-SWAP** and **CNOT** gate to buid amplitude left/right.
- At end **measure** the qubit to gate the output distribution.

One circuit encode the whole galton board all 2^n paths for an *n* layer system.
----

## How the Quantum Peg Works 
Each peg or module uses:
- 1 control qubit : sets the direction (via h or Rx(theta))
- 3 workspace qubits : handel the ball's motion
- Gates :
  - 'h' or 'Rx(theta)'
  - 'controlled-SWAP'
  - CNOT

Repeat this for each layer of board .
> for n layer we meed 2^n qubit

## Why This Matter 
- **Exponential spped-up** : Classical need many runs. Quantum does it in one.
- **Custom distributions**: Just tune the theta angle in Rx(theta) to bias properties.
- **Fexible**: Simulate bionomial , Gaussion , exponential , even weird custum distributions.
It also connects with **quantum walks** , expect this is more like binary tree structure.
---
## My Implementation Plan
1) **Generalization the basic Galton board algorithm:** 
   I will start from a basic 1-2 layer Quantum Galton circuit and write more general function that can generate circuit for any number of layer. The goal here is to cheak that the output distribution tends toward a **quatum version of Gaussian**.
   
2) **Experiment with other distribution:** 
   I will modify the function so that it does not just produce Gaussian pattrens.I will target two other types:
   - An **Exponential Distribution**
   - A **Hadamard quantum walk** this will use an ideal all to all noiseless sampler, so i can see the theoritical performance first.
  
3) **Introduce real-world noise:**
   Quantum computer are not perfect. so next ,I will simulate the same quantum circuit using realistic hardware noise model.The goal is to see how many layer ,I can keep while getting good results even when noise and hardware error start to mess things up.

4) **Measure how close we got:**
   Finally , I will calculate how far off my results are from the target distributions. This include measuring distances and accounting for randomness due to finite sampling.
----
## Final Thought
The Quantum Galton Board really clicked with me because it blends intuitive classical ideas with quantum superposition and interference.I am excited to explore more, impliment it in Qiskit.
---
## Paper and Reference
- Universal Statistical Simulator by Mark Carney & Ben Varcoe [https://arxiv.org/abs/2202.01735]
- Backgrond on Classical Galton Board (wikipedia)
- Note on Quantum Walks and Monte Carlo Sampling [https://www.thewiser.org/quantum-walks-monte-carlo]
