---
title: Base image
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---

To create base image we need to first 

# Download parameter file

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-parameter /opt/data/param/ls_base.prm TSA
```

# get Tile extent
Get the coordinates for the TSA prm file

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-tile-extent /opt/data/misc/mystudyarea_shapefile.shp /opt/data/level2/ /opt/data/level2/base/TSA_extent_info.txt
```

# Base image (level 3)
Add additional tile extent in the params file so all folders are read in 2 extra in each direction

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-higher-level /opt/data/param/ls_base.prm 
```

# Base image mosaic

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-mosaic /opt/data/level2/base/
```

