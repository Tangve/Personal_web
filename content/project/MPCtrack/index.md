+++
# Date this page was created.
date = 2018-11-10T00:00:00
layout = "project"

# Project title.
title = "Obstacle Avoidance: Path Planning and MPC Tracking"

authors = ["Jiacan Xu", "Weiyi Tang", "Suyu Zhou"]

# Project summary to display on homepage.
summary = """
In our project, the cart is running from a predefined source point to a destination point on a map with some fixed x and y boundaries. On the map we generate some randomly distributed obstacles with random sizes and shapes unknown to the cart. When the cart “detects” the obstacle, it will follow the path we planned to avoid collision.
 """

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Control"]

# Optional external URL for project (replaces project detail page).
#external_link = "https://www.educoder.net/paths/130"
+++

---
In the area of unmanned ground vehicles, obstacle avoidance would always be the first problem that we should mainly concern. We have seen many previous works that tried to track predefined reference with fixed obstacles, but these methods would be too fragile to put in real scenario, since most of times we would never know where and when the obstacle will appear at the driving environment. Therefore, in our project, we tried to solve the problem of obstacle avoidance with randomly distributed unknown obstacles by
using path planning methods and receding horizon tracking control. In our project, the cart is running from a predefined source point to a destination point on a map with some fixed x and y boundaries. On the map we generate some randomly distributed obstacles with random sizes and shapes unknown to the cart. When the cart “detects” the obstacle, it will follow the path we planned to avoid collision. Our project includes three main features: vehicle modeling, path planning and controller design. We simplified the model of a unmanned vehicle to have two driving wheels for vehicle modeling, and we used a simple A* method and artificial potential field method for path planning. As for controller design, we used receding horizon (RH) or to say, Model Predictive Control (MPC) for the tracking control of our nonlinear problem. 

Using A* to avoid obstacles:
{{< youtube 0ffQce_p3gE >}}

{{< youtube WcCw1Dj3X-c >}}

Using Potential Field to avoid obstacles:
{{< youtube _N2d3hZdEKs >}}

{{< youtube 9Hw8BJXbXOk >}}
