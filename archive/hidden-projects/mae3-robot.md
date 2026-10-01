---
title: Dual Four-Bar Lift Robot
summary: A lift mechanism for a game-piece retrieval robot, with the torque analysis checked against a test to about 1%.
published: false
order: 14
role: Lift mechanism design and analysis (teammates built the intake and drivetrain)
context: MAE 3, UC San Diego
dates: Fall 2022
tools: [SolidWorks, laser cutting, gear train design]
specs:
  - label: Lift range
    value: 0–14 in
  - label: Critical mass
    value: 0.5755 kg predicted, 0.57 kg measured
thumbnail: /assets/img/mae3-robot/robot.jpg
hero_video: /assets/video/mae3-robot.mp4
---

Our robot had to grab game pieces of any shape with a rubber-band intake and place them anywhere on a model playing field. Luke Valdez designed the intake and Meshal Alwraised the two-wheel drivetrain. I designed the lift: two parallel four-bar linkages that keep the intake horizontal at any arm angle, driven by a geared motor through a herringbone gear train with a 1:4 step-up in torque.

I chose herringbone gears for their higher load capacity than spur gears and because, unlike a single helical gear, they produce no net thrust. Springs offset some of the torque in the worst cases. The 9.25 in arms were sized to reach the highest point on the field.

## Analysis

The lift had to raise the 0.21 kg intake plus the heaviest game piece, a 0.16 kg iPad, so at least 0.37 kg. A quasi-static torque analysis predicted that the motor would stall at a critical mass of 0.5755 kg. The measured value was 0.57 kg, an error of about 1%, with a factor of safety above one at the required load.

## What I would change

The springs bottomed out at 14 in, an inch short of the full 15 in reach. I would use rubber bands as the counterbalance instead. The larger lesson was to do the torque analysis before committing to a design: we spent time on a drivetrain whose high-speed motors turned out to lack the torque to move the robot.

<figure>
  <img src="{{ '/assets/img/mae3-robot/cad.jpg' | relative_url }}" alt="Isometric CAD of the full robot">
  <figcaption>CAD of the full robot.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/mae3-robot/competition.jpg' | relative_url }}" alt="Team at the class competition">
  <figcaption>Competition day.</figcaption>
</figure>
