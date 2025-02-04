type:: experiment
project:: [[project/CasZnO]]
technique:: [[cwEPR]]
spectrometer:: [[Lyra]]
sample:: [[CasZnO-S-001]], [[CasZnO-S-002]]
date:: [[2024-06-20]], [[2024-06-21]], [[2024-06-25]]

- 🎯 Goal: photoexcitation under blue light laser
- CasZnO-E-003001: broad scan, 2 scans
- CasZnO-E-003002 to 007: light dependence of CasZnO-E-001
  id:: 667c37c6-31c8-4ac6-a6bb-2fd51b0ef823
	- |Parameter|Value|
	  |--|--|
	  |B_0|[3200, 3500] G|
	  |\Delta B_0|0.4 G|
	  |B_m|[100 kHz, 3 G]|
	  |gaussmeter|off|
	  |\tau_C|30 ms|
	  |\tau_conv|3 \tau_C|
	  |nRun|[25, 5, 5, 5, 20, 25]|
	  |Att|30 dB|
	  |Temperature|10 K|
	  |Parameter|CasZnO-E-003002|E-003003|E-003004|E-003005|E-003006|E-003007|
	  |--|--|--|--|--|--|--|
	  |P$_\lambda$|dark|1 mW|5 mW|10 mW|20 mW|50 mW|
	  |I$_\lambda$|0 mA|132.5 mA|142.2 mA|152.5 mA|173.0 mA|218.0 mA|
	- Image
- CasZnO-E-003008 to CasZnO-E-003010: power dependence at 50 mW irradiation
	- |Parameter|Value|
	  |--|--|
	  |B_0|[3200, 3500] G|
	  |\Delta B_0|0.4 G|
	  |B_m|[100 kHz, 3 G]|
	  |gaussmeter|off|
	  |\tau_C|30 ms|
	  |\tau_conv|3 \tau_C|
	  |nRun|[25, 5, 5, 5, 20, 25]|
	  |Temperature|10 K|
	  |I$_\lambda$|218.0 mA|
	  |P$_\lambda$|50 mW|
	  |\lambda|450 nm|
	  |Parameter|CasZnO-E-003008|E-003009|E-003010|
	  |--|--|--|--|--|--|--|
	  |Attenuation|24 dB|18 dB| 36 dB|
	- Probably better separation between background and signal when using 36 dB
- CasZnO-E-003011: irradiation with UV LED (360 nm)
	- Same spectrum at 50 mW irradiation of blue laser, probably because the relaxation back to dark state takes hours of time
- CasZnO-E-003012 and 013: background empty tube and empty resonator
	- |Parameter|CasZnO-E-003012|CasZnO-E-003013|
	  |--|--|
	  |B_0|[3200, 3500] G|[3200, 3500] G|
	  |\Delta B_0|0.4 G|0.4 G|
	  |B_m|[100 kHz, 3 G]|[100 kHz, 3 G]|
	  |gaussmeter|off|off|
	  |\tau_C|30 ms|30 ms|
	  |\tau_conv|3 \tau_C|3 \tau_C|
	  |nRun|25|1|
	  |Temperature|10 K|10 K|