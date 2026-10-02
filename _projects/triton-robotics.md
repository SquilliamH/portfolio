---
title: Triton Robotics Competition Robot
summary: Two generations of chassis for a projectile-launching competition robot, then a year leading the 80-member team.
kind: Team leadership
order: 8
role: Lead mechanical engineer (2021–23), president (2023–24)
context: Triton Robotics, UC San Diego
dates: Sep 2021 – Jun 2024
tools: [SolidWorks, CNC machining, manual machining]
specs:
  - label: Team size
    value: 80 members
  - label: Engineers mentored
    value: "6"
  - label: Robot size (2022–23)
    value: 684 × 541 × 472 mm
  - label: Launcher
    value: 42 mm projectile, 16 m/s
  - label: Rotation speed
    value: "+40%"
  - label: Targeting accuracy
    value: "+50%"
thumbnail:
---

Triton Robotics builds robots for the RoboMaster competition. The Hero robot is remote-controlled, fires 42 mm projectiles at 16 m/s, and is the team's main offensive unit. I worked on two generations of its chassis.

## 2021–22 chassis

The goals were a smaller, lighter, cheaper, more accessible chassis. The old design was hard to maintain and transport because it had no access ports and used too much material. The redesign used 30% less aluminum square tubing, with polycarbonate plates carrying the electronics and a hinged top plate for access to the internals. The finished robot could climb a 15° ramp, rotated its turret independently of the chassis, and had a modular suspension, with a 45° elevation and 30° depression range for aiming.

Two problems from the first version shaped the final design. The suspension lunged under acceleration, so we moved to a standardized, proven layout with shock absorbers parallel to the mecanum wheels. And the sprocket-and-chain yaw drive on the turret deformed, which restricted rotation, so I replaced it with a belt system that spreads the stress more evenly.

## 2022–23 chassis

The second redesign aimed to optimize rotation, keep the turret free to rotate independently, and be modular to build. It used omni-wheels in an X-drive to make better use of motor power, a circular chassis, and a slip ring so the turret could rotate without limit. It still climbed a 15° ramp, with no suspension. The omni-wheel X-drive allows planar translation and efficient rotation about the center, a shielded bumper ring on bearings lets the robot deflect off obstacles without stopping its spin, and the drivetrain, bumper, and frame are modular so the robot is quick to assemble and repair. A revolver-inspired serializer indexes the 42 mm projectiles and feeds them up through a 50 mm-bore slip ring to the turret, which is back-fed with a simplified ball path to reduce jamming. The robot measured about 684 × 541 × 472 mm. I mentored six mechanical engineers through CAD, drawings, and machine shop work.

## President, 2023–24

As president I led the 80-member team across mechanical, electrical, and software sub-teams and overhauled the training program and documentation so new members could get up to speed faster. The training program brought in about 40 new members over the year, which addressed a succession problem that had left my term short of team leads. The team competed at the RoboMaster North American regionals in Seattle (2023) and Boulder (2024). At the competition during my term the robots took damage in shipping, but we still won two 1v1 matches and held our own in the 3v3 matches.
<!-- TODO: add photos or CAD renders, and reliability numbers -->
