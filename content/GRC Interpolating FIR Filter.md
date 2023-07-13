---
title: GRC Interpolating FIR Filter
---

[[SDR Notes]]

- Wenn ein sample reinkommt wird dieses mit `taps` multipliziert, d.h. z.B. bei taps = \[10, 0, 0, 0, 0, 0, 0, 0, 0, 0\] wird das einkommende sample mit 10 multipliziert und die 9 folgenden samples sind alle 0en
- Die Länge dieses Vektors muss mit interpolation übereinstimmen
- Natürlich verändert sich dadurch auch die sample rate