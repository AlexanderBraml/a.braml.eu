---
title: Different FSK Modulator Implementations
---

[[SDR FSK Modulation Approaches]]

1. Modulating using a VCO (Voltage Controlled Oscillator)
	- Sample Flowgraph: ![[notes/images/Pasted image 20230709143456.png]]
	- You get Coherent FSK (what we want) ([[Frequency Shift Keying#^90d851]])
	- Parameters unclear because documentation is not good
2. Modulating by generating two signals and adding only portions of them
	- Easiest to implement and understand
	- Sample Flowgraph: ![[notes/images/Pasted image 20230709142840.png]]
	- You get non-coherent FSK ([[Frequency Shift Keying#^90d851]])
		- Not as efficient and easy to decode
3. Using the GFSK Mod Block (built into GNURadio)
	- Sample Flowgraph: ![[notes/images/Pasted image 20230709143807.png]]
	- Problems
		- [[Gaussian FSK Modulation]] is slightly different to FSK Modulation
			- But: You can set $BT$ (Gaussian filter bandwidth * symbol time) to $1$ to effectively get FSK Modulation
		- Minimum Deviation is 800 Hz (not very flexible)
	- Our current solution for the transmitter of the Balise emulation
	- Will probably change in the future, as we want a pure FSK modulation and implement the block ourselves
