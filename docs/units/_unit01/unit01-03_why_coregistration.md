---
title: Why coregistration?
toc: true
header:
  image: '/assets/images/teaser/successful_workflow.jpg'
  caption: '[Rindle](https://images.app.goo.gl/E98WTzaYs5ygL9Gd6){:target="_blank"}'
---


# Lets talk Sentinel-2 

The European Space Agency launched Sentinel-2 A (2015) and Setinel-2B (2017) as a Multi-Spectral Instrument. This pair of polar-orbiting satellite moves around earth every 5 days and monitors land surface conditions.
With a fine resolution of 10m, Sentinel-2 satellites are popular for its application in land monitoring, emergency management, security, climate change, and marine environmental monitoring.     

# But there's a small problem

The images obtained from Sentinel-2 before the usage of Ground Reference Image has a geolocation uncertainity of 12m. 
This uncertainity is slightly more than a pixel (10m). When performing a time series analysis, such a shift of 12m can lead to unreliable results.

<img src="https://force-eo.readthedocs.io/en/latest/_images/tutorial-coreg-animation.gif" width="40" height="40" />

Image: Animation of Sentinel-2 images on Crete. Source - [FORCE](https://force-eo.readthedocs.io/en/latest/howto/coreg.html?highlight=coregistration#coregistration){:target="_blank"}

# FORCE provides a solution to this problem - Coregistration

FORCE uses Landsat images as a baseline to fix the geolocation of Sentinel-2 images. The aggregated Landsat time series (i.e. a "base image", check out the next section in this unit), are very robust to average out the error.
FORCE uses a modfied Landsat Sentinel Registration (LSReg algorithm) to automatically coregister large amounts of Sentinel-2 imageries using the "near infrared multiannual monthly averaged" Landsat base image. 
This algorithm has been explained in detail by (Ruffin et al 2021)[10.1109/LGRS.2020.2982245]{:target="_blank"}.


 