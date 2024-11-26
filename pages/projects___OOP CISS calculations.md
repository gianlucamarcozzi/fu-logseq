type:: project

- ## Project plan
  collapsed:: true
	- DONE Apply a general rotation to the initial state
	  id:: 65ae899c-4d92-493a-b433-ba2bbc651370
	  category:: [[Simulations]]
	  project:: [[projects/OOP CISS calculations]]
	- DONE Echo intensity for singlet and triplets, up down and down up
	  id:: 65b0ee16-7572-4352-a549-c2de328f9c7f
	  category:: [[Simulations]]
	  project:: [[projects/OOP CISS calculations]]
	- DONE Divide pre-beta-pulse and post-beta-pulse script
	  category:: [[Simulations]]
	  project:: [[projects/OOP CISS calculations]]
	  id:: 65ae89d2-a4ff-4d06-a399-b8525ca1f30c
	- DONE Calculate OOP for every basis operator couple
	  id:: 65ba84c2-145e-4c40-bce6-c5cc0875d43f
	  category:: [[Simulations]]
	  project:: [[projects/OOP CISS calculations]]
	- DONE Apply rotation to initial state and average
	  id:: 65ae8a33-2658-4a6b-b312-8a305919ad99
	  category:: [[Simulations]]
	  project:: [[projects/OOP CISS calculations]]
	- DONE Write notes on initial rotation and integral
	  category:: [[Reflection]]
	  project:: [[projects/OOP CISS calculations]]
	  id:: 65bd2137-4cce-48d7-8aa4-a0b94bcc8dfe
