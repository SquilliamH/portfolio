---
title: PHABS Haptic Teleoperation Device
summary: A handheld bimanual teleoperation device with pinch and lateral force feedback, built to improve demonstrations for robot learning.
kind: Research and course project
order: 4
role: Team of four with Emma Fickett, Calvin Joyce, and Lucas Yager. I built the first prototype of the lateral force-feedback mechanism.
context: Haptic Systems course project and ARCLab, UC San Diego
dates: 2-week course project, with later lab work
tools: [Arduino Mega, PyBullet, Vive trackers, capstan drives]
stats:
  - n: "3 of 3"
    label: pilot participants completed the task with haptics (1 of 3 without)
  - n: "0.65 N"
    label: maximum pinch force
  - n: "20 mm"
    label: jaw opening
  - n: "2"
    label: force-feedback axes, pinch and lateral
thumbnail: /assets/img/phabs/thumb.jpg
hero_video: /assets/video/phabs-demo.mp4
hero_caption: Using PHABS to manipulate objects in the PyBullet environment.
---

Most portable teleoperation systems track only position. The operator can't feel contact, which makes teleoperation clumsy and the demonstration data poor. PHABS (Portable Haptic Assisted Bimanual System) adds force feedback to close that loop.

It came out of MAE 219, a haptics course where we built and programmed Hapkit devices. PHABS was the group project that followed.

## How it works

<div class="figure-row">
<div class="mode-card">
  <h3>Pinch</h3>
  <p>A motor drives a capstan that opposes the thumb and index finger. A 2-axis gimbal lets the wrist align on its own.</p>
</div>
<div class="mode-card">
  <h3>Lateral</h3>
  <p>A motor, a 1:5.625 timing pulley, and a linear capstan on rails resist squeezing the hands together. I built the first prototype of this axis.</p>
</div>
</div>

Pinch force follows F = (r_s / r_d)(τ / r_h). With a Mabuchi RF-370CA motor, a 75 mm sector, and a 4.75 mm drive wheel, that gives about 0.65 N.

An Arduino Mega reads the sensors and drives the motors. Vive trackers give each hand's 6-DoF pose to a PyBullet scene, where contact force is rendered as a spring-damper, F = kx + bẋ, with a god-object proxy that keeps the virtual fingers from sinking into objects.

### Details worth knowing

- Serial runs at 38,400 baud, the fastest rate that was reliable over the long cables.
- Potentiometer signals pass through an IIR low-pass filter.
- Motors run on a 22 V rail at reduced duty cycle to stay within thermal limits.

## Pilot study

Three participants tried two tasks with haptics on and off.

{: .callout}
**Stiffness:** 3 of 3 picked the stiffer of two virtual blocks (2000 and 1800 N/m) with haptics. **Fragile-object handoff:** 3 of 3 succeeded with haptics and 1 of 3 without. Two of three rated the feedback useful or very useful.

With three people, this is an indication rather than a statistical result. Without feedback, participants said it was hard to tell when contact happened, so they grasped hesitantly and repeatedly.

## What went wrong

The lateral axis bound, so it was left out of the pilot.

- **Bearing blocks:** the preload screws traded one problem for another. Tight, and the printed surfaces dragged on the wooden rails. Loose, and the pincher's moment jammed the carriage.
- **Gimbal:** when both roll axes align, it hits a singularity and can no longer hold its own weight.

I handed the fix to undergraduate researchers in the lab, who have since made design updates.

### What I'd change

- A lighter motor mounted closer to the capstan.
- Testing each subsystem on its own before integrating.
- A pinch sensor decoupled from the rotating shaft.
- An adjustable handle with per-user calibration, since the housing was sized to our hands.
- Current limiting, after one pincher motor was weakened during testing.

## Since then

The lab has connected PHABS to a robot arm. The pinch aperture sets the gripper command, the robot's measured contact force comes back as pinch feedback, and motion and force are logged together for robot-learning data.

## The paper

{% include pdf-embed.html src="/assets/docs/phabs-paper.pdf" title="PHABS project paper" %}
