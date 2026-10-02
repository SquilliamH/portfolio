---
title: Fastener-Free Chipboard Desk
summary: A structural desk designed with FEA and topology optimization that held about 100 times its own weight.
kind: Course project
order: 20
hidden: true
role: Team project with Anya Ustinova. I built the CAD, ran the FEA, and drew the laser-cut parts.
context: MAE 191 Sustainable Engineering Design, UC San Diego
dates: Oct – Dec 2024
tools: [SolidWorks, SolidWorks Simulation, topology optimization, laser cutting]
stats:
  - n: "98×"
    label: load supported divided by structure weight
  - n: "0.12 kg"
    label: structure mass, no glue or fasteners
  - n: "11.8 kg"
    label: measured supported load
  - n: "94%"
    label: of the simulated performance index
thumbnail: /assets/img/sustainable-desk/desk.jpg
hero_caption: The finished desk structure under load.
---

The challenge: build a desk from chipboard alone, no adhesives or fasteners, that carries as much load as possible for as little material as possible. We settled on an interlocking matrix of slotted panels and used FEA and topology studies to decide where material was needed.

## The brief

- **Size:** at least 0.3 m tall by 0.2 m by 0.15 m.
- **Mass:** no more than 0.12 kg.
- **Load:** at least 9 kg (20 lb), with under 10 mm of deflection.
- **Material:** only 12 × 18 in chipboard (about 3 GPa along the fibers, 0.5 GPa across them).
- **Score:** load supported divided by structure weight. Five weeks to finish.

## How the design changed

1. **A folded desktop with tabs.** Too heavy, and the folds looked like failure points.
2. **A five-legged design,** from a topology study of a solid block. It would have needed extra material to resist torsion.
3. **The interlocking grid.** We went back to it and fixed what worried us. Slots too close to a sheet's edge tore out, so we moved them to each quarter of the sheet length and dropped the folded top.

Rounding the corners to save weight weakened the structure, so we cut large arcs from the outer edges instead, where the stress analysis showed the sheets carry the least load.

<div class="figure-row">
<figure>
  <img src="{{ '/assets/img/sustainable-desk/solid-topology.jpg' | relative_url }}" alt="Topology study of a solid block" loading="lazy">
  <figcaption>A solid-block topology study showing where material carries load.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/sustainable-desk/topology.jpg' | relative_url }}" alt="Topology optimization result" loading="lazy">
  <figcaption>Topology optimization of the matrix.</figcaption>
</figure>
</div>

## Analysis

I built the SolidWorks model for each iteration and the drawings for laser cutting. In simulation, a 12.5 kg (27.5 lb) load produced:

- peak stress of about 4.95 × 10⁵ N/m²,
- a minimum factor of safety of 6.07,
- and 0.04 mm of deflection at the top edges.

<div class="figure-row">
<figure>
  <img src="{{ '/assets/img/sustainable-desk/stress.jpg' | relative_url }}" alt="Von Mises stress plot of the final design" loading="lazy">
  <figcaption>Von Mises stress in the final design.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/sustainable-desk/fea.jpg' | relative_url }}" alt="FEA displacement plot of an early design" loading="lazy">
  <figcaption>Displacement study of an early design.</figcaption>
</figure>
</div>

<div class="figure-row">
<figure>
  <img src="{{ '/assets/img/sustainable-desk/final-cad.jpg' | relative_url }}" alt="CAD of the final interlocking panel matrix" loading="lazy">
  <figcaption>The final design in CAD.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/sustainable-desk/panel-flat.jpg' | relative_url }}" alt="Flat laser-cut panel with slots and tabs" loading="lazy">
  <figcaption>A flat panel as sent to the laser cutter.</figcaption>
</figure>
</div>

## Results

It held 26 lb (11.8 kg) against a 20 lb requirement and failed at 28 lb. FEA had predicted a performance index of 104.08 and failure at 27.65 lb. The measured index of 98.25 is 94.4% of the prediction, and the structure survived a bit past the predicted failure load. It is fully recyclable and needs no other materials.

<div class="figure-row">
<figure>
  <img src="{{ '/assets/img/sustainable-desk/final-build.jpg' | relative_url }}" alt="The assembled chipboard desk structure" loading="lazy">
  <figcaption>The assembled structure.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/sustainable-desk/load-test.jpg' | relative_url }}" alt="A bin of tools loaded on top of the desk structure" loading="lazy">
  <figcaption>Load test with a bin of tools on top.</figcaption>
</figure>
</div>

## The report

{% include pdf-embed.html src="/assets/docs/sustainable-desk-report.pdf" title="Sustainable Desk Challenge report" %}