- ## OOP echo simulations for singlet and triplet states
  id:: 65b1041b-a3ea-48c9-957a-75a935e6bff7
  collapsed:: true
	- Pulse sequence: flashlight - T - \beta_{x} - \tau - \pi - \tau -echo
	- Notation of spin operators: Spq = 2SpSq where p, q = x, y, z
	- Regarding up, down and down, up density matrices:
	  collapsed:: true
		- It is not possible to easily calculate the signal for the (up, down) state applying:
		  collapsed:: true
		  signal_{ud} = 1/$\sqrt{2}$ [ signal_{S0} + signal_{T0} ]
			- It does not work becuase \sigma$_{ud} \neq$ 1/$\sqrt{2}$ [ \sigma$_{S0}$ + \sigma$_{T0}$ ]
		- Since \sigma$_{ud}$ = propagator[ \sigma$_{S0}$, Sxy - Syx, -\pi/4] one could think of just rotating the final matrix after all the calculations before taking the trace
			- Also this does not work because the rotation to bring \sigma$_{S0}$ to \sigma$_{ud}$ does not commute with the Hamiltonian and the pulse along the x-axis, therefore:
			  OOP-sequence[ \sigma$_{ud}$ ] = OOP-sequence[ propagator[ \sigma$_{S0}$, Sxy - Syx, -\pi/4] ]
			  $\neq$  propagator[ OOP-sequence[\sigma$_{S0}$], Sxy - Syx, -\pi/4]
	- Initial density matrices:
		- \sigma_{T+} has only a 1 as (1, 1) element and 0 otherwise
			- \sigma_{T+} = (Szz + Sza + Szb)/2
		- \sigma_{T-} has only a 1 as (4, 4) element and 0 otherwise
			- \sigma_{T-} = (Szz - Sza - Szb)/2
		- \sigma_{T0} has only a 1/2 as (2, 2), (2, 3), (3, 2), (3,3) elements and 0 otherwise
			- \sigma_{T0} = (-Szz + Sxx + Syy)/2
		- \sigma_{S} has only a 1/2 as (2, 2) and (3, 3) elements, -1/2 as (2, 3) and (3, 2) elements and 0 otherwise
			- \sigma_{S0} = (-Szz - Sxx - Syy)/2
		- \sigma_{ud} has only 1 in the (2, 2) element
			- \sigma_{ud} = 1/2 [ - Szz + Sza - Szb ]
		- \sigma_{du} has only 1 in the (2, 2) element
			- \sigma_{du} = 1/2 [ - Szz - Sza + Szb ]
	- Hamiltonian:
		- H= \Omega$_{1}$ Sza + \Omega$_{2}$ Szb + (d -J) Szz - (d + 2J) (Sxx + Syy)/2
		- Can be diagonalized with a transformation using the operators \xi \cdot (Sxy - Syx)/2
			- \xi = arctan[(d + 2J) / (\Omega$_{1}$ - \Omega$_{2}$)]
		- In the eigenbasis: H =  \Omega$_{S}$ (Sza + Szb) + q (Sza - Szb) + (d - J) Szz
			- \Omega$_{S}$ = (\Omega$_{1}$ + \Omega$_{2}) / 2$
			- q = (\Omega$_{1}$ -  \Omega$_{2}$) cos(\xi) - sin(\xi) (d + 2J)/2
			- In this basis the coherence order is a constant of the motion during free evolution
	- Transformation to the rotating frame: the \Omega$_{S}$ (Sza + Szb) term goes to zero
	- Transformation to the eigenbasis of the Hamiltonian of the density matrices:
	  collapsed:: true
		- \sigma_{T+} is invariant under this rotation
		- \sigma_{T-} is invariant under this rotation
		- \sigma_{T0} = 1/2 [-Szz + (Sxx + Syy) cos(\xi) + (Sza - Szb) sin(\xi)]
		- \sigma_{S0} = 1/2 [-Szz - (Sxx + Syy) cos(\xi) - (Sza - Szb) sin(\xi)]
		- \sigma_{ud} = 1/2 [-Szz - (Sxx + Syy) sin(\xi) + (Sza - Szb) cos(\xi)]
		- \sigma_{du} = 1/2 [-Szz + (Sxx + Syy) sin(\xi) - (Sza - Szb) cos(\xi)]
	- Free evolution for time T:
		- Commutators between H and density matrices:
		  collapsed:: true
			- H has a Szz term and a (Sza - Szb) term
			- The density matrices in the eigenbasis have Szz, (Sza + Szb) and (Sxx + Syy) terms.
			- Regarding the Szz term:
				- [szz, sza + szb] = [szz, sxx + syy] = [szz, szz] = 0.
			- Regarding the (Sza - Szb) term:
				- For \sigma$_{T+}$ and \sigma$_{T-}$:
					- [sza - szb, sza + szb] = 0;
				- For \sigma$_{T0}$ and \sigma$_{S0}$:
					- [sza - szb, sxx + syy] = -2i (sxy - syx).
		- \sigma_{T+} is constant under free evolution
		- \sigma_{T-} is constant under free evolution
		- \sigma_{T0} = [-Szz + (Sza - Szb) sin(\xi)
		  $+$ cos(\xi) cos(2qT) (Sxx + Syy) 
		  $-$ cos(\xi) sin(2qT) (Sxy - Syx)]/2
		- \sigma_{S0} = [-Szz - (Sza - Szb) sin(\xi)
		  $-$ cos(\xi) cos(2qT) (Sxx + Syy) 
		  $+$ cos(\xi) sin(2qT) (Sxy - Syx)]/2
		- \sigma_{ud} = - 1/2 Szz + 1/2 (Sza - Szb) cos(\xi)
		  $-$ 1/2 sin(\xi) cos(2qT) (Sxx + Syy) 
		  $+$ 1/2 sin(\xi) sin(2qT) (Sxy - Syx)
		- \sigma_{du} = - 1/2 Szz - 1/2 (Sza - Szb) cos(\xi)
		  $+$ 1/2 sin(\xi) cos(2qT) (Sxx + Syy) 
		  $-$ 1/2 sin(\xi) sin(2qT) (Sxy - Syx)
	- Neglect the sinusoidal terms containing q (fast decaying):
		- \sigma_{T+} = (Szz + Sza + Szb)/2
		- \sigma_{T-} = (Szz - Sza - Szb)/2
		- \sigma_{T0} = 1/2 [-Szz + (Sza - Szb) sin(\xi)]
		- \sigma_{S0} = 1/2 [-Szz - (Sza - Szb) sin(\xi)]
		- \sigma_{ud} = - 1/2 Szz + 1/2 (Sza - Szb) cos(\xi)
		- \sigma_{du} = - 1/2 Szz - 1/2 (Sza - Szb) cos(\xi)
	- Microwave pulse with flip angle \beta along x-axis
		- Bring the density matrix back to the product basis:
		  collapsed:: true
			- Commutator [- (Sxy - Syx), Sza - Szb] = 2i (Sxx + Syy)
			- No change: \sigma_{T+} = (Szz + Sza + Szb)/2
			- No change: \sigma_{T-} = (Szz - Sza - Szb)/2
			- \sigma_{T0} = {-Szz + sin(\xi) [cos(\xi) (Sza - Szb) + sin(\xi) (Sxx + Syy)]} / 2
				- \sigma_{T0} = -Szz/2 + 1/4 \cdot sin(2\xi) (Sza - Szb) + 1/2 \cdot sin$^2$(\xi) (Sxx + Syy)
			- \sigma_{S0} = -Szz/2 - 1/4 sin(2\xi) (Sza - Szb) - 1/2 sin$^2$(\xi) (Sxx + Syy)
			- \sigma_{ud} = -Szz/2 + 1/2 \cdot cos$^2$(\xi) (Sza - Szb) + 1/4 \cdot sin(2\xi) (Sxx + Syy)
			- \sigma_{du} = -Szz/2 - 1/2 \cdot cos$^2$(\xi) (Sza - Szb) - 1/4 \cdot sin(2\xi) (Sxx + Syy)
		- Apply mw pulse \beta
			- Commutators:
			  collapsed:: true
				- [Sxa + Sxb, Szz] = -i (Syz + Szy)
				- For \sigma$_{T+}$ and \sigma$_{T-}$: [Sxa + Sxb, Sza + Szb] = -i (Sya + Syb)
				- For \sigma$_{T0}$ and \sigma$_{S0}$
					- [Sxa + Sxb, Sza - Szb] = -i (Sya - Syb)
					- [Sxa + Sxb, Sxx] = 0
					- [Sxa + Sxb,  Syy] = i (Syz + Szy)
			- \sigma_{T+} =
				- $+$ 1/2 \cdot cos$^2$(\beta) Szz
				  $+$ 1/2 \cdot sin$^2$(\beta) Syy
				  $-$ 1/4 \cdot sin(2\beta) (Syz + Szy)
				- $+$ 1/2 \cdot cos(\beta) (Sza + Szb)
				  $-$ 1/2 \cdot sin(\beta) (Sya + Syb)
			- \sigma_{T-} =
			  collapsed:: true
				- $+$ 1/2 \cdot cos$^2$(\beta) Szz
				  $+$ 1/2 \cdot sin$^2$(\beta) Syy
				  $-$ 1/4 \cdot sin(2\beta) (Syz + Szy)
				- $-$ 1/2 \cdot cos(\beta) (Sza + Szb)
				  $+$ 1/2 \cdot sin(\beta) (Sya + Syb)
			- \sigma_{T0} = {-cos$^2$(\beta) Szz - sin$^2$(\beta) Syy + sin(2\beta)(Syz + Szy)} / 4
			  collapsed:: true
			  $+$ sin(2ξ) [ cos(\beta) (Sza - Szb) - sin(\beta) (Sya - Syb) ]  / 4
			  $+$ sin$^2$(ξ) Sxx / 2
			  $+$ sin$^2$(\xi) [sin$^2$(\beta) Szz + cos$^2$(\beta) Syy + sin(2\beta) (Syz + Szy) / 4
				- \sigma_{T0} =
					- $+$ 1/2 (-cos$^2$(\beta) + sin$^2$(\xi) sin$^2$(\beta) ) Szz
					  $+$ 1/2 ( -sin$^2$(\beta) + sin$^2$(\xi) cos$^2$(\beta) ) Syy
					  $+$ 1/4 sin(2\beta) (1 + sin^2(\xi) ) (Syz + Szy)
					  $+$ 1/4 cos(\beta) sin(2ξ) (Sza - Szb)
					  $-$ 1/4 sin(\beta) sin(2\xi) (Sya - Syb)
					  $+$ 1/2 sin$^2$(ξ) Sxx
			- \sigma_{S0} = - 1/2 cos$^2$(\beta) Szz - 1/2 sin$^2$(\beta) Syy + 1/4 sin(2\beta)(Syz + Szy)
			  collapsed:: true
			  $-$ sin(2ξ) [ cos(\beta) (Sza - Szb) - sin(\beta) (Sya - Syb) ]  / 4
			  $-$ sin$^2$(ξ) Sxx / 2
			  $-$ sin$^2$(\xi) [sin$^2$(\beta) Szz + cos$^2$(\beta) Syy + sin(2\beta) (Syz + Szy) / 4
				- \sigma_{S0} =
					- $+$ 1/2 (-cos$^2$(\beta) - sin$^2$(\xi) sin$^2$(\beta) ) Szz
					  $+$ 1/2 ( -sin$^2$(\beta) - sin$^2$(\xi) cos$^2$(\beta) ) Syy
					  $+$ 1/4 sin(2\beta) (1 - sin^2(\xi) ) (Syz + Szy)]
					  $-$ 1/4 cos(\beta)sin(2ξ)  (Sza - Szb)
					  $+$ 1/4 sin(\beta)sin(2ξ) (Sya - Syb)
					  $+$ 1/4 sin(2ξ) Sxx
			- \sigma_{ud}
			  collapsed:: true
				- $+$ 1/2 [ - cos$^2$(\beta) + 1/2 sin$^2$(\beta) sin(2\xi) ] Szz
				  $+$ 1/2 [ - sin$^2$(\beta) + 1/2 cos$^2$(\beta) sin(2\xi) ] Syy
				  $+$ 1/4 sin(2\beta) [ 1 + 1/2 sin(2\xi) ] (Syz + Szy)
				  $+$ 1/2 cos(\beta) cos$^2$(ξ) (Sza - Szb)
				  $-$ 1/2 sin(\beta) cos$^2$(\xi) (Sya - Syb)
				  $+$ 1/4 sin(2ξ) Sxx
			- \sigma_{du}
			  collapsed:: true
				- $+$ 1/2 [ - cos$^2$(\beta) - 1/2 sin$^2$(\beta) sin(2\xi) ] Szz
				  $+$ 1/2 [ - sin$^2$(\beta) - 1/2 cos$^2$(\beta) sin(2\xi) ] Syy
				  $+$ 1/4 sin(2\beta) [ 1 - 1/2 sin(2\xi) ] (Syz + Szy)
				  $-$ 1/2 cos(\beta) cos$^2$(ξ) (Sza - Szb)
				  $+$ 1/2 sin(\beta) cos$^2$(\xi) (Sya - Syb)
				  $-$ 1/4 sin(2ξ) Sxx
		- Transform again to the eigenbasis:
			- Commutators for \sigma$_{T+}$ and \sigma$_{T-}$:
			  collapsed:: true
				- Szz commutes with Sxy - Syx
				- propagator[Syy, Sxy - Syx, \xi/2] = cos^2(\xi/2) Syy - sin^2(\xi/2) Sxx + 1/2\cdot sin(\xi) (Sza - Szb)
				- propagator[Syz + Szy, Sxy - Syx, \xi/2] = cos(\xi/2) (Syz + Szy) - sin(\xi/2) (Sya - Syb)
				- Sza + Szb commutes
				- propagator[Sya + Syb, Sxy - Syx, \xi/2] = = cos(\xi/2) (Sya - Syb) - sin(\xi/2) (Syz - Szy)
			- Commutators for \sigma$_{T0}$ and \sigma$_{S0}$
			  collapsed:: true
				- propagator[Sza - Szb, Sxy - Syx, \xi/2] = (Sza - Szb) cos[\xi] - (Sxx + Syy) sin[\xi]
				- propagator[Sya - Syb, Sxy - Syx, \xi/2] = (Sya - Syb) cos[\xi/2] + (Syz + Szy) sin[\xi/2]
				- To check results with Bittl: focus only on Syz + Szy and Sya - Syb because they turn one into the other and thats all when applying this sxy - syx transormation
			- \sigma_{T+} =
				- $+$ 1/2\cdot cos$^2$(\beta) Szz
				  $+$ 1/2\cdot sin$^2$(\beta) cos$^2$(\xi/2) Syy
				  $-$ 1/2\cdot sin$^2$(\beta) sin$^2$(\xi/2) Sxx
				  $+$ 1/4\cdot sin$^2$(\beta) sin(\xi) (Sza - Szb)
				  $-$ 1/4\cdot sin(2\beta) cos(\xi/2) (Syz + Szy)
				  $+$ 1/4\cdot sin(2\beta) sin(\xi/2) (Sya - Syb)
				- $+$ 1/2\cdot cos(\beta) (Sza + Szb)
				  $-$ 1/2\cdot sin(\beta) cos(\xi/2) (Sya + Syb)
				  $+$ 1/2\cdot sin(\beta) sin(\xi/2) (Syz - Szy)
			- \sigma_{T-} =
				- $+$ 1/2\cdot cos$^2$(\beta) Szz
				  $+$ 1/2\cdot sin$^2$(\beta) cos$^2$(\xi/2) Syy
				  $-$ 1/2\cdot sin$^2$(\beta) sin$^2$(\xi/2) Sxx
				  $+$ 1/4\cdot sin$^2$(\beta) sin(\xi) (Sza - Szb)
				  $-$ 1/4\cdot sin(2\beta) cos(\xi/2) (Syz + Szy)
				  $+$ 1/4\cdot sin(2\beta) sin(\xi/2) (Sya - Syb)
				- $-$ 1/2\cdot cos(\beta) (Sza + Szb)
				  $+$ 1/2\cdot sin(\beta) cos(\xi/2) (Sya + Syb)
				  $-$ 1/2\cdot sin(\beta) sin(\xi/2) (Syz - Szy)
			- \sigma_{T0} =
				- 1/2\cdot [-cos$^2$(\beta) + sin$^2$(\beta)sin^2(\xi)] Szz
				  $+$ 1/2\cdot [- sin$^2$(\beta) + cos$^2$(\beta)sin$^2$(\xi)] cos$^2$(\xi/2) Syy
				  $-$ 1/2\cdot [- sin$^2$(\beta) + cos$^2$(\beta)sin$^2$(\xi)] sin$^2$(\xi/2) Sxx
				  $+$ 1/4\cdot [- sin$^2$(\beta) + cos$^2$(\beta)sin$^2$(\xi)]  sin(\xi) (Sza - Szb)
				  $+$ 1/4\cdot sin(2\beta) (1 + sin^2(\xi) ) cos(\xi/2) (Syz + Szy)
				  $-$ 1/4\cdot sin(2\beta) (1 + sin^2(\xi) ) sin(\xi/2) (Sya - Syb)
				  $+$ 1/4 \cdot sin(2ξ) cos(\beta) cos(\xi) (Sza - Szb)
				  $-$ 1/4 \cdot sin(2ξ) cos(\beta) sin(\xi) (Sxx + Syy)
				  $-$ 1/4 \cdot sin(2ξ) sin(\beta) cos(\xi/2) (Sya - Syb) 
				  $-$ 1/4 \cdot sin(2ξ) sin(\beta) sin(\xi/2) (Syz + Szy)
				  $+$ 1/2 sin$^2$(ξ) cos$^2$(\xi/2) Sxx
				  $-$ 1/2 sin$^2$(ξ) sin$^2$(\xi/2) Syy
				  $+$ 1/4 sin$^2$(ξ) sin(\xi) (Sza - Szb)
				- \sigma_{T0} =
					- $+$ 1/2\cdot [-cos$^2$(\beta) + sin$^2$(\beta)sin^2(\xi)] Szz
					  $+$ 1/2\cdot [- sin$^2$(\beta) cos$^2$(\xi/2) + cos$^2$(\beta)sin$^2$(\xi)cos$^2$(\xi/2) - sin$^2$(ξ) sin$^2$(\xi/2) - 1/2 \cdot cos(\beta) sin(\xi)sin(2ξ)] Syy
					  $+$ 1/2\cdot [sin$^2$(\beta)sin$^2$(\xi/2) - cos$^2$(\beta)sin$^2$(\xi)sin$^2$(\xi/2) + sin$^2$(ξ) cos$^2$(\xi/2) - 1/2 cos(\beta) sin(\xi)\cdot sin(2ξ)]  Sxx
					  $+$ 1/4\cdot [- sin$^2$(\beta)sin(\xi) + cos$^2$(\beta)sin$^3$(\xi) + sin$^3$(\xi) + cos(\beta)cos(\xi)sin(2ξ)]   (Sza - Szb)
					  $+$ 1/4 \cdot [sin(2\beta) (1 + sin^2(\xi) ) cos(\xi/2) - sin(\beta)sin(2ξ) sin(\xi/2)] (Syz + Szy)
					  $+$ 1/4\cdot [-sin(2\beta) (1 + sin^2(\xi) ) sin(\xi/2) - sin(\beta)sin(2ξ) cos(\xi/2)] (Sya - Syb)
			- \sigma_{S0} =
			  collapsed:: true
				- 1/2\cdot [-cos$^2$(\beta) - sin$^2$(\beta)sin^2(\xi)] Szz
				  $+$ 1/2\cdot [- sin$^2$(\beta) - cos$^2$(\beta)sin$^2$(\xi)] cos$^2$(\xi/2) Syy
				  $-$ 1/2\cdot [- sin$^2$(\beta) - cos$^2$(\beta)sin$^2$(\xi)]  sin$^2$(\xi/2) Sxx
				  $+$ 1/4\cdot [- sin$^2$(\beta) - cos$^2$(\beta)sin$^2$(\xi)]  sin(\xi) (Sza - Szb)
				  $+$ 1/4\cdot sin(2\beta) (1 - sin^2(\xi) ) cos(\xi/2) (Syz + Szy)
				  $-$ 1/4\cdot sin(2\beta) (1 - sin^2(\xi) ) sin(\xi/2) (Sya - Syb)
				  $-$ 1/4 \cdot sin(2ξ) cos(\beta) cos(\xi) (Sza - Szb) 
				  $+$ 1/4 \cdot sin(2ξ) cos(\beta) sin(\xi) (Sxx + Syy)
				  $+$ 1/4 \cdot sin(2ξ) sin(\beta) cos(\xi/2) (Sya - Syb) 
				  $+$ 1/4 \cdot sin(2ξ) sin(\beta) sin(\xi/2) (Syz + Szy)
				  $-$ 1/2 sin$^2$(ξ) cos$^2$(\xi/2) Sxx
				  $+$ 1/2 sin$^2$(ξ) sin$^2$(\xi/2) Syy
				  $-$ 1/4 sin$^2$(ξ) sin(\xi) (Sza - Szb)
				- \sigma_{S0} = 1/2\cdot [-cos$^2$(\beta) - sin$^2$(\beta)sin^2(\xi)] Szz
				  $+$ 1/2\cdot [- sin$^2$(\beta) cos$^2$(\xi/2) - cos$^2$(\beta)sin$^2$(\xi)cos$^2$(\xi/2) + sin$^2$(ξ) sin$^2$(\xi/2) + 1/2 \cdot cos(\beta) sin(\xi)sin(2ξ)] Syy
				  $+$ 1/2\cdot [sin$^2$(\beta)sin$^2$(\xi/2) + cos$^2$(\beta)sin$^2$(\xi)sin$^2$(\xi/2) - sin$^2$(ξ) cos$^2$(\xi/2) + 1/2 cos(\beta) sin(\xi)\cdot sin(2ξ)]  Sxx
				  $+$ 1/4\cdot [- sin$^2$(\beta)sin(\xi) - cos$^2$(\beta)sin$^3$(\xi) - sin$^3$(\xi) - cos(\beta)cos(\xi)sin(2ξ)]   (Sza - Szb)
				  $+$ 1/2\cdot [sin(2\beta) (1 - sin^2(\xi) ) cos(\xi/2) + 1/2\cdot sin(\beta)sin(2ξ) sin(\xi/2)] (Syz + Szy)
				  $+$ 1/2\cdot [-sin(2\beta) (1 - sin^2(\xi) ) sin(\xi/2) + 1/2 \cdot sin(\beta)sin(2ξ) cos(\xi/2)] (Sya - Syb)
			- \sigma_{ud} =
				- $+$ 1/2 [ - cos$^2$(\beta) + 1/2 sin$^2$(\beta) sin(2\xi) ] Szz
				  $+$ 1/2 [ - sin$^2$(\beta) + 1/2 cos$^2$(\beta) sin(2\xi) ] cos$^2$(\xi/2) Syy
				  $-$ 1/2 [ - sin$^2$(\beta) + 1/2 cos$^2$(\beta) sin(2\xi) ] sin$^2$(\xi/2) Sxx
				  $+$ 1/4 [ - sin$^2$(\beta) + 1/2 cos$^2$(\beta) sin(2\xi) ] sin(\xi) (Sza - Szb)
				- $+$ 1/4 sin(2\beta) [ 1 + 1/2 sin(2\xi) ] cos(\xi/2) (Syz + Szy)
				  $-$ 1/4 sin(2\beta) [ 1 + 1/2 sin(2\xi) ] sin(\xi/2) (Sya - Syb)
				- $+$ 1/2 cos(\beta) cos$^2$(ξ)cos(ξ) (Sza - Szb)
				  $-$ 1/2 cos(\beta) cos$^2$(ξ) sin(ξ) (Sxx + Syy)
				  $-$ 1/2 sin(\beta) cos$^2$(\xi) cos(ξ/2) (Sya - Syb)
				  $-$ 1/2 sin(\beta) cos$^2$(\xi) sin(ξ/2) (Syz + Szy)
				  $+$ 1/4 sin(2ξ) cos$^2$(\xi/2) Sxx
				  $-$ 1/4 sin(2ξ) sin$^2$(\xi/2) Syy
				  $+$ 1/8 sin(2ξ) sin(\xi) (Sza -Szb)
				- \sigma_{du}
					- $+$ 1/2 [ - cos$^2$(\beta) + 1/2 sin$^2$(\beta) sin(2\xi) ] Szz
					  $+$ 1/2 [ - sin$^2$(\beta) cos$^2$(\xi/2) + 1/2 cos$^2$(\beta) sin(2\xi)cos$^2$(\xi/2) - cos(\beta) cos$^2$(ξ) sin(ξ) - 1/2 sin(2ξ) sin$^2$(\xi/2) ]  Syy
					  $+$ 1/2 [ sin$^2$(\beta) sin$^2$(\xi/2) - 1/2 cos$^2$(\beta) sin(2\xi) sin$^2$(\xi/2) - cos(\beta) cos$^2$(ξ) sin(ξ) + 1/2 sin(2ξ) cos$^2$(\xi/2)]  Sxx
					  $+$ 1/2 [ - 1/2 sin$^2$(\beta) sin(\xi) + 1/4 cos$^2$(\beta) sin(2\xi) sin(\xi) + cos(\beta) cos$^2$(ξ)cos(ξ/2) + 1/4 sin(2ξ) sin(\xi)] (Sza - Szb)
					  $+$ 1/2 [ 1/2 sin(2\beta) [ 1 + 1/2 sin(2\xi) ] cos(\xi/2) - sin(\beta) cos$^2$(\xi) sin(ξ/2) ] (Syz + Szy)
					  $+$ 1/2 [ - 1/2 sin(2\beta) [ 1 + 1/2 sin(2\xi) ] sin(\xi/2) - sin(\beta) cos$^2$(\xi)cos(\xi/2) ] (Sya - Syb)
				- \sigma_{du}
					- $+$ 1/2 [ - cos$^2$(\beta) - 1/2 sin$^2$(\beta) sin(2\xi) ] Szz
					  $+$ 1/2 [ - sin$^2$(\beta) cos$^2$(\xi/2) - 1/2 cos$^2$(\beta) sin(2\xi)cos$^2$(\xi/2) + cos(\beta) cos$^2$(ξ) sin(ξ) + 1/2 sin(2ξ) sin$^2$(\xi/2) ]  Syy
					  $+$ 1/2 [ sin$^2$(\beta) sin$^2$(\xi/2) + 1/2 cos$^2$(\beta) sin(2\xi) sin$^2$(\xi/2) + cos(\beta) cos$^2$(ξ) sin(ξ) - 1/2 sin(2ξ) cos$^2$(\xi/2)]  Sxx
					  $+$ 1/2 [ - 1/2 sin$^2$(\beta) sin(\xi) + 1/4 cos$^2$(\beta) sin(2\xi) sin(\xi) + cos(\beta) cos$^2$(ξ)cos(ξ/2) - 1/4 sin(2ξ) sin(\xi)] (Sza - Szb)
					  $+$ 1/2 [ 1/2 sin(2\beta) [ 1 - 1/2 sin(2\xi) ] cos(\xi/2) + sin(\beta) cos$^2$(\xi) sin(ξ/2) ] (Syz + Szy)
					  $+$ 1/2 [ - 1/2 sin(2\beta) [ 1 - 1/2 sin(2\xi) ] sin(\xi/2) + sin(\beta) cos$^2$(\xi)cos(\xi/2) ] (Sya - Syb)
			- Compact results:
				- \sigma_{T+/-} =
				  collapsed:: true
					- $+$ 1/2\cdot cos$^2$(\beta) Szz
					  $+$ 1/2\cdot sin$^2$(\beta) cos$^2$(\xi/2) Syy
					  $-$ 1/2\cdot sin$^2$(\beta) sin$^2$(\xi/2) Sxx
					  $+$ 1/4\cdot sin$^2$(\beta) sin(\xi) (Sza - Szb)
					  $-$ 1/4\cdot sin(2\beta) cos(\xi/2) (Syz + Szy)
					  $+$ 1/4\cdot sin(2\beta) sin(\xi/2) (Sya - Syb)
					  $\pm$ 1/2\cdot cos(\beta) (Sza + Szb)
					  $\mp$ 1/2\cdot sin(\beta) cos(\xi/2) (Sya + Syb)
					  $\pm$ 1/2\cdot sin(\beta) sin(\xi/2) (Syz - Szy)
				- \sigma_{T0/S0} =
				  collapsed:: true
					- $+$ 1/2\cdot [-cos$^2$(\beta) \pm sin$^2$(\beta)sin^2(\xi)] Szz
					  $+$ 1/2\cdot [- sin$^2$(\beta) cos$^2$(\xi/2) \pm cos$^2$(\beta)sin$^2$(\xi)cos$^2$(\xi/2) $\mp$ sin$^2$(ξ) sin$^2$(\xi/2) $\mp$ 1/2 \cdot cos(\beta) sin(\xi)sin(2ξ)] Syy
					  $+$ 1/2\cdot [sin$^2$(\beta)sin$^2$(\xi/2) $\mp$ cos$^2$(\beta)sin$^2$(\xi)sin$^2$(\xi/2) \pm sin$^2$(ξ) cos$^2$(\xi/2) $\mp$ 1/2 cos(\beta) sin(\xi)\cdot sin(2ξ)]  Sxx
					  $+$ 1/4\cdot [- sin$^2$(\beta)sin(\xi) \pm cos$^2$(\beta)sin$^3$(\xi) \pm sin$^3$(\xi) \pm cos(\beta)cos(\xi)sin(2ξ)]   (Sza - Szb)
					  $+$ 1/4\cdot [sin(2\beta) (1 \pm sin^2(\xi) ) cos(\xi/2) $\mp$ sin(\beta)sin(2ξ) sin(\xi/2)] (Syz + Szy)
					  $+$ 1/4\cdot [-sin(2\beta) (1 \pm sin^2(\xi) ) sin(\xi/2) $\mp$ sin(\beta)sin(2ξ) cos(\xi/2)] (Sya - Syb)
		- Consider only single-quantum operators:
			- \sigma_{T+/-} =
			  $+$ 1/4\cdot sin(2\beta) sin(\xi/2) (Sya - Syb)
			  $-$ 1/4\cdot sin(2\beta) cos(\xi/2) (Syz + Szy)
			  $\mp$ 1/2\cdot sin(\beta) cos(\xi/2) (Sya + Syb)
			  $\pm$ 1/2\cdot sin(\beta) sin(\xi/2) (Syz - Szy)
			- \sigma_{T0/S0} =
			  $+$ 1/4\cdot [-sin(2\beta) (1 \pm sin^2(\xi) ) sin(\xi/2) $\mp$ sin(\beta)sin(2ξ) cos(\xi/2)] (Sya - Syb)
			  $+$ 1/4\cdot [sin(2\beta) (1 \pm sin^2(\xi) ) cos(\xi/2) $\mp$ sin(\beta)sin(2ξ) sin(\xi/2)] (Syz + Szy)
			- \sigma_{ud/du} +
			  $+$ 1/2 [ - 1/2 sin(2\beta) [ 1 \pm 1/2 sin(2\xi) ] sin(\xi/2) $\mp$ sin(\beta) cos$^2$(\xi)cos(\xi/2)  ] (Sya - Syb)
			  $+$ 1/2 [ 1/2 sin(2\beta) [ 1 \pm 1/2 sin(2\xi) ] cos(\xi/2) $\mp$ sin(\beta) cos$^2$(\xi) sin(ξ/2) ] (Syz + Szy)
		- \tau - \pi - \tau in pathways:
		  collapsed:: true
			- The sequence from now on includes: evolution \tau, transformation to product base, \pi pulse, transformation to eigenbasis, evolution \tau, transformation to product base, Tr[\sigma $\cdot$ (Sxa + Sxb)] and Tr[\sigma $\cdot$ (Sya + Syb)]
				- Note: the free evolutions must be calculated including the q(Sza - Szb) termi in the Hamiltonian. Neglecting the fast decaying terms including q must be done only at the end
			- We consider at the end only terms proportional to (Sxa + Sxb) or to (Sya + Syb) because the other terms will go to zero when the trace is taken
			- Sya - Syb pathway:
				- Coefficient of Sxa + Sxb:
					- $-$ cos(\xi) sin(\xi/2) sin(2dmJ)
					  $+$ cos$^2$(\xi/2) sin(\xi/2) sin(2dmJ) cos(2q) - sin(\xi) sin(\xi/2) cos(2dmJ) sin(2q)
				- Coefficient of Sya + Syb = 0
			- Syz + Szy pathway:
				- Coefficient of Sxa + Sxb
					- $-$ cos(\xi) cos(\xi/2) sin(2dmJ)
					  $-$ sin(\xi) sin(\xi/2) sin(2dmJ) cos(2q) $+$ 2 sin(\xi/2) cos$^2$(\xi/2) cos(2dmJ) sin(2q)
				- Coefficient of Sya + Syb = 0
			- Sya + Syb pathway:
				- Coefficient of Sxa + Sxb = 0
				- Coefficient of Sya + Syb
					- $-$ cos(\xi) cos(\xi/2) cos(2dmJ)
					  $-$ sin(\xi) sin(\xi/2) cos(2dmJ) cos(2q) - cos(\xi/2) sin(\xi) sin(2dmJ) sin(2q)
			- Syz + Szy pathway
				- Coefficient of Sxa + Sxb = 0
				- Coefficient of Sya + Syb
					- $-$ cos(\xi) sin(\xi/2) cos(2dmJ)
					  $+$ 2cos$^2$(\xi/2) sin(\xi/2) cos(2dmJ) cos(2q) + sin(\xi/2) sin(\xi) sin(2dmJ) sin(2q)
		- EPR signal
			- \sigma_{T+}
				- Sx = 1/2 sin(2(J - d)) cos(\xi) sin(2 \beta) sin$^2$(\xi/2)
				- Sy = cos(2(J - d)) cos$^2$(\xi)  sin(\beta)
			- \sigma_{T-}
				- Sx = 1/2 sin(2(J - d)) cos(\xi) sin(2 \beta) sin$^2$(\xi/2)
				- Sy = - cos(2(J - d)) cos$^2$(\xi)  sin(\beta)
			- \sigma_{T0}
				- Sx = sin(2(J - d)) [ -1/4 \cdot sin(\beta) sin$^2$(2\xi) +  1/2 \cdot sin(2\beta) cos$^2$(\xi) (1 + sin^2(\xi)) ]
				- Sy = 0
			- \sigma_{S0}
				- Sx = sin(2(J - d)) [ 1/4 \cdot sin(\beta) sin$^2$(2\xi) +  1/2 \cdot sin(2\beta) cos$^4$(\xi) ]
				- Sy = 0
- ## \tau - \pi - \tau in pathways:
  collapsed:: true
	- The sequence from now on includes: evolution \tau, transformation to product base, \pi pulse, transformation to eigenbasis, evolution \tau, transformation to product base, Tr[\sigma $\cdot$ (Sxa + Sxb)] and Tr[\sigma $\cdot$ (Sya + Syb)]
		- Note: the free evolutions must be calculated including the q(Sza - Szb) termi in the Hamiltonian. Neglecting the fast decaying terms including q must be done only at the end
	- We consider at the end only terms proportional to (Sxa + Sxb) or to (Sya + Syb) because the other terms will go to zero when the trace is taken
	- Sya - Syb pathway:
		- Coefficient of Sxa + Sxb:
			- $-$ cos(\xi) sin(\xi/2) sin(2dmJ)
			  $+$ cos$^2$(\xi/2) sin(\xi/2) sin(2dmJ) cos(2q) - sin(\xi) sin(\xi/2) cos(2dmJ) sin(2q)
		- Coefficient of Sya + Syb = 0
	- Syz + Szy pathway:
		- Coefficient of Sxa + Sxb
			- $-$ cos(\xi) cos(\xi/2) sin(2dmJ)
			  $-$ sin(\xi) sin(\xi/2) sin(2dmJ) cos(2q) $+$ 2 sin(\xi/2) cos$^2$(\xi/2) cos(2dmJ) sin(2q)
		- Coefficient of Sya + Syb = 0
	- Sya + Syb pathway:
		- Coefficient of Sxa + Sxb = 0
		- Coefficient of Sya + Syb
			- $-$ cos(\xi) cos(\xi/2) cos(2dmJ)
			  $-$ sin(\xi) sin(\xi/2) cos(2dmJ) cos(2q) - cos(\xi/2) sin(\xi) sin(2dmJ) sin(2q)
	- Syz - Szy pathway:
		- Coefficient of Sxa + Sxb = 0
		- Coefficient of Sya + Syb
			- $-$ cos(\xi) sin(\xi/2) cos(2dmJ)
			  $+$ 2cos$^2$(\xi/2) sin(\xi/2) cos(2dmJ) cos(2q) + sin(\xi/2) sin(\xi) sin(2dmJ) sin(2q)
	- Sxa - Sxb
		- Coefficient of Sxa + Sxb = 0
		- Coefficient of Sya + Syb
			- $-$ cos(\xi) sin(\xi/2) sin(2dmJ)
			  $-$ 2cos$^2$(\xi/2) sin(\xi/2) sin(2dmJ) cos(2q) - sin(\xi/2) sin(\xi) cos(2dmJ) sin(2q)
	- Sxz + Szx
		- Coefficient of Sxa + Sxb = 0
		- Coefficient of Sya + Syb
			- $-$ cos(\xi) cos(\xi/2) sin(2dmJ)
			  $+$ 2cos$^2$(\xi/2) sin(\xi/2) cos(2dmJ) sin(2q) - sin(\xi/2) sin(\xi) sin(2dmJ) cos(2q)
- ## OOP echo for operators
  collapsed:: true
	- \tau - \pi - \tau in pathways:
	  collapsed:: true
		- The sequence from now on includes: evolution \tau, transformation to product base, \pi pulse, transformation to eigenbasis, evolution \tau, transformation to product base, Tr[\sigma $\cdot$ (Sxa + Sxb)] and Tr[\sigma $\cdot$ (Sya + Syb)]
			- Note: the free evolutions must be calculated including the q(Sza - Szb) termi in the Hamiltonian. Neglecting the fast decaying terms including q must be done only at the end
		- We consider at the end only terms proportional to (Sxa + Sxb) or to (Sya + Syb) because the other terms will go to zero when the trace is taken
		- Sya - Syb pathway:
			- Coefficient of Sxa + Sxb:
				- $-$ cos(\xi) sin(\xi/2) sin(2dmJ)
				  $+$ cos$^2$(\xi/2) sin(\xi/2) sin(2dmJ) cos(2q) - sin(\xi) sin(\xi/2) cos(2dmJ) sin(2q)
			- Coefficient of Sya + Syb = 0
		- Syz + Szy pathway:
			- Coefficient of Sxa + Sxb
				- $-$ cos(\xi) cos(\xi/2) sin(2dmJ)
				  $-$ sin(\xi) sin(\xi/2) sin(2dmJ) cos(2q) $+$ 2 sin(\xi/2) cos$^2$(\xi/2) cos(2dmJ) sin(2q)
			- Coefficient of Sya + Syb = 0
		- Sya + Syb pathway:
			- Coefficient of Sxa + Sxb = 0
			- Coefficient of Sya + Syb
				- $-$ cos(\xi) cos(\xi/2) cos(2dmJ)
				  $-$ sin(\xi) sin(\xi/2) cos(2dmJ) cos(2q) - cos(\xi/2) sin(\xi) sin(2dmJ) sin(2q)
		- Syz + Szy pathway
			- Coefficient of Sxa + Sxb = 0
			- Coefficient of Sya + Syb
				- $-$ cos(\xi) sin(\xi/2) cos(2dmJ)
				  $+$ 2cos$^2$(\xi/2) sin(\xi/2) cos(2dmJ) cos(2q) + sin(\xi/2) sin(\xi) sin(2dmJ) sin(2q)
	- Pulse sequence: flashlight - T - \beta_{x} - \tau - \pi - \tau -echo
	- Notation of spin operators: Spq = 2SpSq where p, q = x, y, z
	- Initial density matrices:
		- \sigma[1] = Szz
		- \sigma[2] = Sxx + Syy
		- \sigma[3] = Sza - Szb
		- \sigma[4] = Sxx - Syy
		- \sigma[6] = Sxy + Syx
		- \sigma[7] = Sxz + Szx
		- \sigma[8] = Syz + Szy
		- \sigma[9] = Sxa - Sxb
		- \sigma[10] = Sya - Syb
		- \sigma[11] = Sza + Szb
		- \sigma[12] = Sxx - Syy
	- Hamiltonian:
		- H= \Omega$_{1}$ Sza + \Omega$_{2}$ Szb + (d -J) Szz - (d + 2J) (Sxx + Syy)/2
		- Can be diagonalized with a transformation using the operators \xi \cdot (Sxy - Syx)/2
			- \xi = arctan[(d + 2J) / (\Omega$_{1}$ - \Omega$_{2}$)]
		- In the eigenbasis: H =  \Omega$_{S}$ (Sza + Szb) + q (Sza - Szb) + (d - J) Szz
			- \Omega$_{S}$ = (\Omega$_{1}$ + \Omega$_{2}) / 2$
			- q = (\Omega$_{1}$ -  \Omega$_{2}$) cos(\xi) - sin(\xi) (d + 2J)/2
			- In this basis the coherence order is a constant of the motion during free evolution
		- Transformation to the rotating frame: the \Omega$_{S}$ (Sza + Szb) term goes to zero
	- Transformation to the eigenbasis of the Hamiltonian of the density matrices:
		- \sigma[1] = Szz
		- \sigma[2] = (Sxx + Syy) cos(\xi) + (Sza - Szb) sin(\xi)
		- \sigma[3] = (Sza - Szb) cos(\xi) - (Sxx + Syy) sin(\xi)
		- \sigma[4] = cos$^2$(\xi/2) Sxx - sin$^2$(\xi/2) Syy + 1/2 sin(\xi) (Sza - Szb)
		- \sigma[5] = -sin$^2$(\xi/2) Sxx + cos$^2$(\xi/2) Syy + 1/2 sin(\xi) (Sza - Szb)
		- \sigma[6] = Sxy + Syx
		- \sigma[7] = (Sxz + Szx) cos(\xi/2) - (Sxa - Sxb) sin(\xi/2)
		- \sigma[8] = (Syz + Szy) cos(\xi/2) - (Sya - Syb) sin(\xi/2)
		- \sigma[9] = (Sxa - Sxb) cos(\xi/2) + (Sxz + Szx) sin(\xi/2)
		- \sigma[10] = (Sya - Syb) cos(\xi/2) + (Syz + Szy) sin(\xi/2)
		- \sigma[11] = Sza + Szb
		- \sigma[12] = Sxx - Syy
	- Free evolution for time T:
		- Commutators between H and density matrices:
		  collapsed:: true
			- H has a Szz term and a (Sza - Szb) term
			- The density matrices in the eigenbasis have Szz, (Sza + Szb) and (Sxx + Syy) terms.
			- Regarding the Szz term:
				- [szz, sza + szb] = [szz, sxx + syy] = [szz, szz] = 0.
			- Regarding the (Sza - Szb) term:
				- For \sigma$_{T+}$ and \sigma$_{T-}$:
					- [sza - szb, sza + szb] = 0;
				- For \sigma$_{T0}$ and \sigma$_{S0}$:
					- [sza - szb, sxx + syy] = -2i (sxy - syx).
		- Szz is constant under free evolution
		- \sigma[2] =
			- (Sza-Szb) sin(\xi)
			  $+$ cos(\xi) (Sxx+Syy) cos(2 q)
			  $-$ cos(\xi) (-Sxy+Syx) sin(2 q)
		- \sigma[3] =
		  collapsed:: true
			- (Sza-Szb) cos(\xi)
			  $-$ sin(\xi) (Sxx+Syy) Cos(2 q)
			  $+$ sin(\xi) (-Sxy+Syx) Sin(2 q)
		- \sigma[4] =
			- $+$ 1/2 cos$^2$(\xi/2) Sxx
			  $-$ 1/2 cos$^2$(\xi/2) Syy
			  $+$ 1/2 cos$^2$(\xi/2) cos(2q) (Sxx + Syy)
			  $-$ 1/2 cos$^2$(\xi/2) sin(2q) (Sxy - Syx)
			  $-$ 1/2 sin$^2$(\xi/2) Syy
			  $+$ 1/2 sin$^2$(\xi/2) Sxx
			  $-$ 1/2 sin$^2$(\xi/2) cos(2q) (Sxx + Syy)
			  $+$ 1/2 sin$^2$(\xi/2) sin(2q) (Sxy - Syx)
			  $+$ 1/2 sin(\xi) (Sza - Szb)
		- \sigma[5] =
		  collapsed:: true
			- $-$ 1/2 sin$^2$(\xi/2) Sxx
			  $+$ 1/2 sin$^2$(\xi/2) Syy
			  $-$ 1/2 sin$^2$(\xi/2) cos(2q) (Sxx + Syy)
			  $+$ 1/2 sin$^2$(\xi/2) sin(2q) (Sxy - Syx)
			  $+$ 1/2 cos$^2$(\xi/2) Syy
			  $-$ 1/2 cos$^2$(\xi/2) Sxx
			  $+$ 1/2 cos$^2$(\xi/2) cos(2q) (Sxx + Syy)
			  $-$ 1/2 cos$^2$(\xi/2) sin(2q) (Sxy - Syx)
			  $+$ 1/2 sin(\xi) (Sza - Szb)
		- \sigma[6] = Sxy + Syx
		- \sigma[7] =
		  collapsed:: true
			- $+$ [- sin(\xi/2) cos(d-J) cos(q) - cos(\xi/2) sin(d-J) sin(q)] (Sxa - Sxb)
			  $+$ [ - cos(\xi/2) sin(d-J) sin(q) + sin(\xi/2) cos(d-J) cos(q)] (Sxz + Szx)
			  $+$ [ cos(\xi/2) sin(d-J) cos(q) + sin(\xi/2) cos(d-J) sin(q)] (Syz - Szy)
			  $+$ [ cos(\xi/2) cos(d-J) cos(q) + sin(\xi/2) sin(d-J) cos(q)] (Sya + Syb)
		- \sigma[8] =
		  collapsed:: true
			- $+$ [- sin(\xi/2) cos(d-J) cos(q) - cos(\xi/2) sin(d-J) sin(q)] (Sya - Syb)
			  $+$ [ sin(\xi/2) sin(d-J) sin(q) + cos(\xi/2) cos(d-J) cos(q)] (Syz + Szy)
			  $+$ [- cos(\xi/2) cos(d-J) sin(q) + sin(\xi/2) sin(d-J) cos(q)] (Sxz - Szx)
			  $+$ [- cos(\xi/2) sin(d-J) cos(q) + sin(\xi/2) cos(d-J) sin(q)] (Sxa + Sxb)
		- \sigma[9] =
		  collapsed:: true
			- $+$ [cos(\xi/2) cos(d-J) cos(q) - sin(\xi/2) sin(d-J) sin(q)] (Sxa - Sxb)
			  $+$ [- cos(\xi/2) sin(d-J) sin(q) + sin(\xi/2) cos(d-J) cos(q)] (Sxz + Szx)
			  $+$ [cos(\xi/2) sin(d-J) cos(q) + sin(\xi/2) cos(d-J) sin(q)] (Syz - Szy)
			  $+$ [cos(\xi/2) cos(d-J) sin(q) + sin(\xi/2) sin(d-J) cos(q)] (Sya + Syb)
		- \sigma[10] =
			- $+$ [cos(\xi/2) cos(d-J) cos(q) - sin(\xi/2) sin(d-J) sin(q)] (Sya - Syb)
			  $+$ [- cos(\xi/2) sin(d-J) sin(q) + sin(\xi/2) cos(d-J) cos(q)] (Syz + Szy)
			  $+$ [- cos(\xi/2) sin(d-J) cos(q) - sin(\xi/2) cos(d-J) sin(q)] (Sxz - Szx)
			  $+$ [- cos(\xi/2) cos(d-J) sin(q) - sin(\xi/2) sin(d-J) cos(q)] (Sxa + Sxb)
		- Sza + Szb is constant under free evolution
		- \sigma[12] = Sxx - Syy
	- Neglect the sinusoidal terms containing q (fast decaying):
		- \sigma[1] = Szz
		- \sigma[2] = (Sza - Szb) sin(\xi)
		- \sigma[3] = (Sza - Szb) cos(\xi)
		- \sigma[4] = 1/2 (Sxx - Syy) + 1/2 sin(\xi) (Sza - Szb) = 1/2 \sigma[12] + 1/2 \sigma[2]
		- \sigma[5] = - 1/2 (Sxx - Syy) + 1/2 sin(\xi) (Sza - Szb) = - 1/2 \sigma[12] + 1/2 \sigma[2]
		- \sigma[6] = Sxy + Syx
		- \sigma[7] = 0
		- \sigma[8] = 0
		- \sigma[9] = 0
		- \sigma[10] = 0
		- \sigma[11] = Sza + Szb
		- \sigma[12] = Sxx - Syy
	- Mw pulse
		- Bring the density matrix back to the product basis:
			- \sigma[1] = Szz
			- \sigma[2] = 1/2 sin(2\xi) (Sza - Szb) + sin$^2$(\xi) (Sxx + Syy)
			- \sigma[3] = cos$^2$(\xi) (Sza - Szb) + 1/2 sin(2\xi) (Sxx + Syy)
			- \sigma[4] =
				- $+$ 1/2[1 + sin$^2$(\xi)] Sxx
				  $+$ 1/2 [-1 + sin$^2$(\xi)] Syy
				  $+$ 1/4 sin(2\xi) (Sza - Szb)
			- \sigma[5] =
				- $+$ 1/2[- 1 + sin$^2$(\xi)] Sxx
				  $+$ 1/2 [1 + sin$^2$(\xi)] Syy
				  $+$ 1/4 sin(2\xi) (Sza - Szb)
			- \sigma[6] = Sxy + Syx
			- \sigma[11] = Sza + Szb
			- \sigma[12] = Sxx - Syy
		- Apply mw pulse \beta
			- \sigma[1] =
			  collapsed:: true
				- $+$ cos$^2$(\beta) Szz
				  $+$ sin$^2$(\beta) Syy
				  $-$ 1/2 \cdot sin(2\beta) (Syz + Szy)
			- \sigma[2] =
				- $+$ 1/2 sin(2\xi) cos(\beta) (Sza - Szb)
				  $-$ 1/2 sin(2\xi) sin(\beta) (Sya - Syb)
				  $+$ sin$^2$(\xi) cos$^2$(\beta) Syy
				  $+$ sin$^2$(\xi) sin$^2$(\beta) Szz
				  $+$ 1/2 sin$^2$(\xi) sin(2\beta) (Syz + Szy)
				  $+$ sin$^2$(\xi) Sxx
			- \sigma[3] =
				- $+$ cos$^2$(\xi) cos(\beta) (Sza - Szb)
				  $-$ cos$^2$(\xi) sin(\beta) (Sya - Syb)
				  $+$ 1/2 sin(2\xi) cos$^2$(\beta) Syy
				  $+$ 1/2 sin(2\xi) sin$^2$(\beta) Szz
				  $+$ 1/4 sin(2\xi) sin(2\beta) (Syz + Szy)
				  $+$ 1/2 sin(2\xi) Sxx
			- \sigma[4] =
				- $+$ 1/2 [1 + \sin$^2$(\xi)] Sxx
				  $+$ 1/2 \cos^2(\beta)[- 1 + \sin$^2$(\xi)] Syy
				  $+$ 1/2 \sin^2(\beta)[- 1 + \sin$^2$(\xi) Szz
				  $+$ 1/4 \sin(2\beta)[- 1 + \sin$^2$(\xi)] (Syz + Szy)
				  $+$ 1/4 \cos(\beta) \sin(2\xi)(Sza - Szb)
				  $-$ 1/4 \sin(\beta) \sin(2\xi)(Sya - Syb)
			- \sigma[5]
				- $+$ 1/2 [- 1 + \sin$^2$(\xi)] Sxx
				  $+$ 1/2 \cos^2(\beta)[1 + \sin$^2$(\xi)] Syy
				  $+$ 1/2 \sin^2(\beta)[1 + \sin$^2$(\xi) Szz
				  $+$ 1/4 \sin(2\beta)[1 + \sin$^2$(\xi)] (Syz + Szy)
				  $+$ 1/4 \cos(\beta) \sin(2\xi)(Sza - Szb)
				  $-$ 1/4 \sin(\beta) \sin(2\xi)(Sya - Syb)
			- \sigma[6] = cos(\beta) (Sxy + Syx) + sin(\beta) (Sxz + Szx)
			- \sigma[11] =
				- $+$ cos(\beta) (Sza + Szb)
				  $-$ sin(\beta) (Sya + Syb)
			- \sigma[12] =
				- $+$ Sxx
				  $-$ cos$^2$(\beta) Syy
				  $-$ sin$^2$(\beta) Szz
				  $-$ 1/2 sin(2\beta) (Szy + Syz)
		- Back to eigenbasis
			- \sigma[1] =
				- $+$ cos$^2$(\beta) Szz
				  $+$ sin$^2$(\beta) cos$^2$(\xi) Syy
				  $-$ sin$^2$(\beta) sin$^2$(\xi) Sxx
				  $+$ 1/2 sin$^2$(\beta) sin(\xi) (Sza - Szb)
				  $-$ 1/2 \cdot sin(2\beta) cos(\xi/2) (Syz + Szy)
				  $+$ 1/2 \cdot sin(2\beta) sin(\xi/2) (Sya - Syb)
			- \sigma[2] =
				- $+$ [1/2 sin(2\xi) cos(\xi) cos(\beta) + 1/2 sin$^2$(\xi) cos$^2$(\beta) sin(\xi) + 1/2 sin$^3$(\xi))] (Sza - Szb)
				  $+$ sin$^2$(\xi) sin$^2$(\beta) Szz
				  $+$ [ - 1/2 sin(2\xi) cos(\beta) sin(\xi) - sin$^2$(\xi) cos$^2$(\beta) sin$^2$(\xi/2) + sin$^2$(\xi) cos$^2$(\xi/2)] Sxx
				  $+$ [ - 1/2 sin(2\xi)  cos(\beta) sin(\xi) + sin$^2$(\xi) cos$^2$(\beta) cos$^2$(\xi/2) - sin$^2$(\xi) sin$^2$(\xi/2)] Syy
				  $+$ [ - 1/2 sin(2\xi) sin(\beta) cos(\xi/2) - 1/2 sin$^2$(\xi) sin(2\beta) sin(\xi/2)] (Sya - Syb)
				  $+$ [- 1/2 sin(2\xi) sin(\beta) sin(\xi/2) + 1/2 sin$^2$(\xi) sin(2\beta) cos(\xi/2) ] (Syz + Szy)
			- \sigma[3] =
				- $+$ cos$^3$(\xi) cos(\beta) (Sza - Szb)
				  $-$ cos$^2$(\xi) cos(\beta) sin(\xi) (Sxx + Syy)
				  $-$ cos$^2$(\xi) sin(\beta) cos(\xi/2) (Sya - Syb)
				  $-$ cos$^2$(\xi) sin(\beta) sin(\xi/2) (Syz + Szy)
				  $+$ 1/2 sin(2\xi) cos$^2$(\beta) cos$^2$(\xi/2) Syy
				  $-$ 1/2 sin(2\xi) cos$^2$(\beta) sin$^2$(\xi/2) Sxx
				  $+$ 1/4 sin(2\xi) cos$^2$(\beta) sin(\xi) (Sza - Szb)
				  $+$ 1/2 sin(2\xi) sin$^2$(\beta) Szz
				  $+$ 1/4 sin(2\xi) sin(2\beta) cos(\xi/2) (Syz + Szy)
				  $-$ 1/4 sin(2\xi) sin(2\beta) sin(\xi/2) (Sya - Syb)
				  $+$ 1/2 sin(2\xi) cos$^2$(\xi/2) Sxx
				  $-$ 1/2 sin(2\xi) sin$^2$(\xi/2) Syy
				  $+$ 1/4 sin(2\xi) sin(\xi) (Sza - Szb)
				- \sigma[3] =
					- $+$ [cos$^3$(\xi) cos(\beta) + 1/4 sin(2\xi) cos$^2$(\beta) sin(\xi) + 1/4 sin(2\xi) sin(\xi)] (Sza - Szb)
					  $+$ 1/2 sin(2\xi) sin$^2$(\beta) Szz
					  $+$ [ - cos$^2$(\xi) cos(\beta) sin(\xi) - 1/2 sin(2\xi) cos$^2$(\beta) sin$^2$(\xi/2) + 1/2 sin(2\xi) cos$^2$(\xi/2)] Sxx
					  $+$ [ - cos$^2$(\xi) cos(\beta) sin(\xi) + 1/2 sin(2\xi) cos$^2$(\beta) cos$^2$(\xi/2) - 1/2 sin(2\xi) sin$^2$(\xi/2) ] Syy
					  $+$ [ - cos$^2$(\xi) sin(\beta) cos(\xi/2) - 1/4 sin(2\xi) sin(2\beta) sin(\xi/2)] (Sya - Syb)
					  $+$ [- cos$^2$(\xi) sin(\beta) sin(\xi/2) + 1/4 sin(2\xi) sin(2\beta) cos(\xi/2) ] (Syz + Szy)
			- \sigma[4] =
				- $+$ 1/2 [-1 + sin$^2$(\xi)] sin$^2$(\beta) Szz
				  $+$ [ 1/2 [1 + sin$^2$(\xi)]cos$^2$(\xi/2) - 1/2 cos$^2$(\beta)[- 1 + sin$^2$(\xi)] sin$^2$(\xi/2) - 1/4 cos(\beta) sin(2\xi) sin(\xi)] Sxx
				  $+$ [ - 1/2  [1 + sin$^2$(\xi)]sin$^2$(\xi/2) + 1/2 cos$^2$(\beta)[- 1 + sin$^2$(\xi)] cos$^2$(\xi/2) - 1/4 cos(\beta) sin(2\xi) sin(\xi)] Syy
				  $+$ [ 1/4 [1 + sin$^2$(\xi)]sin(\xi) + 1/4 cos$^2$(\beta)[- 1 + sin$^2$(\xi)] sin(\xi) + 1/4 cos(\beta) sin(2\xi) cos(\xi)] (Sza - Szb)
				  $+$ [ -1/4 sin(2\beta) [- 1 + sin$^2$(\xi)] sin(\xi/2) - 1/4 sin(2\xi) sin(\beta) cos(\xi/2)] (Sya - Syb)
				  $+$ [1/4 sin(2\beta) [- 1 + sin$^2$(\xi)] cos(\xi/2) - 1/4 sin(2\xi) sin(\beta) sin(\xi/2)] (Syz + Szy)
			- \sigma[5] =
				- $+$ 1/2 [1 + sin$^2$(\xi)] sin$^2$(\beta) Szz
				  $+$ [ - 1/2 cos$^2$(\xi)cos$^2$(\xi/2) - 1/2 cos$^2$(\beta)[1 + sin$^2$(\xi)] sin$^2$(\xi/2) - 1/4 cos(\beta) sin(2\xi) sin(\xi)] Sxx
				  $+$ [ 1/2 cos$^2$(\xi)sin$^2$(\xi/2) + 1/2 cos$^2$(\beta)[1 + sin$^2$(\xi)] cos$^2$(\xi/2) - 1/4 cos(\beta) sin(2\xi) sin(\xi)] Syy
				  $+$ [ - 1/4 cos$^2$(\xi)sin(\xi) + 1/4 cos$^2$(\beta)[1 + sin$^2$(\xi)] sin(\xi) + 1/4 cos(\beta) sin(2\xi) cos(\xi)] (Sza - Szb)
				  $+$ [ -1/4 sin(2\beta) [1 + sin$^2$(\xi)] sin(\xi/2) - 1/4 sin(2\xi) sin(\beta) cos(\xi/2)] (Sya - Syb)
				  $+$ [1/4 sin(2\beta) [1 + sin$^2$(\xi)] cos(\xi/2) - 1/4 sin(2\xi) sin(\beta) sin(\xi/2)] (Syz + Szy)
			- \sigma[6] =
				- $+$ cos(\beta) (Sxy + Syx)
				  $+$ sin(\beta) cos(\xi/2) (Sxz + Szx)
				  $-$ sin(\beta) sin(\xi/2) (Sxa - Sxb)
			- \sigma[11] =
			  collapsed:: true
				- $+$ cos(\beta) (Sza + Szb)
				  $-$ sin(\beta) cos(\xi/2) (Sya + Syb)
				  $+$ sin(\beta) sin(\xi/2) (Syz - Szy)
			- \sigma[12] =
				- $+$ cos$^2$(\xi/2) Sxx
				  $-$ sin$^2$(\xi/2) Syy
				  $+$ 1/2 sin(\xi) (Sza - Szb)
				  $-$ cos$^2$(\beta) cos$^2$(\xi/2) Syy
				  $+$ cos$^2$(\beta) sin$^2$(\xi/2) Sxx
				  $-$ 1/2 cos$^2$(\beta) sin(\xi) (Sza - Szb)
				  $-$ sin$^2$(\beta) Szz
				  $-$ 1/2 sin(2\beta) cos(\xi/2) (Szy + Syz)
				  $+$ 1/2 sin(2\beta) sin(\xi/2) (Sya - Syb)
				- $+$ [ cos$^2$(\xi/2) + cos$^2$(\beta) sin$^2$(\xi/2) ] Sxx
				  $+$ [ - sin$^2$(\xi/2) - cos$^2$(\beta) cos$^2$(\xi/2) ] Syy
				  $+$ 1/2 sin(\xi) [1 - cos$^2$(\beta) ] (Sza - Szb)
				  $-$ sin$^2$(\beta) Szz
				  $-$ 1/2 sin(2\beta) cos(\xi/2) (Szy + Syz)
				  $+$ 1/2 sin(2\beta) sin(\xi/2) (Sya - Syb)
	- Input the results for each pathway:
		- \sigma[1] (initially Szz):
			- Coefficient of Sxa + Sxb:
				- sin(2\beta) cos(\xi)$^2$ sin(2dmJ)
			- Coefficient of Sya + Syb = 0
		- \sigma[2] (initially Sxx + Syy):
		  collapsed:: true
			- Coefficient of Sxa + Sxb:
				- [2 sin(\beta) - sin(2\beta) ] cos(\xi)$^2$ sin(\xi)$^2$ sin(2dmJ)
			- Coefficient of Sya + Syb = 0
		- \sigma[3] (initially Sza - Szb):
		  collapsed:: true
			- Coefficient of Sxa + Sxb:
				- [2 sin(\beta) - sin(2\beta) ] cos(\xi)$^3$ sin(\xi) sin(2dmJ)
			- Coefficient of Sya + Syb = 0
		- \sigma[4] (initially Sxx):
		  collapsed:: true
			- Coefficient of Sxa + Sxb
				- 1/2 [2 sin(\beta) - sin(2\beta) ] cos(\xi)$^2$ sin(\xi)$^2$ sin(2dmJ)
			- Coefficient of Sya + Syb:
				- 1/2 sin(2\beta) cos(\xi)$^2$ sin(2dmJ)
		- \sigma[5] (initially Syy):
		  collapsed:: true
			- Coefficient of Sxa + Sxb:
				- 1/2 [2 sin(\beta) - sin(2\beta) ] cos(\xi)$^2$ sin(\xi)$^2$ sin(2dmJ)
			- Coefficient of Sya + Syb:
				- - sin(2\beta) cos(\xi)$^2$ sin(2dmJ)
		- \sigma[6] (initially Sxy + Syx):
		  collapsed:: true
			- Coefficient of Sxa + Sxb = 0
			- Coefficient of Sya + Syb:
				- -2 sin(\beta) cos(\xi)$^2$ sin(2dmJ)
		- \sigma[11] (initially Sza + Szb):
		  collapsed:: true
			- Coefficient of Sxa + Sxb = 0
			- Coefficient of Sya + Syb:
				- 2 sin(beta) cos(\xi)$^2$ cos(2dmJ)
		- \sigma[12] (initially Sxx - Syy):
			- Coefficient of Sxa + Sxb = 0
			- Coefficient of Sya + Syb:
				- sin(2\beta) cos(\xi)$^2$ sin(2dmJ)
- ## Initial rotation
  id:: 65bd20bf-4996-4b3a-96ec-4fbd1ed452ed
- ((65f03bc9-b0bd-4059-9230-db1f6b0227de))
  collapsed:: true
	- Express in the laboratory frame (z-direction poles of the magnet, x-direction tube axis, y-direction follows) the initial state (updown) which is oriented in the direction of the dipolar coupling $n_D$
		- $n_D$ can be expressed as (sin(\theta)cos(\phi), sin(\theta)sin(\phi), cos(\theta)) (note that \phi is the angle between $n_D$ and the x-axis, not the y-axis)
			- The Euler angles to express the $n_D$ vector [0, 0, 1]$_D$ as [sin(\theta)cos(\phi), sin(\theta)sin(\phi), cos(\theta)]$_L$, where the subscript indicates the system of reference, are \beta = \theta, \gamma = \pi - phi ( ((65f040a7-c270-4eb6-9c1e-0138afcee729)) )
		- The dipolar vector is not coaxial with any principal axis of the molecules of PSI, therefore one first has to express everything as a function of a coordinate system that has the z-axis corresponding with $n_D$ (or the dipolar axis in the molecular frame) and then transform to the lab frame