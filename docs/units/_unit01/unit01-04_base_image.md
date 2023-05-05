---
title: Base image
toc: true
header:
  image: '/assets/images/teaser/successful_workflow.jpg'
  caption: '[Rindle](https://images.app.goo.gl/E98WTzaYs5ygL9Gd6){:target="_blank"}'
---

To coregister a Sentinel-2 image with the Landsat images, we need a base image. A base image is the average of all clear-sky Landsat near-infrared reflectance images from multiple years for a month.
So, we get 12 base images, one for each month, stacked as multi-band file (i.e 12 bands). 

<img src="bi_kili.png" width="1104" height="359" align="centre" vspace="10" hspace="20" />

Image: A base image for Mt. Kilimanjaro consisting of stacked images for each month from 2013 to 2021.
Image by : Netra Bhandari
