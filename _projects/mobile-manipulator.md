---
title: Mobile Manipulator for Rescue Operations
summary: A mobile base carrying two Franka Panda arms, with an actively shifted center of mass for safe human extraction experiments.
order: 2
role: Structural frame, center-of-mass stage, and soft gripper design
context: ARCLab, UC San Diego
dates: Jun 2024 – Present
tools: [SolidWorks, Ansys FEA, ODrive, BLDC, TPU printing]
specs:
  - label: Arms carried
    value: 2× Franka Panda, 36 kg
  - label: Payload
    value: 10 kg
  - label: Counterweight
    value: ~60 kg worst case
thumbnail: /assets/img/mobile-manipulator/thumb.jpg
hero_video: /assets/video/mobile-manipulator-loop.mp4
hero_caption: Field testing the mobile manipulator outdoors.
links:
  - label: Lab project page
    url: https://ucsdarclab.com/projects/emergency-medical-extraction-robots-for-search-and-rescue/
---

This platform is a testbed for studying how a robot can safely handle and extract a person in a rescue scenario. I built the mobile base that carries two 7-DoF Franka Panda arms, along with an active stage that moves the robot's center of mass as loads shift.

<figure>
  <img src="{{ '/assets/img/mobile-manipulator/cad-iso.jpg' | relative_url }}" alt="SolidWorks render of the mobile base with two arms and counterweights">
  <figcaption>CAD of the base, arms, and counterweights.</figcaption>
</figure>

## Frame

The chassis is aluminum extrusion, chosen so the lab could modify it and rebuild test setups quickly. I used FEA to check stiffness and stress under uneven, dynamic loading and removed material where it wasn't doing work. With the arms cantilevered over the front in the operating configuration, the worst case needs about 60 kg of counterweight to keep the center of mass between the wheels. For transport, the arms curl in and counterweights come off, and switching between the two modes takes minutes.

<figure>
  <img src="{{ '/assets/img/mobile-manipulator/frame.jpg' | relative_url }}" alt="Aluminum extrusion chassis with two arm mounting plates">
  <figcaption>The extrusion chassis with the arm mounting plates.</figcaption>
</figure>

## Center-of-mass stage

Rather than carrying all that mass fixed, I designed a capstan-driven linear stage that moves the counterweight during operation. A BLDC motor on an ODrive controller runs it in position control. Load-shift tests confirmed repeatable center-of-mass adjustment and smooth motion without backdriving. 

## Soft gripper

The lab's commercial Inspire hand turned out to be too heavy for the Panda arm, and its grip was too strong for physical human-robot interaction. I designed a lightweight fin-ray-effect TPU gripper instead, which conforms to the limb rather than concentrating force at a few points.

This work supports a labmate's research on safe physical human-robot interaction during rescue manipulation.
