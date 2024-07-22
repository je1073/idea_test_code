# iDEA-masterclass

## Introduction to the repository
This is the repository of my work done in my Summer 2024 physics masterclass working on the iDEA code, supervised by Dr. Matt Hodgson.

All the work was done myself, Jamie Edwards.

The code is contained in a mixture of Jupiter notebooks and python files, which should return the achived results if ran.

## The project

The project had 3 main aims:

1) Prove correlation by iDEA to the analytical solution for a single particle time evolution of a quantum harmonic oscillator system for the ground state.
2) Make tests, using pytest, to allow potential future updates in the code to be shown to correlate.
3) Automate those test’s for push requests on GitHub.

iDEA is an open source Python software available on github that uses an interacting Dynamic Electrons Approach to solve multi-particle quantum mechanics for electrons in matter. It does this by working in 1D and solving the problem using exact methods.

## The system

The Quantum Harmonic oscillator in 1D has been defined as :
```latex
v(x,t) = 
\begin{cases} 
\frac{1}{2} \omega^2 x^2 + \epsilon x & \text{if } t \leq 0 \\ 
\frac{1}{2} \omega^2 x^2 & \text{if } t > 0 
\end{cases}


