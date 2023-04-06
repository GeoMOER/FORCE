---
title: Downloading Sentinel-2 data
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---


#2.1 download sentinel 2 data for selected dates using study area shapefile
# Note: First Docker command needs to use the Docker credentials

```
sudo docker run -v /home/myproject:/opt/data --user "$yourusername" --env FORCE_CREDENTIALS=/app/credentials -v $HOME:/app/credentials davidfrantz/force force-level1-csd -c 0,75 -d 20170101,20211231 -s S2A,S2B /opt/data/catalog/ /opt/data/level1/level1-datapool/ /opt/data/level1/level1-datapool/queue.txt /opt/data/misc/mystudyarea_shapefile.shp
```