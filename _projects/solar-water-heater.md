---
title: Solar Water Heater for an Orphanage in Baja
summary: A student team reviving a low-cost solar water heating system with a microcontroller control box for an orphanage in Tijuana.
kind: Service project
order: 9
role: Team member (secretary in the final team, then continuing on the build)
context: Baja Solar, UCSD Global TIES and La Misión Children's Fund
dates: Winter – Spring 2023
tools: [Solar thermal, ESP32, thermocouples, pump control, CAD]
specs:
  - label: Children served
    value: about 50
  - label: Typical household utility cost
    value: $90 / month in Tijuana
  - label: Typical household income
    value: $1,300 / month in Tijuana
thumbnail: /assets/img/solar-water-heater/roof.jpg
---

Baja Solar is a student-run group at UC San Diego that builds low-cost solar water heaters for an orphanage in Tijuana, in partnership with the NGO La Misión Children's Fund. Hot water is a necessity there for cooking and sanitizing dishes, and the utility bill for an orphanage with about 50 children is high. At the time the kids were limited to quick showers before the hot water ran out.

## The system

The heater circulates water through a rooftop solar collector into a hot water tank. A control box built around an ESP32 reads thermocouples on the tank, and when the water is too cool it turns on a pump to send water through the collector. Earlier teams had developed the design, a filtration module, and the controls. After Covid the project was left incomplete, and the orphanage couldn't fix the system without a manual.

<figure>
  <img src="{{ '/assets/img/solar-water-heater/array.jpg' | relative_url }}" alt="Solar panels on a tiled rooftop" loading="lazy">
</figure>

## My work

I joined in winter 2023 as the team's secretary. That quarter we restored and reordered missing electrical parts, replaced a missing Raspberry Pi, and tested each part of the prototype individually. The tests found a non-functional pump on the test cart and a battery too small for the real system's pump, so the next step was to calculate the right parts. The quarter was also hard because we started late and had no advisor on hand.

In spring 2023 the team (me, Madison Ragone, and Darell Chua) set three goals: bring the existing system online, design a control box with a circulating pump, thermocouple connections, and a flow meter, and write an instruction and maintenance manual for the orphanage staff.

<figure>
  <img src="{{ '/assets/img/solar-water-heater/controller.jpg' | relative_url }}" alt="Wired controller enclosure" loading="lazy">
  <figcaption>Controller enclosure wiring.</figcaption>
</figure>

<figure>
  <img src="{{ '/assets/img/solar-water-heater/team.jpg' | relative_url }}" alt="The team on the rooftop next to the panel" loading="lazy">
</figure>

Working on this project is part of what led me toward engineering with direct human impact.
