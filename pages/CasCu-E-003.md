type:: experiment
project:: [[project/CasCu]]
technique:: [[IV]], [[cwEPR]]
spectrometer:: [[Lyra]]
sample:: [[CasCu-S-001]]
date:: [[2024-05-31]]

- 🎯 Goal: study angular dependence, light dependence, Vbias dependence and possible (did not work) EDMR at RT
  id:: 665a03c0-8051-4e9b-94ba-ef0104aecce3
- CasCu-E-003001: initial IV curve
- CasCu-E-003002 to 004: angular dependence and light dependence
  collapsed:: true
	- |Parameter|CasCu-E-003002|CasCu-E-003003|CasCu-E-003004|
	  |--|--|--|
	  |B_0|[3000, 3700] G|[3000, 3700] G|[3000, 3700] G|
	  |\Delta B_0|1 G|1 G|1 G|
	  |B_m|[100 kHz, 5 G]|[100 kHz, 5 G]|[100 kHz, 5 G]|
	  |gaussmeter|off|off|off|
	  |\tau_C|30 ms|30 ms|30 ms|
	  |\tau_conv|3 \tau_C|3 \tau_C|3 \tau_C|
	  |nRun|16|16|4|
	  |Att|18 dB|18 dB|18 dB|
	  |Temperature|300 K|300K|300 K|
	  |Angle|0deg|90deg|180deg|
	  |P_light|off|off|off|
	  |Vbias|0|0|0|
	- The angle defined here is the one between the normal to the surface of the substrate and the y-axis, that is the direction in which the light hits the sample. With this definition, 90deg is the case of surface normal pointing along the direction of the magnetic field and minimum irradiation of the sample when the light is on.
	- Angular dependence has been observed
	- The position 180deg has similar shape to 0deg but larger signal, therefore it will be used in the following
- CasCu-E-003005: wide scan (very broad signal in the range 2500 to 3300 G?)
- CasCu-E-003006, CasCu-E-003011, CasCu-E-003012: light and bias dependence
  collapsed:: true
	- |Parameter|CasCu-E-003006|CasCu-E-003011|CasCu-E-003012|
	  |--|--|--|
	  |B_0|[3000, 3700] G|[3000, 3700] G|[3000, 3700] G|
	  |\Delta B_0|1 G|1 G|1 G|
	  |B_m|[100 kHz, 5 G]|[100 kHz, 5 G]|[100 kHz, 5 G]|
	  |gaussmeter|off|off|off|
	  |\tau_C|30 ms|30 ms|30 ms|
	  |\tau_conv|3 \tau_C|3 \tau_C|3 \tau_C|
	  |nRun|4|4|4|
	  |Att|18 dB|18 dB|18 dB|
	  |Temperature|300 K|300K|300 K|
	  |P_light|3%|3%|3%|
	  |Vbias|0 V|1 V|2 V|
	- No change observed: same spectra as 003004
- CasCu003007 to 003010: IV curve
  collapsed:: true
	- |Parameter|CasCu-E-003007|CasCu-E-003008|CasCu-E-003009|CasCu-E-003010|
	  |--|--|--|
	  |Temperature|300 K|300K|300 K|300 K|
	  |P_light|0%|1%|2%|3%|
- EDMR measurements: no signal. Following combinations explored:
  collapsed:: true
	- (Vb = 0 V, P_light = 0%)
	  (Vb = 1 V, P_light = 0%)
	  (Vb = 1 V, P_light = 3%)
	  (Vb = 2 V, P_light = 3%)
	  (Vb = 2 V, P_light = 5%)
	  (Vb = 5 V, P_light = 3%)
	- The spectrum at Vbias = 5 V had spikes of noise that lasted around 5 magnetic field points, moreover during the aquisition I_{DC} jumped from 1uA to 2uA
- CasCu-E-003013: IV curve with P_{light} = 3% after having kept the sample at 5V for the EDMR measurement (around 5 minutes)
  collapsed:: true
	- The IV curve looks very asymmetric
-