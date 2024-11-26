## Basics of spin operators
collapsed:: true
	- Spin operators $S_x$, $S_y$, $S_z$ \leftrightarrow Pauli matrices
	- If $H$ commutes with $S^2$ then $S^2 = S_x^2 +S_y^2 + S_z^2 = S(S + 1)$ is a conserved quantity
		- For spin 1/2 particle, $S^2 = 3/4$
			- This follows from Sx^2 = SxSx = 1/4*Id (and analogous for Sy and Sz)
		- Therefore one can also express: $S_x^2 +S_y^2 = S^2 - S_z^2$
		- Introducing the ladder operators $S^+=S^x+iS^y$ and $S^-=S^x-iS^y$, another equality can be derived:
			- $S^2 = S_x^2 +S_y^2 + S_z^2 = (S_+S_- +S_-S_+)/2 + S_z^2$
			  id:: 659ea081-fc83-43f8-a716-66551fc0c1c1
- ## Dipolar interaction
  collapsed:: true
	- Interaction of a dipole with the magnetic field created by another dipole at distance r:
	  $F = \mu_j \cdot \mu_k / r^4 \rightarrow U = \mu_j \cdot \mu_k / r^3$
	  [[@Distance Measurements in Biological Systems by EPR]]
	- In the general anisotropic case, the dot-product of the two vectors is 
	  $$U = \frac{\mu_k \cdot \mu_j}{r_{jk}^3} - 3 \frac{ (\mu_k \cdot r_{jk})(\mu_j \cdot r_{jk}) }{r^5}$$
	- Isotropic case:
	  $$U = \frac{\mu_k \cdot \mu_j}{r_{jk}^3} (1 - 3 \cos(\theta))$$
	  where $\theta$ is the angle between the external magnetic field and the distance vector of the two magnetic dipoles
		- For powder samples this gives the Pake pattern distribution
		- The dipolar interaction is described by the dipolar splitting $D = \mu_j \cdot \mu_k / r^3$
		- For the magic angle $\theta = 54.7^o$ the interaction is zero
		- Average over a sphere is zero
			- Fast rotating spins show no dipolar interaction
		- Assuming $g = 2 \rightarrow D = -2786/r^3$, where $r$ is in angstrom
			- $r = 20$ angstrom $\rightarrow D = 0.35$mT which is small compared to typical spin label linewidths
				- At $T = 80 K$ using pEPR one has $T_m \simeq 2 \mu$s which would correspond to spin packet linewidth of $3 \mu$T therefore pEPR has advantage for measuring lorger interspin distances
- ## Two spins Hamiltonian
	- We use the same convention as Zech
	- For two spins the Hamiltonian is $H = \omega_AS_{z, A} + \omega_BS_{z, B} + 2 S_A D S_B - 2JS_A\cdot S_B$)
		- Note that $S_z$ is the projection to $z$ due to $B = B_z$, while the dipolar coupling tensor is given by Dxx = Dyy = -dd/3, Dzz = 2/3 dd and dd = -3g\mu_B\mu_0/(8\pi r$^3$) and d = 1/3 D(3cos$^2$(\theta) - 1), and finally $JS_A\cdot S_B = J(S_{x,A}S_{x,B} + S_{y,A}S_{y,B} + S_{z,A}S_{z,B})$
		- The Hamiltonian in the coupled basis |+,+>, |+,- >, |-,+>, |-,- > using ((659ea081-fc83-43f8-a716-66551fc0c1c1)) is given by:
			- |$(\omega_A + \omega_B)/2 - J/2$|0|0|0|
			  |--|--|--|--|
			  |0|$(\omega_1 - \omega+2)/2 - J/4$|$J/2$|0|
			  |0|$J/2$|$(-\omega_1 + \omega+2)/2 - J/4$|0|
			  |0|0|0`|$(-\omega_1 - \omega+2)/2 + J/4$|
		- It is diagonal in the triplet-singlet representation with quantum numbers |S_{tot}, m> with |S_{tot}> $= 1, 0$ for triplet and singlet respectively
			- The eigenbase is |T_{+}> = |+,+>, |T_{0}>, |S_{0}>, |T_{-} > = |-,- > and can be obtained from the product basis with a rotation dependent on $J$
- ## Product operators
	-