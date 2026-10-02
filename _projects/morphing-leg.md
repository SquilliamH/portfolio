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
  - label: Measured foot force
    value: 58 N baseline, 106 N elongated
  - label: Actuator reduction
    value: 1:302 (non-backdrivable)
  - label: Force gain from reconfiguration
    value: +57% (retracted links), +83% (elongated ground link)
  - label: Link extension ratio
    value: 4.3× (64 to 273 mm)
  - label: Dragged load
    value: At least 2.3 kg (5 lb)
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

## Origins

The project began as my senior capstone in MAE 156A and 156B, the two-quarter mechanical design sequence, sponsored by ARCLab. The brief was to design a hexapod leg, built from wood and 3D-printed parts, that could cover ground quickly and also drag a heavy load, with a fixture to test and compare candidate designs. Our team set out to build three scaled leg prototypes: a 5-bar pantograph, a swinging 4-bar, and a modified Theo Jansen linkage with an added degree of freedom. We planned to use kinematic simulation to prescribe a walk cycle for each, run them under PID control, and rank them by the ratio of maximum pushing force in high-torque mode to stride length in high-speed mode. The 5-bar design is the one that carried forward into the research below.

## Testbed

To check the simulation against reality, I built a planar testbed with interchangeable link mounts so different 5-bar geometries could be swapped in and measured. Two Cubemars AK60-6 BLDC motors drive the joints. I ran force and displacement tests across reconfiguration states and compared the measured force output with the model predictions.

<figure>
  <img src="{{ '/assets/img/morphing-leg/testbed.jpg' | relative_url }}" alt="Labeled photo of the planar 5-bar testbed" loading="lazy">
  <figcaption>The testbed: AK60-6 motors on an adjustable frame, a manually adjustable 5-bar linkage, and a crane scale on a rail-mounted platform to read foot force.</figcaption>
</figure>

## Capstan-driven reconfiguration

The leg changes geometry with a non-backdrivable capstan actuator: a worm-gear motor winds a tensioned steel cable around a spool to vary link length between 64 and 273 mm. Because it can't be backdriven, the leg holds its configuration under load without drawing power, and the cable drive keeps the motion smooth and free of backlash.

<figure>
  <img src="{{ '/assets/img/morphing-leg/capstan.jpg' | relative_url }}" alt="Capstan reconfiguration module with steel cable and worm-gear motor" loading="lazy">
  <figcaption>The capstan module: a worm-gear motor (1:302) winds steel cable along the link, with guide bearings and a cable tensioner.</figcaption>
</figure>

## Control and the bipedal prototype

I wrote Python position control over CAN to coordinate the joint motors with the gait cycle and the reconfiguration actuators. The bipedal prototype uses four AK60-6 motors for the joints, capstan drives to change the passive link lengths, and a stepper-driven linear stage to change the ground link. It walks in one configuration, reconfigures, and continues in the other.

## Results

The idea is a geometric transformation rather than a gear shift. In search mode the passive links extend and the ground link retracts, which gives a larger workspace, more obstacle clearance, and faster movement. In rescue mode the passive links retract and the ground link extends, which concentrates the workspace into regions of higher force for short dragging steps. A gear change alters the torque-speed ratio but not where the foot can reach; changing link lengths does both.

Simulation, using the Jacobian to map joint torques to foot force (τ = Jᵀ·F), showed how each link length shifts the workspace and force distribution. On the testbed, I measured peak static pushing force at the foot with a crane scale, with the motor bus current limited to 1 A and five trials per configuration:

- Baseline: 58 ± 1 N
- Retracted passive links: 91 ± 1 N (about 57% higher)
- Elongated ground link: 106 ± 2 N (about 83% higher)

On the bipedal prototype, the robot follows a desired foot path and walks, and it drags a weight of at least 5 lb (about 2.3 kg) with the passive links retracted to 18 cm and the ground link extended to 13 cm. The prototype hangs from a boom arm for stability during testing.

<figure>
  <img src="{{ '/assets/img/morphing-leg/workspace-forces.jpg' | relative_url }}" alt="Simulated workspace force maps and measured foot forces for three configurations" loading="lazy">
  <figcaption>Simulated workspace and horizontal force for the baseline, retracted-passive-link, and elongated-ground-link configurations, alongside the measured peak forces.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/morphing-leg/biped.jpg' | relative_url }}" alt="Bipedal prototype on its boom arm" loading="lazy">
  <figcaption>The bipedal prototype, hung from a boom arm during testing.</figcaption>
</figure>

<figure>
  <video controls muted loop playsinline preload="none" poster="{{ '/assets/img/morphing-leg/drag.jpg' | relative_url }}">
    <source src="{{ '/assets/video/leg-drag.mp4' | relative_url }}" type="video/mp4">
  </video>
  <figcaption>Rescue mode: the legs retract and the robot drags a load.</figcaption>
</figure>

## Limitations

The bipedal prototype was tested on a boom arm rather than free-standing, and we saw the feet slip during dynamic load dragging. Terrain interaction and friction aren't modeled yet, and high-force regions of the workspace also have to stay away from singularities. Those are the main gaps the next stage of work targets.

## ICRA 2026

The work was accepted to ICRA 2026 and I presented the poster in person.

<figure>
  <img src="{{ '/assets/img/morphing-leg/icra-poster.jpg' | relative_url }}" alt="Presenting the morphing-leg poster at ICRA 2026" loading="lazy">
  <figcaption>At the ICRA 2026 poster session.</figcaption>
</figure>

## What's next

Single-leg optimization showed its limits once the legs had to work together with the chassis. I've since built a formal optimization of the leg geometry and footpath, and I'm scoping a reinforcement learning approach that optimizes across all legs and the body at once. That work, and the hexapod it targets, is described in [Hexapod Rescue Robot and Leg Optimization]({{ '/projects/hexapod-optimization/' | relative_url }}).
