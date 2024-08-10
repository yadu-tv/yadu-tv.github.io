---
title: Identifying plastic using multispectral images
date: 2024-08-09 22:00:00 +05:30
description: This article talks about how me and my team made use of multispectral drone cameras to effectively detect plastic.
---

This article is on a research paper to identify plastic using reflactance values from multispectral images.

#### What is multispectral images? 

Multispectral images are images that contain data across the electromagnetic spectrum. Our human eye is capable of capturing light in the wavelegth of 380 to 700 nanometers. Multispectral cameras can capture images in range of 400 to 1000 nanometers. 

#### What tech did we use?

We made use of a [DJI P4 multispectral](https://www.dji.com/global/p4-multispectral) drone which was equipped with a multispectral camera. This camera is capable of giving us 6 images as output (each of 2MP):

1. Regular RGB image
2. Red image
3. Green image
4. Blue image
5. Red edge image
6. Near-Infrared image

You can visit [here](https://github.com/yadu-tv/yadu-tv.github.io/tree/main/_posts/identify-plastic-using-multispectral-images/assets/) to see all the images.

#### How is this different from regular CNN detection? 

Regular CNN detection is done by learning the pixel values in the image after they are masked out. In this case, we read the value of each pixel and calculate the reflectance of each pixel. Different objects have different reflectance values based on how much light they reflect when a light of particular wavelength strikes it. We found out that *Blue* images best helped in highlighting the plastic from the background. The value is calculated by subtracting the co-efficient of soil from the pixel value.

Using of YOLO is also not possible as YOLO is not recommended for any images that is not RGB. We made our own Encoder-Decoder to generate images and compare with the ground truth.

#### Result

The results and detailed explanation of the research can be found [here](https://github.com/Deceptrax123/Plastic-Detection-using-Reflectance-Images-of-Hyperspectral-Bands/blob/Main/deep_learning_report.pdf). You can also find the complete project with code [here](https://github.com/Deceptrax123/Plastic-Detection-using-Reflectance-Images-of-Hyperspectral-Bands).