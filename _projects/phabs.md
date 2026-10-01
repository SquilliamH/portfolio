---
title: PHABS Haptic Teleoperation Device
summary: A handheld bimanual teleoperation device with pinch and lateral force feedback, built to improve the quality of demonstrations for robot learning.
kind: Research / course project
order: 4
role: Team member; first prototype of the lateral force feedback mechanism
context: Haptic Systems course project and ARCLab, UC San Diego
dates: 2-week course project, with later lab work
tools: [Arduino Mega, PyBullet, Vive trackers, capstan drives]
specs:
  - label: Pinch force
    value: ~0.65 N max
  - label: Pilot task success
    value: 3/3 with haptics, 1/3 without
thumbnail:
---

PHABS (Portable Haptic Assisted Bimanual System) is a handheld device for teleoperating two robot arms. Most portable teleoperation systems track position only, so operators can't feel contact forces, which makes for poor teleoperation and low-quality demonstration data. PHABS adds pinching and lateral force feedback to close that loop.

## Mechanical design

The pinch axis uses a motor with a direct-drive capstan. A 2-axis gimbal lets the wrist align passively with the target. The lateral axis uses a motor, a 1:5.625 timing pulley, and a linear capstan on rails. I developed the first prototype of the lateral mechanism.

## Hardware and software

An Arduino Mega handles sensing and motor control, with potentiometers for jaw distance and an encoder for lateral position. Vive trackers give 6-DoF pose to a PyBullet virtual environment, where contact force is rendered as a spring-damper (F = kx + bẋ) using a god-object proxy to keep the virtual fingers from penetrating objects.

## Pilot study

We ran a small pilot with three participants, with haptics on and off, and without the lateral axis. Every participant picked the stiffer of two virtual blocks correctly with haptics. On a fragile-object transfer task, all three succeeded with haptics and one of three without. Two of three rated the feedback useful or very useful. With three participants this is an indication, not a statistical result.

## What happened next

The lateral mechanism was left out of the pilot because it bound. I handed the fix over to undergraduate researchers in the lab, who have since made design updates.
