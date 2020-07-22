+++
# Date this page was created.
date = 2018-11-10T00:00:00
layout = "project"

# Project title.
title = "Classic Computer Vision Methods"


authors = ["Weiyi Tang", "Zhiyuan Li"]

# Project summary to display on homepage.
summary = """
Implement Canny edge dectetion, Image Gradient Blending, Image Morphing, Seam Carving, Image Stitching and Optical Flow. (Note: Didn't use any package for all the implementations)
 """

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Computer Vision"]

# Optional external URL for project (replaces project detail page).
#external_link = "https://github.com/Tangve/Classic_Computer_Vision_Methods"
+++
---
Results are below (More details are coming later!)<br>

Image morphing<br>

A morph is a simultaneous warp of the image shape and a cross-dissolve of the image colors. The cross-dissolve is the easier part; controlling and doing the warp is the harder part. The warp is controlled by defining a correspondence between the two pictures. The correspondence should map eyes to eyes, mouth to mouth, chin to chin, ears to ears, etc., to get the smoothest transformations possible.

{{< youtube 0bzqZsvuNrk >}}

Canny Edge Detection<br>

Applying Gaussian smoothing and compute local edge gradient magnitude as well as orientation, then seeking local maximum edge pixel in corresponding orientation. Finally, continue searching in the edge orientation of detected edge points.

{{< figure src="canny.PNG" title="Canny Edge Detection" lightbox="true" >}}

Image Gradient Blending<br>

The goal is to seamlessly blend an object from a source image into a target image. The simplest method would be to just copy and paste the pixels from one image directly into the other. However, this will create apparent seams, even if the backgrounds are alike. We need to get rid of these seams without visually tampering the source image.

Human vision is found to be more sensitive to gradients than absolute image intensities. We formulate this problem as finding values for the output pixels that maximally preserve the gradient of the source region without altering any of the background pixels.

{{< figure src="blend1.PNG" title="Blending Result 1" lightbox="true" >}}
{{< figure src="blend2.PNG" title="Blending Result 2" lightbox="true" >}}

Seam Carving<br>

For this project, I am going to implement image resizing utilizing scene carving. The structure of this part of the project is based heavily on the methods outlined by Avidan & Shamir in their [paper](http://www.faculty.idc.ac.il/arik/SCWeb/imret/index.html).

{{< youtube sWOWxolRWEw >}}
{{< figure src="seam1.PNG" title="Seam Carving Result 1" lightbox="true" >}}
{{< youtube Wq5J-BqKTk4 >}}
{{< figure src="seam2.PNG" title="Seam Carving Result 2" lightbox="true" >}}

Image Stitching<br>

First, detecting features in an image frame and find the best matching features in other frames. These features should be reasonably invariant to translation and rotation. Once we have the homography, we will need to warp the images.

{{< figure src="hebin1.PNG" title="Original Images" lightbox="true" >}}
{{< figure src="hebinres1.PNG" title="Result" lightbox="true" >}}
{{< figure src="hebin2.PNG" title="Original Images" lightbox="true" >}}
{{< figure src="hebinres2.PNG" title="Result" lightbox="true" >}}
{{< figure src="hebin3.PNG" title="Original Images" lightbox="true" >}}
{{< figure src="hebinres3.PNG" title="Result" lightbox="true" >}}

Optical Flow<br>

In this part of the project, I am going to track an object in a video. There are two essential components to this: feature detection and feature tracking. I will identify features within the bounding box for each object using Harris corners or Shi-Tomasi features. Then I will apply the Kanade-Lucas-Tomasi tracking procedure to track the features I found. This involves computing the optical flow between successive video frames and moving the selected features as well as the bounding box from the first frame along the flow field.

{{< youtube NggXtsYj49s >}}

