---
title: Level 2 processing and Coregistration
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---

For level 2 processing and coregistration first

#  Download parameter file
```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-parameter /opt/data/param/sentinel_level2.prm LEVEL2
```

# Force level 2 and coregistration

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-level2 /opt/data/param/sentinel_level2.prm
```

# Create report for your output

```
sudo docker run -v /home/myproject:/opt/data davidfrantz/force force-level2-report /opt/data/log/
```