---
title: Particle-Jamming Limb Stabilization
summary: A vacuum-tunable particle-jamming interface for stabilizing a limb quickly in the field, tested against strap splints.
kind: Course project
order: 4
role: Solo project, design through testing
context: Course project, UC San Diego
dates: Oct – Dec 2025
tools: [Vacuum pneumatics, FSR arrays, Arduino, MATLAB]
specs:
  - label: Duration
    value: 2-week solo project
  - label: Vacuum
    value: ~25 inHg
  - label: Pull-out vs. strap
    value: 1.6–4× higher
thumbnail: /assets/img/particle-jamming/glove.jpg
hero_caption: "The first prototype, a glove of coffee grounds on the vacuum line."
---

Field responders often have to stabilize a limb in an awkward posture among debris. Rigid splints and straps concentrate pressure on bony or swollen areas, which causes pain and risks secondary injury. Particle jamming offers another route: granular material in a flexible membrane is soft and conforms to any shape, then becomes rigid and holds that shape when a vacuum is pulled.

## Prototype

I built the first device from parts lying around the lab: a blue nitrile glove filled with coffee grounds, lab pneumatic lines for the vacuum, and a limb surrogate made from a pencil wrapped in foam to stand in for bone and flesh. There was no vacuum regulation, only on and off, at about 25 inHg (roughly 85 kPa below atmospheric). The baseline was a three-strap splint.

## Measurement

I ran two tests. For pull-out resistance, I pulled the limb surrogate out with a crane scale and recorded the peak force. For the strap, I added hanging masses to tension it at three preloads. For pressure distribution, I put three FSRs under the contact region, read through voltage-divider circuits on an Arduino. I calibrated each with 100, 200, and 300 g weights and used piecewise calibration curves with a simple drift correction.

<figure>
  <img src="{{ '/assets/img/particle-jamming/fsr-setup.jpg' | relative_url }}" alt="FSR array, Arduino, and calibration weights on the bench" loading="lazy">
  <figcaption>The FSR calibration setup with reference weights and the Arduino.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/particle-jamming/fsr-array.jpg' | relative_url }}" alt="Two wooden blocks each carrying FSRs wired through a braided cable" loading="lazy">
  <figcaption>FSR arrays on the contact blocks.</figcaption>
</figure>

## Results

The jammed pad had a higher peak pull-out force than the strap at every preload, and the strap tended to dig into the foam and slip abruptly while the pad released smoothly:

| Strap preload | Strap peak | Jamming peak | Ratio |
|---|---|---|---|
| 0.3 kg | 39 N | 157 N | 4.0× |
| 0.6 kg | 147 N | 343 N | 2.3× |
| 1.0 kg | 255 N | 412 N | 1.6× |

In the strap tests, nearly all the load showed up on a single FSR; with the jammer, all three sensors read nonzero. The jammer's average load was lower, but the FSRs gave inconsistent readings, so I treat that result as suggestive rather than conclusive. A different sensor would be the next step. I also learned afterward that fast-acting jamming splints already exist, so this project was valuable mainly as a way to learn the method and build the test setup.
