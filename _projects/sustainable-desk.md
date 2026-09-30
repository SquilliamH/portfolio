---
title: Fastener-Free Chipboard Desk
summary: A structural desk designed with FEA and topology optimization that held about 100 times its own weight.
order: 6
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

## Design and analysis

I built the SolidWorks models for each design iteration and the drawings for laser cutting, tuning the interlocking joint geometry and cutting arcs out of the outer edges where the stress analysis showed material wasn't working. In simulation, a 27.5 lb (12.5 kg) load produced peak stress of about 4.95 × 10⁵ N/m², a minimum factor of safety of 6.07, and a maximum deflection of 0.04 mm at the top edges.

<figure>
  <img src="/assets/img/sustainable-desk/fea.jpg" alt="FEA displacement plot of an early design">
  <figcaption>FEA displacement study of an early design.</figcaption>
</figure>

<figure>
  <img src="/assets/img/sustainable-desk/topology.jpg" alt="Topology optimization result">
  <figcaption>Topology optimization showing where material is needed.</figcaption>
</figure>

## Results

The structure weighed 0.12 kg, held 26 lb against a 20 lb requirement, and failed at 28 lb, which matched the FEA prediction to 94.4%. It is fully recyclable and needs no other materials.
