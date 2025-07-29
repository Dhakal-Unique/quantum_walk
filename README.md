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
