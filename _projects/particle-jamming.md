---
title: Particle-Jamming Limb Stabilization
summary: A vacuum-tunable particle-jamming interface for stabilizing a limb quickly in the field, tested against strap splints.
kind: Course project
order: 3
role: Solo project, design through testing
context: Course project, UC San Diego
dates: Oct – Dec 2025
tools: [Vacuum pneumatics, FSR arrays, Arduino, MATLAB]
specs:
  - label: Duration
    value: 2-week solo project
thumbnail:
---

Field responders often have to stabilize a limb in an awkward posture among debris. Rigid splints and straps concentrate pressure on bony or swollen areas, which causes pain and risks secondary injury. Particle jamming offers another route: granular material in a flexible membrane is soft and conforms to any shape, then becomes rigid and holds that shape when a vacuum is pulled.

## Prototype

I built the first device from parts lying around the lab: a glove filled with coffee grounds, lab pneumatic lines for the vacuum, and a limb surrogate made from a pencil wrapped in foam to stand in for bone and flesh. There was no vacuum regulation, only on and off.

## Measurement

To compare it with a strap splint, I built an FSR array read through voltage-divider circuits to estimate how contact load is distributed around the limb, and ran a pull-out resistance test.

## Results

The particle-jamming splint held onto the limb better than the strap in the pull-out test. The pressure-distribution data showed a lower average load for the jammer, but the FSRs gave inconsistent readings, so I treat that result as suggestive rather than conclusive. A different sensor would be the next step. I also learned afterward that fast-acting jamming splints already exist, so this project was valuable mainly as a way to learn the method and build the test setup.
