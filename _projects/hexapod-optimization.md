---
title: Hexapod Rescue Robot and Leg Optimization
summary: A formal optimization of the morphing leg's geometry and footpath for search and rescue modes, and the design of the hexapod it will run on.
kind: Research
order: 2
role: Kinematic model, optimization framework, hexapod design and analysis
context: ARCLab, UC San Diego
context_url: https://ucsdarclab.com/
dates: 2025 – Present
tools: [Python, MATLAB, SolidWorks, MuJoCo, CubeMars AK60-6]
stats:
  - n: "7"
    label: design variables, with asymmetric links and an ankle offset
  - n: "12.6×"
    label: larger search-mode step than the rescue reference (simulated)
  - n: "~65 N"
    label: friction-limited drag force of the 11 kg robot (simulated)
  - n: "10.76 kg"
    label: hexapod mass budget, against an 11 kg target
thumbnail: /assets/img/hexapod/search-mode.jpg
hide_hero: true
---

The [morphing leg]({{ '/projects/morphing-leg/' | relative_url }}) showed that changing a five-bar linkage's geometry changes both its workspace and its force. But the geometry I tested was symmetric and picked by hand.

This project asks what geometry is actually best for each mode, and designs the hexapod that will use it.

{: .callout}
**A note on the numbers.** Force and step results below come from a quasi-static simulation, not hardware.

## A more general leg model

<div class="split wide" markdown="1">
<div markdown="1">
I generalized the kinematics so the links don't have to be symmetric and the ankle can sit at an offset angle. That gives seven design variables: the two actuated links, the two passive links, the motor separation, the ankle link, and the ankle offset.

- I derived the forward kinematics, inverse kinematics, and the foot Jacobian.
- I checked the model by confirming it reduces to the standard symmetric 5-bar when the new terms are zero.
- The ankle offset rotates the leg's force ellipse without changing its size, which separates force direction from force magnitude.
</div>
<figure>
  <img src="{{ '/assets/img/hexapod/force-heatmaps.jpg' | relative_url }}" alt="Workspace force heatmaps for several link-length configurations" loading="lazy">
  <figcaption>Horizontal force across the workspace as each link is changed in turn.</figcaption>
</figure>
</div>

## Rescue mode: the weakest point decides

<div class="split flip wide" markdown="1">
<div markdown="1">
A drag fails at the weakest point of the stance, not on average. So the optimizer maximizes the **minimum** horizontal force across the whole stance path.

Strong regions of a 5-bar's workspace sit near singularities, where force transmission becomes unreliable. The optimizer is held to a Jacobian condition number of 10 or less, a bound taken from the AK60-6's current-sensing accuracy rather than picked arbitrarily.

Other constraints: inverse kinematics must be feasible, the foot must clear the ground, and forward and inverse kinematics must agree. The objective is non-smooth, so I used multi-seed differential evolution followed by a Powell refinement.
</div>
<figure>
  <img src="{{ '/assets/img/hexapod/condition-number.jpg' | relative_url }}" alt="Workspace map of the Jacobian condition number" loading="lazy">
  <figcaption>Jacobian condition number across the workspace. The optimizer stays out of the magenta regions near singularities.</figcaption>
</figure>
</div>

## The real limit is friction

With six legs, at least three in contact, and two motors per leg, the single-leg result scales to the whole robot.

- **Motor limit:** at about 26 N per N·m of torque, roughly 468 N of drag force.
- **Friction limit:** a rubber foot on dry concrete (μ = 0.6) under an 11 kg robot slips at about 65 N.
- **Target:** dragging an 8 kg load (a scaled stand-in for a casualty) needs about 47 N, leaving a 38% margin before slipping.

{: .callout}
**The design is friction-limited.** Robot weight and foot friction, not motor torque or leg geometry, decide how much it can drag. Reducing robot weight directly reduces drag capacity.

## Search mode and footpath shape

For search mode the same framework maximizes stride length and chassis clearance, subject to a minimum vertical force. In simulation the optimized geometry gives a 44.3 cm stride and 16.2 cm step height. That is a 718 cm² step envelope against 57 cm² for the rescue reference, about 12.6 times larger.

<figure>
  <img src="{{ '/assets/img/hexapod/search-mode.jpg' | relative_url }}" alt="Search-mode optimization results compared with the rescue-mode reference" loading="lazy">
  <figcaption>Search-mode optimization against the rescue reference: geometry, step envelope, and force along the stance.</figcaption>
</figure>

Optimized links: 14.6, 11.8, 23.5, 23.0, and 2.8 cm, a 3.9 cm motor separation, and an ankle offset of −11.4°.

### Choosing the swing path

<div class="split wide" markdown="1">
<div markdown="1">
I compared six candidate swing paths: a capsule, a pure half-ellipse, a cycloid with blended ends, the raw cycloid, an ellipse with Bézier blends, and a degree-6 polynomial. The pure half-ellipse won.

- **It needs no blend.** Its tangent is vertical at the ground, so the foot touches down moving horizontally.
- **Bézier blends fail by construction.** A quintic Bézier that turns about 90° in a short distance always produces an inflection point.
- **A raw cycloid has a cusp** with unbounded curvature at touchdown, which a real controller can't follow. I made sure not to hide that by resampling before differentiating.
</div>
<figure>
  <img src="{{ '/assets/img/hexapod/search-footpath.jpg' | relative_url }}" alt="Kinematic analysis of the search-mode footpath" loading="lazy">
  <figcaption>Speed, acceleration, and curvature of the chosen swing path against the raw cycloid.</figcaption>
</figure>
</div>

## The hexapod

The platform is a six-legged robot with the morphing 5-bar on every leg. The mass budget comes to 10.76 kg against an 11 kg target:

- **Twelve AK60-6 motors:** 4.56 kg
- **Aluminum square-tube body:** 2.10 kg
- **PLA joints and mounts:** 2.00 kg
- **Electronics and battery:** 1.60 kg
- **Laser-cut plywood links:** 0.50 kg

I chose the actuator by comparing eleven candidates on price, rated torque, weight, size, and whether a driver and encoder are built in, including the Eaglepower LA8308 and the CubeMars AK60, AK70, AK80, and AK90 families. The AK60-6 (3 N·m rated, 9 N·m peak, 6:1 planetary, 380 g) was the best fit for a robot this light.

## What's next

The quasi-static model prescribes how the robot walks and then optimizes the geometry for that gait, so the answer is only optimal for the assumed behavior. A real hexapod also chooses its posture, leg coordination, and contacts.

The next stage is a bilevel reinforcement learning framework. The outer loop searches over leg geometry, starting from this result instead of at random. The inner loop trains a walking policy for each candidate, with separate objectives for search and rescue.

The central question: **does the geometry found by optimization still hold once the robot is free to discover its own behavior?** If the two differ, learning found something the optimizer couldn't. If they agree, the optimum has been validated independently. I proposed the optimization stage as a funding proposal for MAE 269 with Dillan Selitsch.
