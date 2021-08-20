---
layout: post
title:  "Gear Ratio"
author: pvmilk
categories: [robotics]
tags: [mechanic, electronic]
image: assets/images/2021/08-20_gear-sample.jpg
---

Imagine a bicycle with usually has two gears; one at the padel as a driver gear and another one at the wheel as a driven gear.
Considering a size of the driven gear is fixed, you will chain down to smaller gear when riding the bicycle up the hill.
This will result in the slower speed, but more strength to get you up the hill.

In other words, if the driver gear at the pedal is smaller than the driven gear at the wheel, the torque (or strength) at the driven gear will be increased.
The opposite if also true.

<figure class="align-center">
  <a href="#"><img src="{{ '/assets/images/2021/08-20_gear-relationship.png' | absolute_url }}" alt=""></a>
  <figcaption>Gearing Relationship [<a href="https://youtu.be/5IjG4iSJYQ4?t=271">reference</a>]. Note: The gear ration formula in the link might not be so accurate.</figcaption>
</figure> 

## Gear Ratio

A gear ratio is the ratio of the number of rotations of a driver gear to the number of rotations of a driven gear.
You may also find out the gear ratio without actually turning the gears by counting the number of teeth.


$$ GearRatio = {\text{Rotations of driver gear} \over \text{Rotations of driven gear}} = {\text{# of teeth of driver gear} \over \text{# of teeth of driven gear}}$$


## Reference

* [Developing the Gear Ratio Formula](https://www.sae.org/binaries/content/assets/cm/content/learn/education/motortoycar-samplelessonplan.pdf)
* [Gear Ratios Speed Vs Torque Tutorial](https://youtu.be/5IjG4iSJYQ4)
* [150:1 reduction ratio - DIY Gearbox - 5 Stage Spur gears!](https://youtu.be/8rGYe9lTIHY)
* [How Gear Ratios Work](https://science.howstuffworks.com/transport/engines-equipment/gear-ratio.htm)

