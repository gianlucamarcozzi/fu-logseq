type:: experiment
project:: [[projects/CasCu]]
technique:: [[IV]], [[cwEPR]]
spectrometer:: [[Lyra]]
sample:: [[CasCu-S-001]], [[CasCu-S-002]]
date:: [[2024-05-17]]

- CasCu-E-002009 [[DPPH]] [[Field calibration]] at RT using gaussmeter
	- |Parameter|Value|
	  |--|--|
	  |Sample|DPPH|
	  |B_0|[3300, 3500] G|
	  |\Delta B_0|0.2|
	  |B_m|[100 kHz, 0.1 G]|
	  |Gaussmeter|on|
	  |\tau_C|10 ms|
	  |\tau_conv|3 \tau_C|
	  |nRun|1|
	  |Att|48 dB|
	  |Temperature|300 K|
	  |f_mw|9.403024 GHz|
- Other measurements (CasCu-E-002011 to 013 are just noise, no EDMR signal)
	- |Parameter|CasCu-E-002010|CasCu-E-002014|CasCu-E-002015|
	  |--|--|--|
	  |Sample|[[CasCu-S-001]]|[[CasCu-S-001]]|[[CasCu-S-002]]|
	  |B_0|[2000, 4000] G|[2000, 4000] G|[2000, 4000] G|
	  |\Delta B_0|2 G|2 G|2 G|
	  |B_m|[100 kHz, 5 G]|[100 kHz, 5 G]|[100 kHz, 5 G]|
	  |gaussmeter|off|off|off|
	  |\tau_C|10 ms|10 ms|10 ms|
	  |\tau_conv|3 \tau_C|3 \tau_C|3 \tau_C|
	  |nRun|50|1|10|
	  |Att|18 dB|18 dB|18 dB|
	  |Temperature|300 K|==60 K==|300 K|
	- Signal looks broader than what shown for sample 1-film in the supplementary information of [[@VdW Mediated Strong Magnetic Exchange Interactions in Chains of Hydrogen-Free Sublimable Molecular Qubits]]
		- It might be degrading and the g-anisotropy changing, with another contribution arising from the degraded part
	- Signal at 350 mT coming from quartz substrate (as also demonstrated by CasCu-E-002015)
	- No linewidth change between 300 K and 60 K
	- ![E-002_cwEPRatRTand50K.png](../assets/E-002_cwEPRatRTand50K_1716903183922_0.png)
-