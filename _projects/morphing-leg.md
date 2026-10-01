---
# Front matter: the layout reads these fields. The Markdown below the
# second --- line is the page body.
title: Adaptive Morphing Leg for Search and Rescue
summary: A reconfigurable 5-bar leg that switches between fast traversal and high-force load dragging. ICRA 2026.
kind: Research
order: 1
role: Mechanical design, prototyping, and experimental validation. Co-first author.
context: ARCLab, UC San Diego
dates: Jun 2024 – Present
tools: [SolidWorks, Ansys FEA, Python, CAN, Cubemars AK60-6]
specs:
  - label: Link length range
    value: 64–273 mm
  - label: Joint motors
    value: 2× AK60-6, 3 Nm
  - label: Simulated foot force
    value: 58 N baseline, up to 106 N
  - label: Actuator reduction
    value: 1:302 (non-backdrivable)
thumbnail: /assets/img/morphing-leg/thumb.jpg
hero_video: /assets/video/leg-loop.mp4
hero_caption: Bipedal prototype switching from traversal to load-dragging mode.
links:
  - label: Paper (arXiv)
    url: https://arxiv.org/abs/2511.10816
  # - label: Full video
  #   url: https://youtu.be/...
---

Search and rescue robots need to cover rough ground quickly, then pull or carry heavy loads once they reach a victim. A leg tuned for one of those jobs is usually poor at the other. This project uses a 5-bar linkage whose geometry can change while the robot is running, so the same leg can trade speed for force on demand.

I led the mechanical design, prototyping, and testing that took the linkage from simulation to working hardware, first as a single-leg testbed and then as a bipedal robot that switches modes in real time.

## Testbed

To check the simulation against reality, I built a planar testbed with interchangeable link mounts so different 5-bar geometries could be swapped in and measured. Two Cubemars AK60-6 BLDC motors drive the joints. I ran force and displacement tests across reconfiguration states and compared the measured force output with the model predictions.

<!-- Add a figure like this once you have images:
<figure>
  <img src="{{ '/assets/img/morphing-leg/testbed.jpg' | relative_url }}" alt="Planar 5-bar testbed with interchangeable link mounts">
  <figcaption>Testbed with interchangeable link mounts for evaluating different geometries.</figcaption>
</figure>
-->

## Capstan-driven reconfiguration

The leg changes geometry with a non-backdrivable capstan actuator: a worm-gear motor winds a tensioned steel cable around a spool to vary link length between 64 and 273 mm. Because it can't be backdriven, the leg holds its configuration under load without drawing power, and the cable drive keeps the motion smooth and free of backlash.

## Control and the bipedal prototype

I wrote Python position control over CAN to coordinate the joint motors with the gait cycle and the reconfiguration actuator. On the bipedal prototype, this let the robot walk in one configuration, reconfigure, and continue in the other.

<figure>
  <video controls muted loop playsinline preload="none" poster="{{ '/assets/img/morphing-leg/drag.jpg' | relative_url }}">
    <source src="{{ '/assets/video/leg-drag.mp4' | relative_url }}" type="video/mp4">
  </video>
  <figcaption>Rescue mode: the legs retract and the robot drags a load.</figcaption>
</figure>

## Results

The idea is a geometric transformation rather than a gear shift. In search mode the passive links extend and the ground link retracts, which gives a larger workspace, more obstacle clearance, and faster movement. In rescue mode the passive links retract and the ground link extends, which concentrates the workspace into regions of higher force for short dragging steps. A gear change alters the torque-speed ratio but not where the foot can reach; changing link lengths does both.

In simulation, using the Jacobian to map joint torques to foot force (τ = Jᵀ·F), three configurations gave:

- Baseline: 58 N
- Retracted passive links: 91 N (about 57% higher)
- Elongated ground link: 106 N (about 83% higher)

On the bipedal prototype, the robot walks with longer legs and more ground clearance in search mode, then shortens its legs and drags a 5 lb weight in rescue mode. The prototype is attached to a boom arm for stability during testing. <!-- TODO: how closely did the measured testbed forces match these simulated values? -->

## What's next

Single-leg optimization showed its limits once the legs had to work together with the chassis, so I'm now scoping a reinforcement learning approach that optimizes across all legs and the body at once.
