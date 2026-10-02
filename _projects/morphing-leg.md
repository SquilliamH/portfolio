---
title: Adaptive Morphing Leg for Search and Rescue
summary: A reconfigurable 5-bar leg that switches between fast traversal and high-force load dragging. Published at ICRA 2026.
kind: Research
order: 1
role: Mechanical design, prototyping, and experimental validation. Co-first author.
context: ARCLab, UC San Diego
dates: Jun 2024 – Present
tools: [SolidWorks, Ansys FEA, Python, CAN, CubeMars AK60-6]
stats:
  - n: "+83%"
    label: foot force from reconfiguring the same hardware (58 to 106 N)
  - n: "4.3×"
    label: link length range, 64 to 273 mm
  - n: "1:302"
    label: non-backdrivable capstan actuator
  - n: "2.3 kg"
    label: load dragged by the biped (5 lb minimum)
thumbnail: /assets/img/morphing-leg/thumb.jpg
hero_video: /assets/video/leg-loop.mp4
hero_caption: Bipedal prototype switching from traversal to load-dragging mode.
links:
  - label: Paper (arXiv)
    url: https://arxiv.org/abs/2511.10816
---

Search and rescue robots have two jobs that pull against each other. They need to cover rough ground fast, then pull a heavy load once they reach someone. A leg tuned for one job is usually poor at the other.

This leg gets both by changing shape. It is a 5-bar linkage whose link lengths change while the robot is running, so the same motors can trade speed for force on demand.

## Two modes, one leg

<div class="figure-row">
<div class="mode-card">
  <h3>Search mode</h3>
  <p>Passive links extend and the ground link retracts. The foot can reach farther, clear bigger obstacles, and move faster.</p>
</div>
<div class="mode-card">
  <h3>Rescue mode</h3>
  <p>Passive links retract and the ground link extends. The workspace shrinks into a region of high force, good for short dragging steps.</p>
</div>
</div>

A gear change alters the torque-speed ratio but not where the foot can reach. Changing link lengths does both.

## Results

I measured peak static pushing force at the foot with a crane scale, with motor bus current limited to 1 A and five trials per configuration.

| Configuration | Foot force | Change |
|---|---|---|
| Baseline | 58 ± 1 N | |
| Retracted passive links | 91 ± 1 N | +57% |
| Elongated ground link | 106 ± 2 N | +83% |

{: .callout}
**On the biped,** the robot follows a foot path, walks, then reconfigures and drags a load of at least 5 lb (2.3 kg) with the passive links retracted to 18 cm and the ground link extended to 13 cm.

<figure>
  <video controls muted loop playsinline preload="none" poster="{{ '/assets/img/morphing-leg/drag.jpg' | relative_url }}">
    <source src="{{ '/assets/video/leg-drag.mp4' | relative_url }}" type="video/mp4">
  </video>
  <figcaption>Rescue mode: the legs retract and the robot drags a load.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/morphing-leg/workspace-forces.jpg' | relative_url }}" alt="Simulated workspace force maps and measured foot forces for three configurations" loading="lazy">
  <figcaption>Simulated workspace and horizontal force for each configuration, next to the measured peak forces.</figcaption>
</figure>

## How it's built

### The testbed

A planar testbed with interchangeable link mounts lets me swap in different 5-bar geometries and measure each one. Two CubeMars AK60-6 BLDC motors drive the joints, and I compared measured force against the model's prediction (τ = Jᵀ·F).

<figure>
  <img src="{{ '/assets/img/morphing-leg/testbed.jpg' | relative_url }}" alt="Labeled photo of the planar 5-bar testbed" loading="lazy">
  <figcaption>The testbed: AK60-6 motors on an adjustable frame, a manually adjustable 5-bar linkage, and a crane scale on a rail-mounted platform.</figcaption>
</figure>

### Capstan-driven reconfiguration

A worm-gear motor winds a tensioned steel cable around a spool to change a link's length from 64 to 273 mm.

- **It can't be backdriven,** so the leg holds its shape under load without drawing power.
- **The cable drive is smooth** and has no backlash.

<figure>
  <img src="{{ '/assets/img/morphing-leg/capstan.jpg' | relative_url }}" alt="Capstan reconfiguration module with steel cable and worm-gear motor" loading="lazy">
  <figcaption>The capstan module: a 1:302 worm-gear motor winds steel cable along the link, with guide bearings and a cable tensioner.</figcaption>
</figure>

### Control and the biped

I wrote the Python position control that runs over CAN and coordinates the joint motors with the gait cycle and the reconfiguration actuators. The biped has four AK60-6 joint motors, capstan drives for the passive links, and a stepper-driven linear stage for the ground link.

<figure>
  <img src="{{ '/assets/img/morphing-leg/biped.jpg' | relative_url }}" alt="Bipedal prototype on its boom arm" loading="lazy">
  <figcaption>The bipedal prototype, hung from a boom arm for stability during testing.</figcaption>
</figure>

## What didn't work yet

- The biped was tested on a boom arm, not free-standing.
- The feet slipped during dynamic load dragging.
- Terrain interaction and friction aren't modeled.
- High-force regions sit near singularities and have to be avoided.

These are the gaps the next stage targets.

## Where it came from

The project began as my senior capstone (MAE 156A and 156B), sponsored by ARCLab. The brief was a hexapod leg, made from wood and 3D-printed parts, that could cover ground quickly and also drag a heavy load.

Our team set out to compare three scaled leg designs: a 5-bar pantograph, a swinging 4-bar, and a modified Theo Jansen linkage with an extra degree of freedom. The plan was to use kinematic simulation to set each walk cycle, run them under PID control, and rank them by maximum pushing force in high-torque mode against stride length in high-speed mode. The 5-bar is the design that went forward.

## ICRA 2026

The paper was accepted to ICRA 2026, and I presented the poster there.

<figure>
  <img src="{{ '/assets/img/morphing-leg/icra-poster.jpg' | relative_url }}" alt="Presenting the morphing-leg poster at ICRA 2026" loading="lazy">
  <figcaption>At the ICRA 2026 poster session.</figcaption>
</figure>

## What's next

The single-leg result doesn't say how the legs should work together with the body. I've since built a formal optimization of the leg's geometry and footpath, and I'm planning a reinforcement learning approach across all legs. It's covered in [Hexapod Rescue Robot and Leg Optimization]({{ '/projects/hexapod-optimization/' | relative_url }}).
