---
title: Base image
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---

####################################
# 4. Landsat base image
####################################


# 4.1 Download parameter file
sudo docker run -v /media/dogbert/memory99/force_projects/RLP:/opt/data davidfrantz/force force-parameter /opt/data/param/ls_base.prm TSA
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-parameter /opt/data/param/ls_base.prm TSA

# 4.2 get Tile extent
#get the coords for the TSA prm file
sudo docker run -v /media/dogbert/memory99/force_projects/RLP:/opt/data davidfrantz/force force-tile-extent /opt/data/misc/RLP_4326.gpkg /opt/data/level2/europe/ /opt/data/level2/europe/base/TSA_extent_info.txt
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-tile-extent /opt/data/misc/kili_shp_medicine_tmp.shp /opt/data/level2/ /opt/data/level2/base/TSA_extent_info.txt

# 4.3 Force Level3
#add additional tile extent in the params file so all folders are read in 2 extra in each direction
sudo docker run -v /media/dogbert/memory99/force_projects/RLP:/opt/data davidfrantz/force force-higher-level /opt/data/param/ls_base.prm 
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-higher-level /opt/data/param/ls_base.prm 

# 4.4 base image mosaic
sudo docker run -v /media/dogbert/memory99/force_projects/RLP:/opt/data davidfrantz/force force-mosaic /opt/data/europe/base/
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-mosaic /opt/data/level2/base/
