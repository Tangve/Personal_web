+++
# Date this page was created.
date = 2018-11-10T00:00:00
layout = "project"

# Project title.
title = "Machine Perception"

authors = ["Weiyi Tang"]

# Project summary to display on homepage.
summary = """
Implement machine perception technology include: logo projection, scale invariant, SIFT matching and 3D reconstruction.
 """

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Computer Vision"]

# Optional external URL for project (replaces project detail page).
#external_link = "https://www.educoder.net/paths/130"
+++
---
**Logo Projection**<br>

In this programming assignment, we will use the concepts of projective geometry and homographies to allow us to project an image onto a scene in a natural way that respects perspective. To demonstrate this, we will project our logo onto the goal during a football match. I have images from a video sequence of a football match, as well as the corners of the goal in each image and an image of the Penn Engineering logo. Our task is, for each image in the video sequence, compute the homography between the Penn logo and the goal, and then warp the goal points onto the ones in the Penn logo to generate a projection of the logo onto the video frame.

{{< figure src="logo.PNG" title="" lightbox="true" >}}<br>


**Scale Invariant**<br>

I am going to implement a scale-invariant blob detector. First, applying a series of DoG filters to the initial image to build a 3D-matrix of responses, then finding local maxima in position and scale.

{{< figure src="Sinv1.PNG" title="" lightbox="true" >}}<br>


**Pose Optimization**<br>

In the first step, I trained a heatmap-based neural network that given an image of an object, it estimates the location of the keypoints in the image. For the second step, I used the coordinates of detected keypoints to estimate the 6DoF pose of the object.

{{< figure src="3Dre.PNG" title="" lightbox="true" >}}
