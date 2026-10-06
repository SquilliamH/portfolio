---
title: Hexapod Leg Senior Design Project
summary: "The senior capstone that started the legged rescue robot: a team of five picks a leg mechanism for a hexapod that can carry a person, and builds a test bed to prove it."
group: research
blurb: "The capstone that started the legged robot: choosing a leg for a hexapod that carries a person."
card_role: "Proposed the project as a capstone; team of five."
kind: Senior capstone, phase 1
order: 2
phase: 1
role: Team of five with Giovanni Bernal Ramirez, Hwuiyun Park, Elias Smith, and Lucas Yager. I asked my lab mentor to offer this project as a capstone, so it could be the first step toward a full hexapod.
context: MAE 156A/B, sponsored by ARCLab, UC San Diego
context_url: https://ucsdarclab.com/
dates: Jan – Jun 2025
tools: [5-bar linkage design, test bed design, force-torque testing]
result: "The team chose a 5-bar pantograph leg whose ground-link actuator changes how hard it can push, and built a test bed to measure that."
links:
  - label: Team 37 project site
    url: https://sites.google.com/eng.ucsd.edu/mae156b-2025spring-team37
---

This was the first phase of the legged rescue robot. The lab wanted a hexapod that could cross rough ground and also drag a person out, and I asked my lab mentor to offer the first step as a senior capstone. The project was part of a Department of Defense (TATRC) funded effort at ARCLab.

## The problem

The leg has two jobs that pull against each other.

- **Move fast.** Cross rough terrain at about human walking speed, 1.2 to 1.4 m/s.
- **Push hard.** Carry or drag a 90 kg person, while also supporting the chassis and two robotic arms.

A fixed leg tuned for one of those is poor at the other. The brief was a leg that can switch between two configurations, one for speed and one for load.

## The design

We settled on a **5-bar pantograph linkage**. It has planar kinematics and high stiffness, and it can shift its mechanical advantage by moving a single ground-link actuator.

## The test bed

To compare configurations, we built a modular test bed.

- **Linear bearing rails** to constrain the motion.
- **A counterweight system** to offset the weight of the test bed itself.
- **A force-torque sensor under the foot** to measure ground reaction forces.

All configurations were tested at a foot velocity of 0.2 m/s.

## What we found

{: .callout}
**Stride length** was greatest when the driven links (A and D) were lengthened. **Pushing force** changed the most, and stayed stable, when the ground link was lengthened.

Lengthening the driven links also made the pushing force unstable, which we judged undesirable for the final design. So the ground link became the lever for force, and that choice carried straight into the first paper.

## What came next

- **Phase 2:** the lab and I took the 5-bar leg into hardware and tested it on a bipedal prototype. That became the ICRA 2026 paper: [Adaptive Morphing Leg]({{ '/projects/morphing-leg/' | relative_url }}).
- **Phase 3:** optimizing the leg geometry and footpath, then learning behavior across all six legs: [Hexapod Rescue Robot and Leg Optimization]({{ '/projects/hexapod-optimization/' | relative_url }}).

## The team's full write-up

The team site has the final report, executive summary, CAD, parts list, and code.

<p class="project-links"><a class="btn" href="https://sites.google.com/eng.ucsd.edu/mae156b-2025spring-team37/final-design">Final design</a> <a class="btn" href="https://sites.google.com/eng.ucsd.edu/mae156b-2025spring-team37/reports/final-report">Final report</a> <a class="btn" href="https://sites.google.com/eng.ucsd.edu/mae156b-2025spring-team37/reports/cad">CAD</a></p>

<!-- TODO(William): add (1) your specific part of the team's work, (2) a CAD render or test bed photo from the team site or poster in Portfolio_Stuff, and (3) any measured numbers you want to quote (forces, stride lengths). -->
