---
title: Mobile Manipulator for Rescue Operations
summary: A mobile base carrying two Franka Panda arms, with an actively shifted center of mass for safe human extraction experiments.
kind: Research
order: 3
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
    value: 41–61 kg, depending on configuration
  - label: Total mass estimate
    value: 117–142 kg
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

<figure>
  <img src="{{ '/assets/img/mobile-manipulator/lab-weights.jpg' | relative_url }}" alt="Mobile base in the lab with a weight plate on the counterweight rack" loading="lazy">
  <figcaption>The base in the lab with weight plates on the counterweight rack.</figcaption>
</figure>

The mass budget shows why the balance matters. The two arms and the 10 kg payload together are about 46 kg. The frame is 30 to 35 kg, and the counterweight is two or three 45 lb plates (40.8 or 61.2 kg), so the whole platform comes to roughly 117 to 142 kg depending on the configuration. The wheels are driven by off-the-shelf electric scooter hub motors.

## Center-of-mass stage

Rather than carrying all that mass fixed, I designed a capstan-driven linear stage that moves the counterweight during operation. A BLDC motor on an ODrive controller runs it in position control. Load-shift tests confirmed repeatable center-of-mass adjustment and smooth motion without backdriving. 

## Soft gripper

The lab's commercial Inspire hand turned out to be too heavy for the Panda arm, and its grip was too strong for physical human-robot interaction. I designed a lightweight fin-ray-effect TPU gripper instead, which conforms to the limb rather than concentrating force at a few points.

<figure>
  <img src="{{ '/assets/img/mobile-manipulator/soft-gripper.jpg' | relative_url }}" alt="Fin-ray-effect TPU gripper mounted on a Panda hand" loading="lazy">
  <figcaption>The fin-ray TPU gripper on the Panda hand.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/mobile-manipulator/gripper-wrist.jpg' | relative_url }}" alt="Gripper fin wrapped gently around a wrist" loading="lazy">
  <figcaption>A gripper finger resting on a wrist: it conforms rather than pinching.</figcaption>
</figure>

## Field testing

We took the platform outdoors onto uneven, loose ground to test it in conditions closer to a real rescue, with the arms positioned over a volunteer lying on a stretcher.

<figure>
  <img src="{{ '/assets/img/mobile-manipulator/field-setup.jpg' | relative_url }}" alt="Team setting up the mobile manipulator in a eucalyptus grove" loading="lazy">
  <figcaption>Setting up outdoors on uneven ground.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/mobile-manipulator/extraction-demo.jpg' | relative_url }}" alt="Panda arms positioned over a person lying on a stretcher" loading="lazy">
  <figcaption>Arms positioned over a person on a stretcher during an extraction trial.</figcaption>
</figure>

This work supports a labmate's research on safe physical human-robot interaction during rescue manipulation.
