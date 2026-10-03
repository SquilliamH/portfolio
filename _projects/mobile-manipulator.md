---
title: Mobile Manipulator for Rescue Operations
summary: A mobile base carrying two Franka Panda arms, with an actively shifted center of mass for safe human extraction research.
group: research
blurb: "A mobile base with two Franka arms and a moving counterweight for safe human extraction research."
kind: Research
order: 3
role: Structural frame, center-of-mass stage, and soft gripper design
context: ARCLab, UC San Diego
context_url: https://ucsdarclab.com/
dates: Jun 2024 – Present
tools: [SolidWorks, Ansys FEA, ODrive, BLDC, TPU printing]
result: "A capstan-driven stage moves the counterweight so two Franka arms (36 kg together) and a 10 kg payload stay balanced on a platform weighing roughly 117 to 142 kg."
thumbnail: /assets/img/mobile-manipulator/thumb.jpg
hero_video: /assets/video/mobile-manipulator-loop.mp4
hero_caption: Field testing the mobile manipulator outdoors.
links:
  - label: Lab project page
    url: https://ucsdarclab.com/projects/emergency-medical-extraction-robots-for-search-and-rescue/
---

This platform is a testbed for studying how a robot can safely handle and extract a person in a rescue scenario. I built the base that carries the two arms, an active stage that moves the center of mass as loads shift, and a soft gripper for touching human limbs.

## The frame

<div class="split wide" markdown="1">
<div markdown="1">
The chassis is aluminum extrusion, so the lab can modify it and rebuild test setups quickly. I used FEA to check stiffness and stress under uneven, dynamic loads and removed material that wasn't doing work.

The arms are heavy and reach out over the front, so balance sets the design:

- **Arms and payload:** about 46 kg together.
- **Frame:** 30 to 35 kg.
- **Counterweight:** two or three 45 lb plates (40.8 or 61.2 kg) to keep the center of mass between the wheels.
- **Transport mode:** arms curl in and counterweights come off, in minutes.

The wheels are driven by off-the-shelf electric scooter hub motors.
</div>
<figure>
  <img src="{{ '/assets/img/mobile-manipulator/cad-iso.jpg' | relative_url }}" alt="SolidWorks render of the mobile base with two arms and counterweights" loading="lazy">
  <figcaption>CAD of the base, arms, and counterweights.</figcaption>
</figure>
</div>

<div class="figure-row">
<figure>
  <img src="{{ '/assets/img/mobile-manipulator/frame.jpg' | relative_url }}" alt="Aluminum extrusion chassis with two arm mounting plates" loading="lazy">
  <figcaption>The extrusion chassis and arm mounts.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/mobile-manipulator/lab-weights.jpg' | relative_url }}" alt="Mobile base in the lab with a weight plate on the counterweight rack" loading="lazy">
  <figcaption>Weight plates on the counterweight rack.</figcaption>
</figure>
</div>

## Moving the center of mass

Instead of carrying that mass fixed, I designed a capstan-driven linear stage that moves the counterweight during operation. A BLDC motor on an ODrive controller runs it in position control.

{: .callout}
**Load-shift tests** showed repeatable center-of-mass adjustment with smooth motion and no backdriving.

## A gentler gripper

<div class="split flip" markdown="1">
<div markdown="1">
The lab's commercial hand was too heavy for the Panda arm, and its grip was too strong for physical contact with a person.

I designed a lightweight fin-ray-effect TPU gripper instead. The fins conform to a limb rather than concentrating force at a few points.
</div>
<div class="stack">
<figure>
  <img src="{{ '/assets/img/mobile-manipulator/soft-gripper.jpg' | relative_url }}" alt="Fin-ray-effect TPU gripper mounted on a Panda hand" loading="lazy">
  <figcaption>The gripper on the Panda hand.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/mobile-manipulator/gripper-wrist.jpg' | relative_url }}" alt="Gripper fin wrapped gently around a wrist" loading="lazy">
  <figcaption>A finger resting on a wrist. It conforms rather than pinching.</figcaption>
</figure>
</div>
</div>

## Out in the field

<div class="split" markdown="1">
<div markdown="1">
We took the platform outdoors onto uneven, loose ground, with the arms positioned over a volunteer on a stretcher.

This work supports a labmate's research on safe physical human-robot interaction during rescue manipulation.
</div>
<div class="stack">
<figure>
  <img src="{{ '/assets/img/mobile-manipulator/field-setup.jpg' | relative_url }}" alt="Team setting up the mobile manipulator in a eucalyptus grove" loading="lazy">
  <figcaption>Setting up on uneven ground.</figcaption>
</figure>
<figure>
  <img src="{{ '/assets/img/mobile-manipulator/extraction-demo.jpg' | relative_url }}" alt="Panda arms positioned over a person lying on a stretcher" loading="lazy">
  <figcaption>Arms over a person during an extraction trial.</figcaption>
</figure>
</div>
</div>
