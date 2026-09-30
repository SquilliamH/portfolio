---
title: Automated Shaft Design in MATLAB
summary: A 500-line script that sizes a shaft under combined bending and torsion in about five iterations.
order: 9
hidden: true
role: Individual project
context: MAE 190 Design of Machine Elements, UC San Diego
dates: 2025
tools: [MATLAB]
specs: 
  - label: Length
    value: ~500 lines
  - label: Convergence
    value: 5 iterations or fewer
thumbnail: 
links:
  - label: Code documentation (PDF)
    url: /assets/docs/shaft-design-documentation.pdf
---

Shaft sizing by hand is circular: you need the diameter to find the stress concentration factors, and you need those factors to find the diameter. The manual process means repeated chart lookups, interpolation, and plenty of chances for arithmetic errors.

I wrote a MATLAB script that does the whole loop. You pick a standard ASTM steel or enter your own material properties, enter the bending moments and torques in SI or imperial units, and it interpolates the stress concentration factors (Kt, Kts) from the D/d and r/d ratios, calculates notch sensitivity, applies the size, surface, and temperature factors, and iterates to a diameter that meets the safety factor, usually within five iterations.
<!-- TODO: confirm the term/year and, if you like, add a worked example -->

