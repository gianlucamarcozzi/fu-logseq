type:: experiment
project:: [[projects/ZePSI]] 
technique:: [[trEPR]]
spectrometer:: [[Isaak]]
resonator:: [[MD5-W1]]
date:: [[2024-02-21]]

- trEPR on [[Samples/ZePSI-S-001]] at 80K
	- Dependence of the signal from experimental parameters
- Problem with the **trigger level**:
  id:: 660ecd66-b56e-4e34-9979-7d384ecb3e30
	- the trigger level was too low, therefore when the laser was not lasing properly (instead of seeing a pulse in the oscilloscope one would see a sinusoidal) the measurement would accumulate almost continuously even though there was no laser pulse (see also page 6 of labbook 1)
	- ![troubleshoot_triggerLevel_E-001.svg](../assets/troubleshoot_triggerLevel_E-001_1712246351146_0.svg)
	- Above there is an example of some outliers that are recorded due to this problem with the laser trigger