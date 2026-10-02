---
title: Fastener-Free Chipboard Desk
summary: A structural desk designed with FEA and topology optimization that held about 100 times its own weight.
kind: Course project
order: 7
role: Team project with Anya Ustinova; CAD, FEA, and laser-cut drawings
context: MAE 191 Sustainable Engineering Design, UC San Diego
dates: Oct – Dec 2024
tools: [SolidWorks, SolidWorks Simulation, topology optimization, laser cutting]
specs:
  - label: Supported load
    value: 11.8 kg (26 lb)
  - label: Structure mass
    value: 0.12 kg
  - label: Performance index
    value: "98.25"
  - label: Measured vs. FEA
    value: 94.4%
thumbnail: /assets/img/sustainable-desk/desk.jpg
hero_caption: The finished desk structure under load.
links:
  - label: Project report (PDF)
    url: /assets/docs/sustainable-desk-report.pdf
---

The challenge was to build a desk from chipboard alone, with no adhesives or fasteners, that carries as much load as possible for as little material as possible. We settled on an interlocking matrix of slotted panels and used FEA and topology studies to decide where material was needed.

## Requirements

The brief set a minimum size of 0.3 m tall by 0.2 m by 0.15 m, a maximum structure mass of 0.12 kg, a minimum load of 9 kg (20 lb), and a maximum deflection of 10 mm. The only material was 12 x 18 in chipboard, with a modulus of about 3 GPa along the fibers and 0.5 GPa across them, and the score was the load supported divided by the structure's weight. We had five weeks to design, analyze, and test.

## Iteration

The first concept had a folded desktop with interlocking tabs, but it was too heavy and the folds looked like failure points. A topology study on a solid block pointed to a top surface carried on a few legs, which led to a five-legged design that we modeled in SolidWorks, but it would have needed more material to resist torsion. We went back to the interlocking grid and fixed what had worried us: slots placed too close to the sheet edges tore out under load, so we moved them to each quarter of the sheet length and dropped the folded desktop. Rounding the corners to save weight weakened the structure, so we cut large arcs from the outer edges instead, where the stress analysis showed the sheets carry the least load.

## Design and analysis

I built the SolidWorks models for each design iteration and the drawings for laser cutting, tuning the interlocking joint geometry and cutting arcs out of the outer edges where the stress analysis showed material wasn't working. In simulation, a 27.5 lb (12.5 kg) load produced peak stress of about 4.95 × 10⁵ N/m², a minimum factor of safety of 6.07, and a maximum deflection of 0.04 mm at the top edges.

<figure>
  <img src="{{ '/assets/img/sustainable-desk/final-cad.jpg' | relative_url }}" alt="CAD of the final interlocking panel matrix" loading="lazy">
  <figcaption>The final design in CAD: interlocking slotted panels.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/sustainable-desk/panel-flat.jpg' | relative_url }}" alt="Flat laser-cut panel with slots and tabs" loading="lazy">
  <figcaption>A flat panel as sent to the laser cutter.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/sustainable-desk/fea.jpg' | relative_url }}" alt="FEA displacement plot of an early design">
  <figcaption>FEA displacement study of an early design.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/sustainable-desk/topology.jpg' | relative_url }}" alt="Topology optimization result">
  <figcaption>Topology optimization showing where material is needed.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/sustainable-desk/final-build.jpg' | relative_url }}" alt="The assembled chipboard desk structure">
  <figcaption>The assembled structure.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/sustainable-desk/stress.jpg' | relative_url }}" alt="Von Mises stress plot of the final design" loading="lazy">
  <figcaption>Von Mises stress in the final design under the target load.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/sustainable-desk/solid-topology.jpg' | relative_url }}" alt="Topology study of a solid block" loading="lazy">
  <figcaption>A solid-block topology study, which showed where material carries load.</figcaption>
</figure>

## Results

The structure weighed 0.12 kg, held 26 lb against a 20 lb requirement, and failed at 28 lb. FEA predicted failure at 27.65 lb and a performance index of 104.08; the measured index of 98.25 is 94.4% of that. It is fully recyclable and needs no other materials.

<figure>
  <img src="{{ '/assets/img/sustainable-desk/load-test.jpg' | relative_url }}" alt="A bin of tools loaded on top of the desk structure">
  <figcaption>Load test with a bin of tools on the structure.</figcaption>
</figure>
