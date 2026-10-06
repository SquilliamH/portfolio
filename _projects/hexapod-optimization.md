---
title: Hexapod Rescue Robot
summary: "The full legged robot: one morphing leg design for both rescue and search modes, optimized in simulation, with hardware and demos next."
group: research
blurb: "One leg for both rescue and search modes, optimized in simulation, now heading to the full hexapod."
card_role: "Wrote the leg model and optimization, and designed the hexapod."
kind: Research, phase 3
order: 3
phase: 3
role: Leg model and optimization, mass budget and actuator selection for the hexapod.
context: ARCLab, UC San Diego
context_url: https://ucsdarclab.com/
dates: 2025 – Present
tools: [Python, GPU computing, MuJoCo, SolidWorks, CubeMars AK60-6]
result: "In simulation, a single leg with one shared foot works in both modes: in rescue mode it can push about 2.5 times harder than a rubber foot can grip, and in search mode it takes a larger step."
thumbnail: /assets/img/hexapod/hex-thumb.jpg
hide_hero: true
---

This is phase 3 of the legged robot, after the [senior capstone]({{ '/projects/senior-design-leg/' | relative_url }}) and the [first paper]({{ '/projects/morphing-leg/' | relative_url }}). The first paper showed that changing a 5-bar leg's link lengths changes both its reach and its force. This phase asks what the leg should actually look like, and builds the hexapod that will use it.

{: .callout}
**Status: in progress.** The numbers below come from a quasi-static simulation, not hardware. The next steps are building the full robot and showing what the legs can do with it.

## One leg, two modes

<figure>
  <img src="{{ '/assets/img/hexapod/final-both-modes.jpg' | relative_url }}" alt="The optimized leg in rescue mode and in search mode, drawn at the same scale" loading="lazy">
  <figcaption>The same leg in rescue mode (left) and search mode (right), drawn at the same scale. Faint poses are the start and end of the stance and the top of the swing; the red line is the foot pushing along the ground.</figcaption>
</figure>

<div class="split wide" markdown="1">
<div markdown="1">
### Rescue mode

The goal is to drag a person without the foot slipping, so the leg is tuned for its **weakest** point in the stance, not its average. In simulation it can push about **2.5 times harder than a rubber foot can grip**. That makes foot grip, not leg strength, the limit on how much it can drag.
</div>
<div markdown="1">
### Search mode

The goal is to cover ground, so the leg is tuned for the **largest step** it can take while still supporting the robot. In simulation that is a step of about **51 cm²** (roughly a 10 cm stride and 5 cm of lift), with margin to spare.
</div>
</div>

Both modes use the same motors and the same foot. Only the link geometry changes, and the changes are within what the hardware can build: the design still works when any link is off by 2 mm.

## How it was done

I generalized the leg model so the links no longer have to be symmetric, then set up the two modes as optimization problems and solved them on a GPU. A lot of the work was checking the optimizer against a slow, simple solver, and fixing places where the first version scored good designs too low.

## The hexapod

The robot is a six-legged platform with the morphing leg on every leg. The mass budget comes to about **10.8 kg**:

- twelve CubeMars AK60-6 motors (about 4.6 kg),
- an aluminum square-tube body,
- 3D-printed joints and mounts,
- laser-cut plywood links,
- and the electronics and battery.

I chose the AK60-6 after comparing eleven motors on price, torque, weight, size, and whether a driver and encoder come built in. It is a good fit for a robot this light.

## What's next

The next step is the full hexapod: first dragging demos, then showing what the legs can do beyond dragging. Robot arms tend to be weak, so the legs may be able to help with tasks like rolling a person over or moving heavy objects. The exact plan is still taking shape.
