---
title: GRC Low Pass Filter
---

[[SDR Notes]]

- Filtert Signal
- Fokussiert sich auf Bereich von `center_freq - cutoff_freq` - `center_freq + cutoff_freq`
	- cutoff_freq muss man selbst herausfinden, gute Möglichkeit ist sich das im frequency sink anzuschauen und zu bestimmen
- Transition width gibt an wie "scharf" abgeschnitten wird
	- Niedrigerer Wert bedeutet "schärfere" Abschneidung, allerdings dadurch mehr Rechenleistung benötigt
	- Guter Start-Wert: 50e6
	- Vorstellung:
		- Der Bereich um center_freq mit cutoff_freq bleibt immer drin
		- Bei center_freq +- cutoff_freq wird langsam abgeschnitten bis man bei center_freq +- cutoff_freq +- transition_width dann nur noch bei Noise ist
- Decimation
	- Nach dem Filtern behalte nur `1/decimation` samples
	- Schmeißt Samples außerhalb der gewünschten Region weg
	- Achtung: Dadurch ändert sich die Sample Rate!
		- In den folgenden Blöcken anpassen
		- Kurze Notiz im Flow-Graph schadet auch nicht
- Beispiel Flow-Graph
	- ![[notes/images/Pasted image 20230622095924.png]]