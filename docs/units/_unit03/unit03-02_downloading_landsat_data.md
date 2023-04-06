---
title: Downloading Landsat data
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---


Download landsat data using landsatlinks

## --> make an account and request permission to download e.g. get "machine to machine" API
## create a file with your user credentials
## a simple .txt file first row username, second row password ### think of special character readability
## save the study area shapefile in the misc directory
## we used landsatlinks version 1.0.0 https://github.com/ernstste/landsatlinks

# Create file with download links for Landsat using landsatlinks:

```
landsatlinks search /home/myproject/misc/mystudyarea_shapefile.shp /home/myproject/misc -s OLI -d 20220101,20221231 -m 1,2,3,4,5,6,7,8,9,10,11,12 -c 0,75 --secret /home/myproject/misc/landsatlink.txt -q /home/myproject/misc/landsat_download_links.txt
```
-d = daterange
-m = month
-s = sensor
-c = cloud cover
-q = queue file
--secret = path to the login credentials (Earth Explorer login)

Reference to the landsatlinks github repository:  https://github.com/ernstste/landsatlinks

# In the misc folder access the download URLS written as a .txt file

```
cat /home/myproject/misc/urls_landsat_OLI_20230130T143754.txt| xargs -n 1 -P 50 wget -q -P /home/myproject/level1/level1-datapool/Landsat/landsatlinks --content-disposition
```

ATTENTION: Please note, that the TXT file needs to be exchange for your project related file. This is just an example file mentioned here!

# Unzip all the downloaded .tar files in the respective landsatlinks folder:

```
cd /home/myproject/level1/level1-datapool/Landsat/landsatlinks
for f in *.tar; do 
y=${f%.tar} 
mkdir $y 
sudo tar -xf "$f" -C $y; done
```

