---
title: PHABS Haptic Teleoperation Device
summary: A handheld bimanual teleoperation device with pinch and lateral force feedback, built to improve the quality of demonstrations for robot learning.
kind: Research / course project
order: 5
role: Team of four with Emma Fickett, Calvin Joyce, and Lucas Yager; first prototype of the lateral force feedback mechanism
context: Haptic Systems course project and ARCLab, UC San Diego
dates: 2-week course project, with later lab work
tools: [Arduino Mega, PyBullet, Vive trackers, capstan drives]
specs:
  - label: Pinch force
    value: ~0.65 N max
  - label: Jaw opening
    value: 20 mm
  - label: Pilot task success
    value: 3/3 with haptics, 1/3 without
thumbnail: /assets/img/phabs/thumb.jpg
hero_video: /assets/video/phabs-demo.mp4
hero_caption: Using PHABS to manipulate objects in the PyBullet environment.
links:
  - label: Project paper (PDF)
    url: /assets/docs/phabs-paper.pdf
---

I came to PHABS from MAE 219, a haptics course where we built and programmed instructor-provided Hapkit devices and rendered virtual environments on them. PHABS was the group project that followed.

PHABS (Portable Haptic Assisted Bimanual System) is a handheld device for teleoperating two robot arms. Most portable teleoperation systems track position only, so operators can't feel contact forces, which makes for poor teleoperation and low-quality demonstration data. PHABS adds pinching and lateral force feedback to close that loop.

## Mechanical design

The pinch axis uses a motor with a direct-drive capstan. A 2-axis gimbal lets the wrist align passively with the target. The lateral axis uses a motor, a 1:5.625 timing pulley, and a linear capstan on rails. I developed the first prototype of the lateral mechanism, using a linear capstan design drawn from a dynamically extensible leg mechanism.

The pinch force is F = (r_s / r_d)(τ/r_h): with a Mabuchi RF-370CA motor, a 75 mm sector, and a 4.75 mm drive wheel, that comes to about 0.65 N at the fingertip.

## Hardware and software

An Arduino Mega handles sensing and motor control, with potentiometers for jaw distance and an encoder for lateral position. Serial runs at 38,400 baud, the highest rate that was reliable over the long cable runs. Potentiometer signals go through an IIR low-pass filter. Vive trackers give 6-DoF pose to a PyBullet virtual environment, where contact force is rendered as a spring-damper (F = kx + bẋ) using a god-object proxy to keep the virtual fingers from penetrating objects.


## Pilot study

We ran a small pilot with three participants, with haptics on and off, and without the lateral axis. Every participant picked the stiffer of two virtual blocks (2000 and 1800 N/m) correctly with haptics. On a fragile-object transfer task, all three succeeded with haptics and one of three without. Two of three rated the feedback useful or very useful. With three participants this is an indication, not a statistical result.

## What happened next

The lateral mechanism was left out of the pilot because it bound. The bearing blocks had adjustable preload screws, but that set up a tradeoff: tightening them removed slop and let the 3D-printed surfaces drag on the wooden rails, while loosening them let the moment from the pincher assemblies bind the carriage. The gimbal added a second problem, since when both roll axes align it reaches a singularity and can no longer hold up its own weight. I handed the fix over to undergraduate researchers in the lab, who have since made design updates.

## Lessons

The paper's main takeaways for a next version were to move to a lighter motor closer to the capstan, test each subsystem on its own before integrating, and decouple the pinch sensor from the rotation shaft. The housing was sized to our team's hands, so a future version needs an adjustable handle and per-user calibration. Motor current also needs limiting after one pincher motor was weakened during testing, and shielded cables would allow a faster serial link.

The lab has since connected PHABS to a robot arm, mapping the pinch aperture to the gripper command and sending the robot's measured contact force back as pinch feedback, with motion and force logged together for robot-learning data.
