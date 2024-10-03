# iDEA-masterclass

## Introduction to the repository
This is the repository of my work done in my Summer 2024 physics masterclass working on the iDEA code, supervised by Dr. Matt Hodgson.

All the work was done myself, Jamie Edwards.

The code is contained in a mixture of Jupiter notebooks and python files, which should return the achived results if ran.

Also contained is the presentation I performed to the approximately 10 academics of the group I was in, performed after 2 weeks of the project. Alongside this is a recording of my presentation.

## The project

The project had 3 main aims:

1) Prove correlation by iDEA to the analytical solution for a single particle time evolution of a quantum harmonic oscillator system for the ground state.
2) Make tests, using pytest, to allow potential future updates in the code to be shown to correlate.
3) Automate those test’s for push requests on GitHub.

iDEA is an open source Python software available on github that uses an interacting Dynamic Electrons Approach to solve multi-particle quantum mechanics for electrons in matter. It does this by working in 1D and solving the problem using exact methods.

# Main Findings

I found that iDEA correlates very well with the analytical solution for Quantum Harmonic oscillators of up to an order of 10. The differnece between the analytical solution for density and the iDEA prediction was of order e-12, and followed expected trends with respect to large time periods, up to 50 seconds. The energy of the system was found to remain constant, to a level also less than e-12.

### Time depenant increases

The point-wise difference between the analytical solution and iDEA was found to increase linearly with time, after 50 seconds of one evolution of a fully converged system the error had inceased from 0 to 3e-12. The energy of the system was found to remain constant, as expected. A small, less than e-12 error, was found for a fully converged system, however this was due to numerical noise rather than problem with iDEA code.

### Analytical terms

I found that approximately 17 terms were required in the analytical solution for it to be converged, at this number of terms the correlations were of the order e-12. Any less terms than 17 and it appeared the differences between iDEA and the analytical solution were due to the truncated analytical solution, not iDEA. Beyond 17 terms in the solution the differences between iDEA and the analytical didn't reduce, and the analytical solution stayed virtually the same, suggesting convergence in analytical terms had been found.

### Convergence

The system was converged with respect to both timesteps and steps in x, this being a 1D system. I found that steps of 0.1 in both x and t were the best compromise between commutation time and accuracy with these values being fully converged for the system studied, with runs conduced with values of step less than this having no meaningful increase in accuracy and significant increases in computation time.

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

The final system suddied was of lengh 40 with a dx of 0.1 used, 400 steps. The system was studied up to 50 seconds to ensure stability, and as already discussed a dt of 0.1 was used. The code is fully able to support alternative sised systems and sises of dx and dt.

The system used an omega value of 0.25 throughout, although is able to also be easily changed if required, and a field strengh of 0.1. 

# Findings

The projects main aim was to prove the correlation of iDEA for a single particle time evolution of a quantum harmonic oscillator system for the ground state with the know analytical solution and then produce a test for this to run on git hub. Both these aims were achived as I will explain bellow.

## Correlation with analytical solution

I showed that the intergral difference between iDEA and the solution was always less than e-12, and often was lower up to e-14, for a system of lengh 40 over time of 50 seconds. The ground state solution can be seen in attachment one, with the difference between the analytical solution and iDEA in attachmnet 2. It can be seen that for both measures of difference are very small suggesting very good corillation.

The intergral difference, that is the intergrated difference between the density functions, remains relatively constant over the runtime, with small fluctuations, of order e-15, due to numerical noise. The difference, calculated as the pointwise difference, between the two functions increases over the run time in a linear fashion. These results were took to suggest that the two systems arn't exactly evolving together with time with one oscillating slighty faster than the other. Because the functions are both correct in shape, just are slightly offset, the intergral difference dozen't capture this difference, as the erros cancel out.

## Terms to check and prove convergence of system

There were a number of terms that I checked for convergence. The main 3 turned out to be ; timestep sise, x step sise and umber of anytical terms in analytical solution. I also checked the sise of system in x, checking for edge effects, the impact of the chosen terms, omega and field strengh as well as the runtime.

## Convergence in number of analytical terms

## Convergence in dt

## Convergence in dx

## Immpact of other terms

## Extra findings

It was also found that this correlation in the ground state was also true for all states up to t=10.

# Method and timeline of investigations

### This sections contains a short summary of how my project developed, both as a record and so any future iDEA uses can learn from my mistakes









