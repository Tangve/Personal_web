+++
# Date this page was created.
date = 2018-11-10T00:00:00
layout = "project"

# Project title.
title = "Deep Learning System for Bone Age Assessment"


authors = ["Weiyi Tang", "Tiening Li", "Shiao Li", "Songyue Lu"]

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
---
In this project, we want to implement a fully automated deep learning pipeline to segment a region of interest, standardize and preprocess input radiographs, and perform Bone Age Assessments. We first normalize our input images, because they have different sizes and background color. We then try different ways including Image Processing Technology, Single Shot MultiBox Detector (SSD) and Mask R-CNN to remove annotation markers and background border from image to make our data more clearly. We finally feed processed pictures to GoogLeNet to predict the age of bone. As for the result, we can get accuracy of roughly 95% if allowing error within 2 years, while roughly 80% if allowing error within 1 years.

The first approach we have tried to remove markers and background is first segment the hand and fingers from the image, then create another image with just the hand silhouette. Once we have the silhouette image we can erode the image to make it a little smaller by using OpenCV package. But this method failed, because import pixels of hand will lose though we can successfully remove markers.

Then we are thinking about utilize CNNs to help us find the position of hand. There are many cases that can detect human's real hand instead of hand bone, so we want to try to use real human hand as training date set and see how good trained model can be to detect hand bone.  We tried a neural network based on Tensorflow named Single Shot MultiBox Detector (SSD) that was trained on EgoHands dataset by Indiana University. The EgoHands dataset contains 48 Google Glass videos of complex, first-person interactions between two people and provides high quality, pixel-level segmentations of hands, which is frequently used as training and validation sets of hand detection on images or real-time webcam video streams. The SSD model we used implement transfer learning by taking a pre-trained model (especially its weights) named ssd_mobilenet_v1_coco in Tensorflow model zoo to detect hands after we train it again on frozen graphs from EgoHands dataset. According to the model name we know that it is a SSD model trained with COCO dataset, which is another widely used set in object detection. However, there is a fatal defect that both COCO and EgoHand only contain figure of hands in normal shape rather than X-ray photo, which looks quite different. The x-ray photos highlighted hand bones and make other tissue more transparent, so it is difficult for model trained by normal hand images to recognize them as “hands”. This unreliable performance is shown in Fig. 4, only some hands of the x-ray photos can be detected (with red bounding box).

We finally decided to utilize Mask R-CNN to extract hang bone from image. Mask R-CNN is conceptually simple: Faster R-CNN has two outputs for each candidate object, a class label and a bounding-box offset; to this it adds a third branch that outputs the object mask. Mask R-CNN is thus a natural and intuitive idea. But the additional mask output is distinct from the class and box outputs, requiring extraction of much finer spatial layout of an object. And Mask R-CNN usually gives good result with small train data set, which is good for us, because we need to make all the train data set by ourselves.

We select 50 images from the rsna training data set, and use VIA(VGG Image Annotator) only to label the hand position in the image. This is because we only care about the hand’s figure and not interested in other parts. The learning rate is 0.001, number of epochs is 30, training steps for every epoch is 200. The result is shown in Fig. 3. 

When we have more clear images, we need to group our images, in others words, we need to label our data. We first divide the dataset into male and female. Then we utilize two ways to label bone age for each gender. We group data at 12-month intervals (e.g. 11 months old belongs to label 0) and 6-month intervals (e.g. 11 months old belongs to label 1). In the end, we have four groups: A1 (female, 6-month intervals), B1 (male, 6-month intervals), A2 (female, 12-month intervals), B2 (male, 12-month intervals). And we will have results for each group.

Next step is to build a system to predict the boneage of the input radiograph. We choose deep learning since transfer learning can bring us a better result. AlexNet,VGGNet and GoogLeNet are the candidates of our system. We finally use GoogLeNet who has sparse connectivity and won the champion of ILSVRC14. Also, GoogLeNet has higher prediction accuracy than AlexNet and is more efficient than VGGNet.

Firstly, we use gzip and pickle module to pack all the training images in size of 500. Meanwhile, all the images are resized into 227×227×3. The learning rate is set to be 0.001, the batch size is 32 (75\% GPU usage). We use categorical cross-entropy as Loss Function to define the distance between the actual output (probability) and the expected output (probability) (in ‘googlenet.py’ line 153-155). We also set 10\% of each training data to be the validation to prevent overfitting. Then, we use A1, B1, A2, B2 as training data and get four models, which can be used to predict the boneage of the test data. The whole flow chart of our approach can be seen in Fig. 5.

The result table can be seen in TABLE I. Here, we discuss the accuracy which allows error within 2 years and 1 year, which is the same with medical standard. Our result implies that we can use the system to correctly predict the boneage of the input radiograph. The prediction rate of each picture is 0.5s per image, which is higher than manual efficiency. We also categorize the test dataset by different age periods: 4-7 years, 7-13 years, 13-15 years, 15+ years. When the bone age is too big or too small, the accuracy will become lower since we do not have enough training data. mAP and RSME can be computed by the equation below.

\begin{equation*}
mAP=\frac{1}{Q_{r}}\sum_{q\in Q_{r}}AP(q)
\end{equation*}
\begin{equation*}
RSME=\sqrt{\frac{1}{m}\sum_{i=1}^{m}(h(x^{(i)})-y^{(i)})^{2}}
\end{equation*}

From the TABLE II , we can find that the Russian team has a lower RSME and high mAP. This is because that they extract features to train. And their ROI are finger phalanx, ulnar radius and carpal bone, and they conclude that using carpal bone as feature can get a better accurate result. Furthermore, their image size is the largest, which means that their figures have more information to train.

And the bone age between 7-15 years have a better prediction result. This is because we have the most data in this age range. And although the features are obvious when bone age is under 4 years. However, it is difficult the data for the new baby.

