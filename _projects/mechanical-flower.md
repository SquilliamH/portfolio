---
title: Mechanical Flower
summary: A modular, gear-actuated 3D-printed flower that blooms, made as interactive art to explore digital fabrication.
kind: Course project
order: 14
role: Individual project; design, CAD, and prototyping
context: VIS 146B Digital Fabrication, UC San Diego
dates: Winter 2025
tools: [Fusion 360, SolidWorks, FDM 3D printing, crossed helical gears]
specs:
  - label: Base diameter
    value: 7.5 cm (reduced from 10 cm)
  - label: Gears
    value: 42-tooth central, 6-tooth petals
  - label: Gear module
    value: 1 mm at 45° helix
thumbnail:
---

This was an art class, and I used it to see how far my mechanical design skills could go toward making something beautiful. The idea was a flower built from interchangeable parts, whose petals open and close like a bloom, inspired by the mechanical sculptures of David C. Roy. The first version proved the modular concept but had no actuation. This one added the blooming mechanism.

## Design

I shrank the base from 10 cm to 7.5 cm so it looked like a flower, and replaced the Lego-style clip-and-rod petal mounts with a sturdier through-hole and pin hinge that doesn't rely on the plastic flexing. The stem is made of stackable segments joined by screws and nuts, which I shaped to read as thorns.

The bloom is driven by gears. I first considered worm gears, but a worm can't be backdriven, so a central worm wheel could never turn the petals. I switched to crossed helical (screw) gears with a 1 mm module and a 45° helix angle, which are smooth and backdrivable: a 42-tooth, 5 mm central gear driving 6-tooth, 10 mm petal gears. Each petal comes in two variants with the gear rotated 60° from the other so the teeth engage consistently around the central gear.

## Prototyping

I had planned to try injection molding and resin printing, but the shop told me a mold would be too slow and expensive for the quarter, and resin printer access needed a workshop that wasn't offered. So I iterated in PLA on an FDM printer, with finer layers and part orientations chosen to ease support removal.

The hard part was transmitting torque to the central gear without slipping. The first version used a steel pin and hubs with set screws, and the hub slipped on the round pin. The second used a printed shaft, which was too weak and sheared at the screw holes, and the central gear wobbled. The third used a D-shaft made by grinding a flat on a stainless pin, with printed hubs and a pressed-in bearing, which worked.

## Status

The central actuation mechanism works, but I ran out of time before assembling the full set of petals, so the flower hasn't been built and tested as a complete piece. If I continued, I would move the gears to resin printing for precision.
