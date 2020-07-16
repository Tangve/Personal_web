+++
# Date this page was created.
date = 2018-11-10T00:00:00
layout = "project"

# Project title.
title = "Deep Learning System for Bone Age Assessment"

# Project summary to display on homepage.
summary = """
we are going to implement a fully automated deep learning pipeline to segment a region of interest, standardize and preprocess input radiographs, and perform Bone Age Assessments. We first normalize our input images, because they have different sizes and background color. We then try different ways including Image Processing Technology, Single Shot MultiBox Detector (SSD) and Mask R-CNN to remove annotation markers and background border from image to make our data more clearly. We finally feed processed pictures to GoogLeNet to predict the age of bone. As for the result, we can get accuracy of roughly 95% if allowing error within 2 years, while roughly 80% if allowing error within 1 years.
 """

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Computer Vision"]

# Optional external URL for project (replaces project detail page).
# external_link = "https://www.educoder.net/paths/130"
+++
