+++
# Date this page was created.
date = 2018-11-10T00:00:00
layout = "project"

# Project title.
title = "ODrive Hopper Robot"

authors = ["Weiyi Tang", "Sonia Roberts"]

# Project summary to display on homepage.
summary = """
Using mechanical design inspired by the [Ghost Minitaur](https://kodlab.seas.upenn.edu/robots/ghost-minitaur/) and the open-source motor controller hardware from the [Stanford Doggo](https://github.com/Nate711/StanfordDoggoProject), we built an open-source two-degree-of-freedom hopping robot. The robot hops using a Raibert-inspired reactive controller on the leg length and velocity.
 """

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Control"]

# Optional external URL for project (replaces project detail page).
# external_link = "https://github.com/Tangve/ODrive_Hopper_Robot"
+++
---
{{< youtube 7lFuCAbviWo >}}

The [Ghost Minitaur](https://kodlab.seas.upenn.edu/robots/ghost-minitaur/) is a medium-sized legged robot platform which has been used to perform a variety of robotics research, much of which makes use of the actuator transparency conferred by the direct-drive (no gearbox) motors and high-bandwidth motor controllers. This robot's morphology and "compliant" direct-drive architecture both warrant further study, but Minitaur is not open-source and is no longer being sold by Ghost. Researchers therefore need alternative open-source platforms that they can build and modify for their own projects.

The [Stanford Doggo](https://github.com/Nate711/StanfordDoggoProject) is a fully open-source platform, down to the open-source Teensy microcontroller and ODrive motor controllers. The result is a highly agile and accessible robot which can be programmed using a variety of methods, including open-loop trajectory control and impedance control. The extensive [documentation](https://docs.odriverobotics.com/) provided enables other researchers to adapt the control system to different morphologies.

The final piece of the puzzle was the reactive jumping controller. The leg emulates a soft spring (low proportional and derivative gain) during the first half of stance, while it compresses, and then switches to emulating a stiff spring (high gains) when the leg length velocity changes sign, and the leg starts to extend. This simple controller dates back to Marc Raibert's seminal work on legged locomotion and is still used to underpin robust legged robot locomotion to this day.
