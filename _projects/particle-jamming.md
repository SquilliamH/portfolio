---
title: Particle-Jamming Limb Stabilization
summary: A vacuum-tunable particle-jamming interface for stabilizing a limb quickly in the field, tested against strap splints.
kind: Course project
order: 5
role: Solo project, from design through testing
context: Soft Robotics course, UC San Diego
dates: Oct – Dec 2025
tools: [Vacuum pneumatics, FSR arrays, Arduino, MATLAB]
result: "The jamming pad took 1.6 to 4 times the pull-out force of a strap splint."
thumbnail: /assets/img/particle-jamming/glove.jpg
hero_caption: "The first prototype: a blue nitrile glove of coffee grounds on a vacuum line."
---

Field responders often have to stabilize an injured limb in an awkward position among debris. Straps and rigid splints concentrate pressure on bony or swollen spots, which hurts and risks more injury.

Particle jamming is another route. Granular material in a flexible membrane is soft and conforms to any shape. Pull a vacuum and it locks rigid in that shape.

## The prototype

<div class="split" markdown="1">
<div markdown="1">
I built it from what was in the lab:

- a blue nitrile glove filled with coffee grounds,
- the lab's vacuum line, on or off at about 25 inHg (no regulation),
- a limb surrogate: a foam-wrapped pencil standing in for flesh and bone,
- a three-strap splint as the baseline.
</div>
<figure>
  <img src="{{ '/assets/img/particle-jamming/pencil-glove.jpg' | relative_url }}" alt="Glove with a pencil limb surrogate inside, connected to a vacuum line" loading="lazy">
  <figcaption>The glove pad holding the pencil surrogate.</figcaption>
</figure>
</div>

## Two tests

<div class="split flip tall-media" markdown="1">
<div markdown="1">
### Pull-out

Pull the surrogate out with a crane scale and record the peak force. The strap baseline was tensioned with hanging masses at three preloads, so its resistance could be compared like for like.
</div>
<div class="stack">
<figure>
  <img src="{{ '/assets/img/particle-jamming/pullout.jpg' | relative_url }}" alt="Pulling the limb surrogate out of the pad with a crane scale" loading="lazy">
  <figcaption>Pull-out test with the crane scale.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/particle-jamming/strap-rig.jpg' | relative_url }}" alt="Strap splint clamped to a bench with a hanging mass" loading="lazy">
  <figcaption>The strap rig, tensioned with a hanging mass.</figcaption>
</figure>
</div>
</div>

<div class="split tall-media" markdown="1">
<div markdown="1">
### Load spread

Three force-sensing resistors under the contact region, read through voltage dividers on an Arduino. I calibrated each at 100, 200, and 300 g, with piecewise curves and a simple drift correction.
</div>
<div class="stack">
<figure>
  <img src="{{ '/assets/img/particle-jamming/fsr-setup.jpg' | relative_url }}" alt="FSR array, Arduino, and calibration weights on the bench" loading="lazy">
  <figcaption>FSR calibration with reference weights.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/particle-jamming/fsr-array.jpg' | relative_url }}" alt="Two wooden blocks each carrying FSRs wired through a braided cable" loading="lazy">
  <figcaption>FSR arrays on the contact blocks.</figcaption>
</figure>
</div>
</div>

## Results

<div class="split wide" markdown="1">
<div markdown="1">
The jammed pad beat the strap at every preload. The strap tended to dig into the foam and slip suddenly, while the pad let go smoothly.

Peak pull-out force, strap against jamming pad:

- At a 0.3 kg strap preload: 39 N against **157 N** (4.0×)
- At 0.6 kg: 147 N against **343 N** (2.3×)
- At 1.0 kg: 255 N against **412 N** (1.6×)

With the strap, nearly all the load landed on one FSR at a time. With the jammer, all three read nonzero.
</div>
<figure>
  <img src="{{ '/assets/img/particle-jamming/fsr-average.jpg' | relative_url }}" alt="Bar chart of average FSR readings for straps and the jamming pad" loading="lazy">
  <figcaption>Average FSR readings: the jamming pad loads each sensor less than the straps.</figcaption>
</figure>
</div>

## How far to trust it

{: .callout}
**The pull-out result is solid. The pressure result is suggestive.** The FSRs drifted and disagreed with each other, so a better sensor is the next step. I also learned afterward that fast-acting jamming splints already exist, so the real value was learning the method and building the test setup.
