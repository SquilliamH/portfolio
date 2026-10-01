---
title: Line-Following Car That Plays Music
summary: A ROS 2 robot car that follows a track and plays a note each time it sees a colored marker.
order: 8
hidden: true
role: Team project; hardware and integration
context: MAE 148 Autonomous Vehicles, UC San Diego
dates: Fall 2024
tools: [ROS 2, Ubuntu 20.04, NVIDIA Jetson Nano, OAK-D camera, DonkeyCar]
specs: []
thumbnail: /assets/img/autonomous-car/car.jpg
---

We combined autonomous driving with music: a Jetson Nano car follows a line track and, when its camera sees a specific color, plays the matching note from the C major scale (C4, D4, E4).

- Line following with a modified Lane_Detection node, built on UCSD's Robocar ROS 2 framework
- Real-time color recognition mapped to notes, running at the same time as line following
- Custom mounts and chassis parts, an OAK-D camera, a speaker, and the power and electrical integration
- DonkeyCar used for early testing and simulation

<figure>
  <video controls muted loop playsinline preload="none" poster="{{ '/assets/img/autonomous-car/video-poster.jpg' | relative_url }}">
    <source src="{{ '/assets/video/car-3.mp4' | relative_url }}" type="video/mp4">
  </video>
  <figcaption>The car running the track.</figcaption>
</figure>
<!-- TODO: confirm which clip is which. Old site had: first notes, early run, and Au Clair de la Lune. Files are car-1, car-2, car-3 in assets/video. -->

<figure>
  <img src="{{ '/assets/img/autonomous-car/hardware.jpg' | relative_url }}" alt="The car chassis on the bench with electronics">
</figure>

