+++
# Date this page was created.
date = 2018-11-10T00:00:00
layout = "project"

# Project title.
title = "Inverse Lego"

authors = ["Weichen (Tony) Zheng", "Yiting (Ellen) Hua", "Weiyi Tang", "Hanyu (Sylvie) Sun"]

# Project summary to display on homepage.
summary = """
LEGO, a robust collection of plastic construction toys manufactured by the LEGO Group, is a great target to study for a computer vision machine learning project. It's natural for the Lego fans like us to ask: if we toss a bunch of Lego pieces on to the ground and took a photo, will the computer be able to recognize each piece captured? Our project seeks to dig deep into this question using object detection model.
 
 """

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Computer Vision"]

# Optional external URL for project (replaces project detail page).
# external_link = "https://www.educoder.net/paths/130"
+++
---
LEGO, a robust collection of plastic construction toys manufactured by the LEGO Group, is a great target to study for a computer vision machine learning project. It's natural for the Lego fans like us to ask: if we toss a bunch of Lego pieces on to the ground and took a photo, will the computer be able to recognize each piece captured? Our project seeks to dig deep into this question using object detection model.

Data is the foundation of any machine learning task. In this project, we generate synthetic data as there is no readily available labeled data, and annotating data within the time frame of this project is impossible. Hence we choose to generate datasets using a 3D modeling tool: Blender. For object detection, we test the use of Faster R-CNN in this task. We also introduce a novel adaptive convolutional layer (AdaConv) and we propose replacing the RoI pooling layer in the original Faster R-CNN model with an AdaConv layer, which we hypothesize would reduce information loss and improve performance of the model.

In the original Faster R-CNN architecture, the RoI pooling is done using an adaptive max pooling layer to convert feature maps of different sized RoIs into the same size. However max pooling can lead to information loss. Hence we propose a new type of layer: adaptive convolutional layer (AdaConv). AdaConv performs the same shape conversion as adaptive max pooling, but uses convolutional operations rather than max pooling operations.

{{< figure src="lego1.PNG" title="" lightbox="true" >}}
