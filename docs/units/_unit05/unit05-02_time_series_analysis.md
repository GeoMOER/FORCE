---
title: Time series analysis - indices
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Environmental Informatics Marburg](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---

To get the Spectral indices, first 

# Create a parameter file
```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-parameter /opt/data/param/sentinel_level3.prm TSA
```

# For getting FORCE Sentinel Level3 spectral indices

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-higher-level /opt/data/param/sentinel_level3.prm
```

* for monthly aggregates, use FBM = TRUE
* for yearly aggregates, use FBY = TRUE (here date range is only one year)
* for multi-annual aggregates, use FBY = TRUE AND!
* Under "PROCESSING TIMEFRAME", adjust to more than one year. For example, adjust DATE_RANGE to 2017-01-01 - 2021-12-31

# Mosaicing the level 3 output

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-mosaic /opt/data/level3/
```