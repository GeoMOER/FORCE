---
title: Level 2 processing
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---


###################################
# 3. Landsat ARD
###################################

# 3.1 DEM
# provide a DEM for enhanced cloud and cloud shadow detection, atmospheric correction, and to perform the topographic correction
# download SRTM 1-arc second global from earth explorer
# built vrt with force
find misc/dem/ -name '*.tif' > misc/dem/srtm.txt
gdalbuildvrt -input_file_list misc/dem/srtm.txt misc/dem/srtm.vrt

# 3.2 extract tar files
cd /media/dogbert/memory99/force_projects/RLP/level1/level1-datapool/Landsat/landsatlinks
for f in *.tar; do 
y=${f%.tar} 
mkdir $y 
sudo tar -xf "$f" -C $y; done

cd /media/dogbert/memory99/force_projects/bale/data/force/level1/level1-datapool/Landsat/landsatlinks
for f in *.tar; do 
y=${f%.tar} 
mkdir $y 
sudo tar -xf "$f" -C $y; done

cd /media/dogbert/memory99/force_projects/kili/data/force/level1/level1-datapool/Landsat/landsatlinks
for f in *.tar; do 
y=${f%.tar} 
mkdir $y 
sudo tar -xf "$f" -C $y; done


# 3.3 Download parameter file
sudo docker run -v /media/dogbert/memory99/force_projects/RLP:/opt/data davidfrantz/force force-parameter /opt/data/param/landsat_level2.prm LEVEL2
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-parameter /opt/data/param/landsat_level2.prm LEVEL2


# 3.4 create queue file
#do by hand..
# 3.5 Force Level2
sudo docker run -v /media/dogbert/memory99/force_projects/RLP:/opt/data davidfrantz/force force-level2 /opt/data/param/landsat_level2.prm
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-level2 /opt/data/param/landsat_level2.prm
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-level2 /opt/data/param/landsat_level2_2011.prm



## 30 jan
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-level2 /opt/data/param/landsat_level2_2022.prm

#create report
sudo docker run -v /media/dogbert/memory99/force_projects/kili/data/force:/opt/data davidfrantz/force force-level2-report /opt/data/log/
