# iDEA-masterclass

## Introduction to the repository
This is the repository of my work done in my Summer 2024 physics masterclass working on the iDEA code, supervised by Dr. Matt Hodgson.

All the work was done myself, Jamie Edwards.

The code is contained in a mixture of Jupiter notebooks and python files, which should return the achived results if ran.

Also contained is the presentation I performed to the approximately 10 academics of the group I was in, performed after 2 weeks of the project. Alongside this is a recording of my presentation.
I performed the presentation far faster than I would normally, but did this as a concious decision as I only began the 15 minute plus questions 5 minutes before the meeting was due to end.

## The project

The project had 3 main aims:

1) Prove correlation by iDEA to the analytical solution for a single particle time evolution of a quantum harmonic oscillator system for the ground state.
2) Make tests, using pytest, to allow potential future updates in the code to be shown to correlate.
3) Automate those test’s for push requests on GitHub.

iDEA is an open source Python software available on github that uses an interacting Dynamic Electrons Approach to solve multi-particle quantum mechanics for electrons in matter. It does this by working in 1D and solving the problem using exact methods.

## The system

The Quantum Harmonic oscillator in 1D has been defined as :
```math
v(x,t) = 
\begin{cases} 
\frac{1}{2} \omega^2 x^2 + \epsilon x & \text{if } t \leq 0 \\ 
\frac{1}{2} \omega^2 x^2 & \text{if } t > 0 
\end{cases}
```

This means that when a perturbating field is applied the potential and therefore the resultant wavfunction, and it's derivatives which is what I was actually interested in, will shift. It is due to the  application of this field that the system has a time depandance and ossliates. This is effect is shown in picture 1, from Hodgson, M. J. P. (2021). 'Analytic solution to the time-dependent Schrödinger equation for the one-dimensional quantum harmonic oscillator with an applied uniform field.'

# Main Findings

I found that iDEA correlates very well with the analytical solution for Quantum Harmonic oscillators of up to and order of 10. The diffrnece between the analytical solution for density and the iDEA prediction was of order e-12, and followed expected trends with respect to large time periods, up to 50 seconds. The energy of the system was found to remain constant, to a level also less than e-12.


### Time depenant increases

The point-wise difference between the analytical solution and iDEA was found to increase linearly with time, after 50 seconds of one evolution of a fully converged system the error had inceased from 0 to 3e-12. The energy of the system was found to remain constant, as expected. A small, less than e-12 error, was found for a fully converged system, however this was due to numerical noise rather than problem with iDEA code.

### Analytical terms

I found that approximately 17 terms were required in the analytical solution for it to be converged, at this number of terms the correlations were of the order e-12. Any less terms than 17 and it appeared the differences between iDEA and the analytical solution were due to the truncated analytical solution, not iDEA. Beyond 17 terms in the solution the differences between iDEA and the analytical didn't reduce, and the analytical solution stayed virtually the same, suggesting convergence in analytical terms had been found.

### Convergence

The system was converged with respect to both timesteps and steps in x, this being a 1D system. It was found that steps of were needed for the systems to be converged.









