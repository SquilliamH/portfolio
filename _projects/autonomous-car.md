---
title: Line-Following Car That Plays Music
summary: A ROS 2 car on a Jetson Nano that follows a track and plays a note when it sees a colored marker.
kind: Course project
order: 21
hidden: true
role: Team of four; hardware setup, system debugging, and software integration
context: MAE 148 Introduction to Autonomous Vehicles, UC San Diego
dates: Summer 2024
tools: [ROS 2, Ubuntu 20.04, Docker, NVIDIA Jetson Nano, OAK-D camera, OpenCV, DonkeyCar]
stats:
  - n: "3"
    label: colors mapped to notes (C4, D4, E4)
  - n: "4"
    label: team members
  - n: "Jetson Nano"
    label: onboard compute, with an OAK-D camera
thumbnail: /assets/img/autonomous-car/car-bench.jpg
hero_caption: The car on the bench during development.
links:
  - label: Team repository
    url: https://github.com/dwengxz/SU24-TEAM6-MAE148
---

For our MAE 148 final project, my team combined autonomous driving with music. The car follows a line track using computer vision, and when its camera sees a colored marker it plays the matching note through an onboard speaker. Red, green, and blue map to the first three notes of a C major scale (C4, D4, E4), enough to play the opening of "Au Clair de la Lune."

The team was Kim Garbez, Kenneth Ho, Daniel Weng, and me. We built on UCSD's Robocar ROS 2 framework, running in Docker on Ubuntu 20.04 on a Jetson Nano with an OAK-D camera.

## My part

- **Hardware setup:** mounting the camera, electronics, and speaker.
- **Integration and debugging:** getting the modified ROS 2 and OpenCV packages to run together on the Jetson.
- **Early testing:** DonkeyCar simulation before moving to the physical car.

## How it works

The Robocar lane detection node handles line following, and we modified it to run alongside a color-detection node. The color node looks for the target marker colors in the camera image and triggers the matching note on the speaker.

## What didn't work

- Following the line around curves while also detecting colors was unreliable.
- The car sometimes played the same note more than once for one marker.

Our proposed fixes: run lane detection in its own thread so it doesn't compete with color detection, and control the car's speed to set the song's tempo.

<figure>
  <img src="{{ '/assets/img/autonomous-car/car-closeup.jpg' | relative_url }}" alt="Close-up of the car at night" loading="lazy">
  <figcaption>The car at night.</figcaption>
</figure>

## Demo clips

<figure>
  <video controls muted loop playsinline preload="none" poster="{{ '/assets/img/autonomous-car/video-poster.jpg' | relative_url }}">
    <source src="{{ '/assets/video/car-1.mp4' | relative_url }}" type="video/mp4">
  </video>
  <figcaption>One of our first times playing notes on seeing colors.</figcaption>
</figure>

<figure>
  <video controls muted loop playsinline preload="none">
    <source src="{{ '/assets/video/car-2.mp4' | relative_url }}" type="video/mp4">
  </video>
  <figcaption>An early run on the track.</figcaption>
</figure>

<figure>
  <video controls muted loop playsinline preload="none">
    <source src="{{ '/assets/video/car-3.mp4' | relative_url }}" type="video/mp4">
  </video>
  <figcaption>Playing "Au Clair de la Lune."</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/autonomous-car/team.jpg' | relative_url }}" alt="The team standing outdoors holding the finished car" loading="lazy">
  <figcaption>The team with the car.</figcaption>
</figure>
