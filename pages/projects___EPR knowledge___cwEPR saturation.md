## Fitting the saturation curve
	- According to [[@EPR Spectroscopy: Fundamentals and Methods]] page 9
		- $$ I_{pp} \propto \frac{\sqrt{P}}{(1 + P/P_{1/2})^{b/2}}$$
			- where $P_{1/2}$ is the power such that the saturation factor S is equal to 1/2
				- $$ S = \frac{1}{1 + \gamma^2 B_1^2 T_1 T_2} = 1/2 \Rightarrow \gamma^2 B_1^2 T_1 T_2 = 1$$
			- where $1 < b < 3$, $b = 1$ inhomogeneous line, $b = 3$ homogeneous line
		- Where does this $P_{1/2}$ actually lie in the saturation curve?
			- Taking the derivative of the saturation formula we obtain a relation between $P_{1/2}$ and $P^*$, where $P^*$ is the power at which we have the maximum of the saturation curve
				- Derivative:
					- $$\frac{d}{dP}I_{pp} = \frac{P_{1/2} - (b - 1)P}{2 P_{1/2} \sqrt{P} (P/P_{1/2})^{-b/2 - 1}}$$
				- Setting this equal to zero for $P = P^*$:
					- $$(b - 1)P^* = P_{1/2}$$
						- Or $$(b - 2^{2/b} + 1)P^* = P_{1/2}$$ if the term $(2^{2/b} - 1)$ is taken into consideration
				- $P^* \rightarrow \infty$ for $b = 1$
				  $P^* = P_{1/2}$ for $b = 2$
				  $P^*$ corresponds to the power at which $S = 2/3$ for $b = 3$
			- ![pOneHalf_satCurve_new_new.png](../assets/pOneHalf_satCurve_new_new_1707140475260_0.png)
				- $P_{1/2}$ can be larger or smaller than $P^*$ depending on the value of $b$
	- BUT according to the same book at page 296
		- $$ I_{pp} \propto \frac{\sqrt{P}}{(1 + (2^{2/b} - 1)P/P_{1/2})^{b/2}}$$
		- Why does the term $(2^{2/b} - 1)$ appear?
		  id:: 65c0bc02-0aff-4a84-b417-a8d71d8ec5f4
			- It appears because the definition of $P_{1/2}$ is different: here $P_{1/2}$ is the power at which the intensity is half of what it would have been if there were no saturation
				- See [[@ESR spectroscopy in membrane biophysics]] page 141
				- Also [[@Quantitative EPR]], [[@Electron Paramagnetic Resonance: A Practitioner’s Toolkit]] and [[@Quantitative studies of free radicals in biology: Corrections to ESR saturation data]] state that $P_{1/2}$ is the power at which the intensity is half of what it would be if there had not been saturation
		- [[@Electron spin relaxation of iron-sulphur proteins studied by microwave power saturation]] shows the saturation curve in a nice way, i.e. plotting $I_{pp}/\sqrt{P}$ vs $P$ in a loglog plot
			- Advantage of this: the curve is a constant in the linear regime and deviates from it when saturation starts
			- [[@Electron Paramagnetic Resonance: A Practitioner’s Toolkit]] use the same plots and define $P_{1/2}$ as the value at which the normalized intensity is half
				- This is coherent with the definition of power at which the intensity is half of what it would have been if there were no saturation
				- ![pOneHalf_satCurveNorm.png](../assets/pOneHalf_satCurveNorm_1707152157562_0.png){:height 500, :width 656}
					- All these curves with different $b$ values have the same $P_{1/2}$ and they cross at that value
	- These curves are the same for $b = 2$ because in that case the definitions of the $P_{1/2}$ coincide
	- The case $b = 3$ corresponds to the case of Bloch equations:
		- $$ M_y = M_0 \frac{\nu_1 T_2}{1 + (\nu_0 - \nu_1)^2 T_2^2 + \nu_1^2 T_1 T_2}$$
		- For the derivative spectrum, one has to consider the value of the derivate of the previous expression at frequency such that $\nu_0 - \nu = 1/2 \Delta \nu_{pp}$, where $\Delta \nu_{pp}$ is the distance between the peaks of the derivative spectrum in frequency
			- One obtains $I_{pp} \propto \sqrt{P} S^{-3/2}$
			- See [[@Electron spin resonance: a comprehensive treatise on experimental techniques]] page 590 and [[@ESR spectroscopy in membrane biophysics]] page 141