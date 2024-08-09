---
title: Identify plastic using multispectral images
date: 2024-08-09 22:00:00 +05:30
description: This article talks about how me and my team made use of multispectral drone cameras to effectively detect plastic.
---

I am currently working on a research paper on identifying plastic from multispectral images. Github repository to the research can be found [here](https://github.com/Deceptrax123/Plastic-Detection-using-Reflectance-Images-of-Hyperspectral-Bands)

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

Below given are 6 images of the same scene

<img src="assets/rgb.JPG">
<img src="assets/r.TIF">
<img src="assets/g.TIF">
<img src="assets/b.TIF">
<img src="assets/red_edge.TIF">
<img src="assets/nir.TIF">

