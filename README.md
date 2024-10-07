# iDEA-masterclass

## Introduction to the repository
This is the repository of my work done in my Summer 2024 physics masterclass working on the iDEA code, supervised by Dr. Matt Hodgson.

All the work was done myself, James (Jamie) Edwards.

The code is conatined in two python files, one which contains the code to run anaylyis, the other to run the check of any updates to iDEA. If ran they should return the achived results.

Also contained is the presentation I performed to the approximately 10 academics of the group I was in, performed after 2 weeks of the project. Alongside this is a recording of my presentation.

## The project

The project had 3 main aims:

1) Prove correlation by iDEA to the analytical solution for a single particle time evolution of a quantum harmonic oscillator system for the ground state.
2) Make tests, using pytest, to allow potential future updates in the code to be shown to correlate.
3) Automate those test’s for push requests on GitHub.

iDEA is an open source Python software available on github that uses an interacting Dynamic Electrons Approach to solve multi-particle quantum mechanics for electrons in matter. It does this by working in 1D and solving the problem using exact methods.

# Main Findings

I found that iDEA correlates very well with the analytical solution for Quantum Harmonic oscillators of up to an order of 5. The differnece between the analytical solution for density and the iDEA prediction was of order e-12, and followed expected trends with respect to large time periods, up to 50 seconds. The energy of the system was found to remain constant, to a level also less than e-12.

### Time depenant increases

The point-wise difference between the analytical solution and iDEA was found to increase linearly with time, after 50 seconds of one evolution of a fully converged system the error had inceased from 0 to 3e-12. The energy of the system was found to remain constant, as expected. A small, less than e-12 error, was found for a fully converged system, however this was due to numerical noise rather than problem with iDEA code.

### Analytical terms

I found that approximately 17 terms were required in the analytical solution for it to be converged, at this number of terms the correlations were of the order e-12. Any less terms than 17 and it appeared the differences between iDEA and the analytical solution were due to the truncated analytical solution, rather than iDEA. Beyond 17 terms in the solution the differences between iDEA and the analytical didn't reduce, and the analytical solution stayed virtually the same, suggesting convergence in analytical terms had been found.

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

I showed that the intergral difference between iDEA and the solution was always less than e-12, and often was lower up to e-14, for a system of lengh 40 over time of 50 seconds. The ground state solution can be seen in figure one, with two measures of difference between the analytical solution and iDEA in figures 2 and 3. It can be seen that for both measures of difference are very small, of order e-12 or less, suggesting very good corillation.

The intergral difference, that is the intergrated difference between the density functions, remains relatively constant over the runtime, with small fluctuations, of order e-15, attributated due to numerical noise. The difference, calculated as the pointwise difference, between the two functions increases over the run time in a linear fashion. These results were took to suggest that the two systems arn't exactly evolving together with time with one oscillating slighty faster than the other. Because the functions are both correct in shape, just are slightly offset, the intergral difference dozen't capture this difference, as the erros always cancel out. The pointwise diffrence does cature these very small diffrences hense the linear increase. However given the small scale of the increase 2.5e-12 over the 50 second run it was concidered to be insignificant for most caculations but could be releveant for exceptionaly long calculations.

## Terms to check and prove convergence of system

There were a number of terms that I checked for convergence. The main 3 were; x step sise, timestep sise and number of anytical terms in analytic solution. I also checked the sise of system in x, checking for edge effects, omega and field strengh as well as the runtime.

### Convergence in dx

The convergence of the system with respect to dx was investigated. It was found that the system only became converged to an accatable level beyond 200 terms, that is a dx of 0.2 for the system, to achive the nececarry precision. Beyond 400 terms, a dx of 0.1, there was very little gain in accuracy but significant increases in runtime, therefore a dx of 0.1 was chosen. This is seen in figure 4 and 5. The significant drop off in return of increasing accuracy in term for increasing runtime can be seen in figure 6, this figure best illistrats why a dx of 0.1 was chosen, as the diminihsing returns are very stark.

In figure 5 the decreasing returns, and actually reduction in accuracy can be seen. Beyond 600 terms, a dx of 0.067, the accuracy actually increases slightly with more terms. This is due to numerical noise, it can also be seen that the shape of the plots changes at N=600, lickley due to numerical noise being the new most significant source of error rather than an unconverged term in the system.

The effect of changing dx on runtime was investigated, as seen in figure 7. A roughly linear realtionship can be seen,in figure 7, as expected. This sugested the system was behaving well and gave confidence the convergence was working.

### Convergence in dt

The convergence of dt was investgated. As can be seen in figure 8 the system dispayed a very simlar trend in the convergance to dx, that is converging quite rapidly up to about a dt of 0.1 and then very limited returns after that. Figure 9 shows how the number of timesteps impacted the intergarl diffrence over time for a otherwise fully converged system. It can be seen that at specific points the overall intergral diffrence reduced to a local minimum, this was attriputed two the two evolutions evolving at very slightly diffrent rates. The diffrence in the positions of these local minima coraspond to the frequency of the system, this suggested that it was due to the two evolutions becoming overlapped as they pass back over each other due to turning at the edge of the system.

A linear realtionship can be seen, in figure 10, for the effect of changing dx on runtime. Like for dx this sugested the system was behaving well and gave confidence the convergence was working.

### Convergence in number of analytical terms

The number of analytical terms in the solution was found to have a signficant effect on the diffrence between the iDEA solution and the analytical solution. This meant that while not relevant for the iDEA code as a whole, as there are very few analytical solutions to quantum problems, it did have a significant effect on the testing.

It was found, as seen in figure 11, that increasing the number of terms in the anlytical solution significantly reduced the intergral diffrence. To achive the level of accuracy wanted, that is less than e-12, at least 17 terms were required. Also to note the periodicity seen and discussed previosly can again be seen here. Beyond 19 terms there was very little increase in the accuracy but significant increases in runtime, this can be seen in figures 12 and 13. It was because of these significant increases in runtime that 17 terms was the chosen number of terms to use.

The shape of the plots was also investigated. It was found, as can be seen in figure 14 that the peaks have a linear fit. This is expected as numerical noise is relevant at these small values and so this linear increase with time is to be expected.

### Additional findings

It was found that the energy of the system remains constant too. This can be seen in figure 15. There is an oscillation in energy with periodicity equal to that of the evolving wavefunction, but as it is of order e-16 it is considered to be constant as this is less than machine prescison. 

It was also found that this correlation in the ground state was also true for all states up to t=5. These plots and correlations can be seen in figures 16, 17, 18 and 19. 

The plots of intergral difference and difference for the first exciteted state are shown in figures 20 and 21. Comparing them to figures 2 and 3 it can be seen they have similar shapes suggesting that the analysis completed for the ground state also applies to the first excited states. Similar plots were produced for the higher states also.

### Completed test

The completed test code, test_time_evolution_final, can be found attached as a file. This uses pytest to check new updates to iDEA against the analytic solution within a tolerance. The tollarances are set at 5e-13 for the density test and wavefunction at 1e-7, however these are easily changeable within the code. The tests check for numerical accuracy with the observales of density and wavefunction.

## Conclusion

In conclusion I proved that iDEA correlates very well with the analytical solution for Quantum Harmonic oscillator system of up to an order of 5. 

The difference between the analytical solution for density and the iDEA prediction was found to be of order e-12. The solution also followed expected trends with respect to runtime and convergence suggesting that the findings are as predicited.

The tests work well to test against the analytical solution for this system and should work well for tests. 










