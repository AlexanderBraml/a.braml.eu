[[SDR Notes]]

- Demoduliert gefiltertes Signal zu einem Audio-Signal
- Quadrature Rate ist die eingehende sample_rate
	- hier aufpassen mit Decimation in vorherigen Blöcken
- Audio Decimation ändert wieder die sample_rate
	- Audio Karte empfängt Daten mit 48 kHz
	- Also hier decimation so einstellen dass 48 kHz rauskommt