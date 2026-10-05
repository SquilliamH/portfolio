---
title: PHABS Haptic Teleoperation Device
summary: A handheld bimanual teleoperation device with pinch and lateral force feedback, built to improve demonstrations for robot learning.
group: coursework
blurb: "A handheld bimanual haptic device that lets operators feel contact while teaching robots."
card_role: "Built the first lateral force-feedback prototype."
kind: Course project
order: 7
role: Team of four with Emma Fickett, Calvin Joyce, and Lucas Yager. I built the first prototype of the lateral force-feedback mechanism.
context: MAE 219 Haptic Systems, UC San Diego
dates: 2026
tools: [Arduino Mega, PyBullet, Vive trackers, capstan drives]
result: "In a three-person pilot, everyone completed a fragile-object handoff with haptic feedback, and only one of three did without it."
thumbnail: /assets/img/phabs/thumb.jpg
hero_video: /assets/video/phabs-demo.mp4
hero_caption: Using PHABS to manipulate objects in the PyBullet environment.
---

Most portable teleoperation systems track only position. The operator can't feel contact, which makes teleoperation clumsy and the demonstration data poor. PHABS (Portable Haptic Assisted Bimanual System) adds force feedback to close that loop.

It came out of MAE 219, a haptics course where we built and programmed Hapkit devices. PHABS was the group project that followed.

## The device

<div class="split wide" markdown="1">
<div markdown="1">
Two pincher assemblies ride on bearing blocks along parallel rails. Each pincher sits on a 2-axis gimbal so the wrist can align on its own, and one carriage is driven by a motor so the hands feel resistance when squeezing a box between them.

That gives two kinds of feedback: **pinching** between thumb and index finger, and **lateral** squeezing between the hands.
</div>
<figure>
  <img src="{{ '/assets/img/phabs/cad-assembly.jpg' | relative_url }}" alt="CAD of the PHABS assembly with labeled bearing blocks, gimbals, pincher assemblies, and capstan drive" loading="lazy">
  <figcaption>The full assembly, labeled.</figcaption>
</figure>
</div>

<div class="split" markdown="1">
<div markdown="1">
### Pinch

A motor drives a capstan that opposes the index finger while the thumb rests on the housing. A potentiometer is both the pivot and the angle sensor.

Pinch force follows F = (r_s / r_d)(τ / r_h). With a Mabuchi RF-370CA motor, a 75 mm sector, and a 4.75 mm drive wheel, that gives about **0.65 N**.
</div>
<figure>
  <img src="{{ '/assets/img/phabs/pincher.jpg' | relative_url }}" alt="Pinch mechanism worn on a hand, with labeled drive wheel, motor, potentiometer, and finger strap" loading="lazy">
  <figcaption>The pinch mechanism in a right hand.</figcaption>
</figure>
</div>

<div class="split flip" markdown="1">
<div markdown="1">
### Lateral

A motor, a 1:5.625 timing pulley, and a compound pulley-capstan wound with steel cable move one carriage along its rails. I built the first prototype of this axis, using a linear capstan design drawn from a dynamically extensible leg mechanism.
</div>
<figure>
  <img src="{{ '/assets/img/phabs/linear-capstan.jpg' | relative_url }}" alt="Linear capstan drive with labeled cable tensioner, guide bearings, timing pulley, and Maxon motor" loading="lazy">
  <figcaption>The linear capstan drive for the lateral axis.</figcaption>
</figure>
</div>

## Electronics and software

<div class="split" markdown="1">
<div markdown="1">
An Arduino Mega reads the sensors and drives the motors.

- Potentiometers measure jaw distance and an encoder measures lateral position.
- Serial runs at 38,400 baud, the fastest rate that was reliable over the long cables.
- Motors run on a 22 V rail at reduced duty cycle to stay within thermal limits.
</div>
<figure>
  <img src="{{ '/assets/img/phabs/wiring.jpg' | relative_url }}" alt="Wiring diagram of the PHABS electronics" loading="lazy">
  <figcaption>The wiring: Arduino Mega, motors, potentiometers, and a dual-rail supply.</figcaption>
</figure>
</div>

<div class="split flip" markdown="1">
<div markdown="1">
Vive trackers give each hand's 6-DoF pose to a PyBullet scene. Contact force is rendered as a spring-damper, F = kx + bẋ, with a god-object proxy that keeps the virtual fingers from sinking into objects.

Two scenes: a stiffness comparison of two blocks, and a fragile object to hand off and drop in a bin.
</div>
<figure>
  <img src="{{ '/assets/img/phabs/simulation.jpg' | relative_url }}" alt="Two PyBullet scenes: stiffness blocks and a fragile object with a bin" loading="lazy">
  <figcaption>The two simulated tasks.</figcaption>
</figure>
</div>

## Pilot study

<div class="split wide tall-media" markdown="1">
<div markdown="1">
Three participants tried two tasks with haptics on and off.

{: .callout}
**Stiffness:** 3 of 3 picked the stiffer of two virtual blocks (2000 and 1800 N/m) with haptics. **Fragile-object handoff:** 3 of 3 succeeded with haptics and 1 of 3 without. Two of three rated the feedback useful or very useful.

With three people, this is an indication rather than a statistical result. Without feedback, participants said it was hard to tell when contact happened, so they grasped hesitantly and repeatedly.
</div>
<figure>
  <img src="{{ '/assets/img/phabs/operator.jpg' | relative_url }}" alt="A participant using PHABS with Vive trackers in front of the PyBullet simulation" loading="lazy">
  <figcaption>A participant with the device and Vive trackers.</figcaption>
</figure>
</div>

## What broke

The lateral axis bound, so it was left out of the pilot.

- **Bearing blocks:** the preload screws traded one problem for another. Tight, and the printed surfaces dragged on the wooden rails. Loose, and the pincher's moment jammed the carriage.
- **Gimbal:** when both roll axes align, it hits a singularity and can no longer hold its own weight.

I handed the fix to undergraduate researchers in the lab, who have since made design updates.

### What I'd change

- A lighter motor mounted closer to the capstan, and testing each subsystem on its own before integrating.
- A pinch sensor decoupled from the rotating shaft.
- An adjustable handle with per-user calibration, since the housing was sized to our hands.
- Current limiting, after one pincher motor was weakened during testing.

## Since then

After the course, PHABS continued as its own effort in the lab, and I wasn't part of that work. It has since been connected to a robot arm: the pinch aperture sets the gripper command, the robot's measured contact force comes back as pinch feedback, and motion and force are logged together for robot-learning data.

## The paper

{% include pdf-embed.html src="/assets/docs/phabs-paper.pdf" title="PHABS project paper" %}
