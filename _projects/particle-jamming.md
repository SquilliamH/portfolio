---
title: Particle-Jamming Limb Stabilization
summary: A vacuum-tunable particle-jamming interface for stabilizing a limb quickly in the field, tested against strap splints.
kind: Course project
order: 5
role: Solo project, from design through testing
context: Soft Robotics course, UC San Diego
dates: Oct – Dec 2025
tools: [Vacuum pneumatics, FSR arrays, Arduino, MATLAB]
stats:
  - n: "1.6–4×"
    label: higher pull-out force than a strap splint
  - n: "~85 kPa"
    label: vacuum (25 inHg)
  - n: "3"
    label: FSRs measuring load distribution
  - n: "2 weeks"
    label: solo build and test
thumbnail: /assets/img/particle-jamming/glove.jpg
hero_caption: "The first prototype: a blue nitrile glove of coffee grounds on a vacuum line."
---

Field responders often have to stabilize an injured limb in an awkward position among debris. Straps and rigid splints concentrate pressure on bony or swollen spots, which hurts and risks more injury.

Particle jamming is another route. Granular material in a flexible membrane is soft and conforms to any shape. Pull a vacuum and it locks rigid in that shape.

## The prototype

I built it from what was in the lab:

- a blue nitrile glove filled with coffee grounds,
- the lab's vacuum line, on or off at about 25 inHg (no regulation),
- a limb surrogate made from a foam-wrapped pencil standing in for flesh and bone,
- a three-strap splint as the baseline.

## Two tests

<div class="figure-row">
<div class="mode-card">
  <h3>Pull-out</h3>
  <p>Pull the surrogate out with a crane scale and record the peak force. The strap was tensioned with hanging masses at three preloads.</p>
</div>
<div class="mode-card">
  <h3>Load spread</h3>
  <p>Three force-sensing resistors under the contact region, read on an Arduino. Each was calibrated at 100, 200, and 300 g, with a simple drift correction.</p>
</div>
</div>

<div class="figure-row">
<figure>
  <img src="{{ '/assets/img/particle-jamming/fsr-setup.jpg' | relative_url }}" alt="FSR array, Arduino, and calibration weights on the bench" loading="lazy">
  <figcaption>FSR calibration with reference weights.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/particle-jamming/fsr-array.jpg' | relative_url }}" alt="Two wooden blocks each carrying FSRs wired through a braided cable" loading="lazy">
  <figcaption>FSR arrays on the contact blocks.</figcaption>
</figure>
</div>

## Results

The jammed pad beat the strap at every preload. The strap tended to dig into the foam and slip suddenly, while the pad let go smoothly.

| Strap preload | Strap peak | Jamming peak | Ratio |
|---|---|---|---|
| 0.3 kg | 39 N | 157 N | 4.0× |
| 0.6 kg | 147 N | 343 N | 2.3× |
| 1.0 kg | 255 N | 412 N | 1.6× |

With the strap, nearly all the load landed on one FSR. With the jammer, all three read nonzero, so the load was shared.

## How far to trust it

{: .callout}
**The pull-out result is solid. The pressure result is suggestive.** The jammer's average load was lower, but the FSRs were inconsistent, so a better sensor is the next step. I also learned afterward that fast-acting jamming splints already exist, so the real value was learning the method and building the test setup.
