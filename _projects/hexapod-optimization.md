---
title: Hexapod Rescue Robot and Leg Optimization
summary: A formal optimization of the morphing leg's geometry and footpath for search and rescue modes, and the design of the hexapod it will run on.
kind: Research
order: 2
role: Kinematic model, optimization framework, hexapod design and analysis
context: ARCLab, UC San Diego
dates: 2025 – Present
tools: [Python, MATLAB, SolidWorks, MuJoCo, CubeMars AK60-6]
specs:
  - label: Design variables
    value: 7 (asymmetric links and ankle offset)
  - label: Hexapod mass budget
    value: 10.76 kg of an 11 kg target
  - label: Search-mode step area
    value: 12.6× the rescue-mode step (simulated)
  - label: Rescue-mode limit
    value: Friction, about 65 N (simulated)
thumbnail: /assets/img/hexapod/search-mode.jpg
hero_caption: Simulated search-mode result. The optimized geometry (left) takes steps 12.6 times larger than the rescue-mode reference (middle).
---

The [morphing leg]({{ '/projects/morphing-leg/' | relative_url }}) showed that changing a five-bar linkage's geometry changes both its workspace and its force, but the geometry I tested was a fixed, symmetric one picked by hand. This project asks what geometry is actually best for each mode, and builds the hexapod that will carry the answer. Everything below on force and step size comes from a quasi-static simulation, not hardware.

## Generalizing the model

I generalized the leg's kinematics so the links no longer have to be symmetric and the ankle can sit at an offset angle. That gives seven design variables: the two actuated link lengths, the two passive ones, the motor separation, the ankle link length, and the ankle offset angle. I derived the forward kinematics, the inverse kinematics, and the foot Jacobian, and checked the model by confirming it reduces to the standard symmetric five-bar when the asymmetric terms are set to zero.

The ankle offset is useful because it rotates the leg's force ellipse without changing its size, which separates the direction of the force from its magnitude.

## Optimizing for rescue mode

When the robot drags a casualty, the drag fails at the weakest point in the stance phase, not on average. So the optimizer maximizes the minimum horizontal force across the whole stance path (a minimax formulation) over a set of stance points.

High-force regions of a five-bar's workspace tend to sit next to singularities, where force transmission becomes unreliable, so the optimizer is constrained to a Jacobian condition number of at most 10. That bound comes from the AK60-6 motors' current sensing accuracy rather than being picked arbitrarily. Other constraints are inverse-kinematics feasibility, ground clearance, and a forward and inverse kinematics consistency check. Since the objective is non-smooth, I used multi-seed differential evolution followed by a Powell refinement.

<figure>
  <img src="{{ '/assets/img/hexapod/condition-number.jpg' | relative_url }}" alt="Workspace map of the Jacobian condition number" loading="lazy">
  <figcaption>The Jacobian condition number across the leg's workspace. The optimizer is kept out of the high-condition (magenta) regions near singularities.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/hexapod/force-heatmaps.jpg' | relative_url }}" alt="Workspace force heatmaps for several link-length configurations" loading="lazy">
  <figcaption>Horizontal force across the workspace for the baseline and for each link modified in turn, which shows which changes help.</figcaption>
</figure>

## Where the real limit is

The weight budget changes what matters. With six legs, at least three in contact, and two motors per leg, the single-leg result scales to the whole robot. At the optimized force of about 26 N per N·m of motor torque, the motors could produce roughly 468 N of drag force. But friction caps it far lower: with a rubber foot on dry concrete (μ = 0.6) and an 11 kg robot, the slip limit is only about 65 N.

That makes the design friction-limited. Robot weight and foot friction, not motor torque or leg geometry, are what set how much it can drag. For a target load of 8 kg (a scaled stand-in for a casualty), the required force is about 47 N, which leaves roughly a 38% margin before the feet slip. It also means that reducing robot weight directly reduces how much it can drag.

## Search mode and footpath shape

For search mode the same framework maximizes stride length and chassis clearance, subject to a minimum vertical force. In simulation the optimized geometry (links of 14.6, 11.8, 23.5, 23.0, and 2.8 cm, a 3.9 cm motor separation, and an ankle offset of −11.4°) gives a 44.3 cm stride and 16.2 cm step height. That is a 718 cm² step envelope against 57 cm² for the rescue-mode reference, about 12.6 times larger.

<figure>
  <img src="{{ '/assets/img/hexapod/search-mode.jpg' | relative_url }}" alt="Search-mode optimization results compared with the rescue-mode reference" loading="lazy">
  <figcaption>Search-mode optimization against the rescue-mode reference: geometry, step envelope, and force along the stance.</figcaption>
</figure>

I also compared six candidate swing paths for the foot: a capsule, a pure half-ellipse, a cycloid with blended ends, the raw cycloid, an ellipse with Bézier blends, and a degree-6 polynomial. The pure half-ellipse won. Its tangent is exactly vertical where it meets the ground, so the foot touches down with horizontal velocity and no blend is needed. The blended alternatives failed in an instructive way: a quintic Bézier that has to turn about 90° in a short distance always produces an inflection point, which is a property of the Bézier basis rather than a tuning problem. A raw cycloid has a cusp with unbounded curvature at touchdown, which a real controller can't follow, and part of the analysis was making sure not to hide that by resampling the data before differentiating.

<figure>
  <img src="{{ '/assets/img/hexapod/search-footpath.jpg' | relative_url }}" alt="Kinematic analysis of the search-mode footpath" loading="lazy">
  <figcaption>Speed, acceleration, and curvature of the chosen swing path against the raw cycloid.</figcaption>
</figure>

## The hexapod

The platform is a six-legged robot with the morphing five-bar on every leg. Its mass budget comes to 10.76 kg against an 11 kg target: twelve AK60-6 motors at 4.56 kg, a 2.1 kg aluminum square-tube body, 2.0 kg of PLA joints and mounts, 1.6 kg of electronics and battery, and 0.5 kg of laser-cut plywood links.

I chose the actuator by comparing eleven candidates on price, rated torque, weight, size, and whether they come with a driver and encoder, including the Eaglepower LA8308 and the CubeMars AK60, AK70, AK80, and AK90 families. The AK60-6 (3 N·m rated, 9 N·m peak, 6:1 planetary, 380 g, driver and single encoder built in) was the best fit for a robot this light.

## What's next

The quasi-static model prescribes how the robot walks and then optimizes the geometry for that behavior, so its answer is only optimal for the assumed gait. A real hexapod can also choose its body posture, leg coordination, and contact pattern. The next stage is a bilevel reinforcement learning framework: the outer loop searches over leg geometry, starting from the quasi-static result instead of at random, and the inner loop trains a locomotion policy for each candidate, with separate objectives for search and rescue.

The central question is whether the geometry found by optimization still holds once the robot is free to discover its own behavior. If the two differ, learning found something the optimizer couldn't anticipate; if they agree, the analytic optimum has been validated independently. Either result is useful. I proposed the optimization stage as a funding proposal for MAE 269 with Dillan Selitsch.
