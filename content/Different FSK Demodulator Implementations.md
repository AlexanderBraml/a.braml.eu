---
title: Different FSK Demodulator Implementations
---

[[SDR FSK Modulation Approaches]]

1. Using the GFSK Demod Block (built into GNURadio)
	- Sample Flowgraph: ![[notes/images/Pasted image 20230709144847.png]]
	- Problems
		- Lack of documentation of the parameters
			- But: Default parameters work good enough, although more fine-tuning needed if we pursue this path further
	- Our current solution as it works perfectly with the GFSK Mod block
2. Using the Quadrature Demod Block (built into GNURadio)
	- Sample Flowgraph: ![[notes/images/Pasted image 20230709150751.png]]
	- Haven't tested this implementation thouroughly, but plan to in the near future as we optimize the receiver
