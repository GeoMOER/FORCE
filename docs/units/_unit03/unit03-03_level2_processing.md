---
title: Level 2 processing
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---

Downloading DEM 

* provide a DEM for enhanced cloud and cloud shadow detection, atmospheric correction, and to perform the topographic correction
* download DEM of your choice, we recommend ASTER/SRTM 1-arc second (30m) global from USGS earthexplorer or NASA Earthdata
* built vrt with force
```
find misc/dem/ -name '*.tif' > misc/dem/srtm.txt
gdalbuildvrt -input_file_list misc/dem/srtm.txt misc/dem/srtm.vrt
```
# Download parameter file

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-parameter /opt/data/param/landsat_level2.prm LEVEL2
```

* create a queue file (.txt format) in the following structure
/opt/data/level1/level1-datapool/landsat/landsatlinks/name_of_landsat_file QUEUED

* Update the path of the queue file in the parameter file

# Force Level2 processing

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-level2 /opt/data/param/landsat_level2.prm
```


