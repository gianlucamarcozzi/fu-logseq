## 🤖 Introduction
	- Be careful about the screws of the coupler of the faser: the red ones are not to be touched!
	  collapsed:: true
		- Windows user: InnoLas, pwd: InnoLas
		- Connect
		- Turn the key to 1 and a bit further
		- On the right: first button top-left to start-up
		- Wait for temperature to reach 25 degrees
		- On the right: second row button to turn on the diodes
		- To access restricted area: Ctrl+L, pwd: Innolas
		- More options available: remember to click on "Apply changes"
	- ### Software turn on procedure
	- ### Trigger
	  collapsed:: true
		- You can trigger the laser (TRIG) or get a trigger from the laser (SYNC)
		- Triggering the laser: between the diodes and the Q-switch (?) there are 240 us second delay
			- You can trigger the diodes only and the second trigger is sent automatically by the network
			- You can trigger both but you need to send two triggers with the correct time delay
			- This means that between the first trigger and the start of the pulse there will be 240 us seconds
			- When the laser is triggered then one can get a trigger from the laser when the pulse starts (or when the "Q-switch" is internally triggered) from the SYNC port
	- ### Optimal alignment
	  collapsed:: true
		- The max of the 532nm does not correspond to the max of the OPO signal because the majority of the radiation goes through
			- One needs to go a bit on the sides and will find two symmetric peaks
		- For best stability: one has to sit close to the top but not exactly on the maximum
			- The installers said that for our system they found that the area on the left side of the right peak is the most stable