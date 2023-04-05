---
title: Downloading Landsat data
toc: true
header:
  image: '/assets/images/teaser/ndvi.jpg'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---


#####IF using Landsatlinks
--> make an account and request permission to download e.g. get "machine to machine" API
#####
# 2.1.1 create file with download links for Landsat using landsatlinks:
# Please keep in mind, that the Landsat tiles should cover the extent of the Sentinel-2 tiles. The reserach shapefile is not enough, select the tile path and row (i.e. 197024,197025,197026)
# WRS2_descending shape file at top letel of force projects.
# make the .txt file yourself by listing the tilenumbers and save at  i.e. "misc folder"

#2.1.2 create a file with your user credetials
#simple .txt file first row username, second row password ### think of special character readability

# 2.2 create file with download links for Landsat using landsatlinks:
landsatlinks landsat_download_links.txt OLI /media/dogbert/memory99/force_projects/RLP/misc/Landsat_pathrowlist.txt --daterange 2014-01-01,2019-12-31 -s /media/dogbert/memory99/force_projects/RLP/misc/landsatlink.txt

landsatlinks landsat_download_links.txt OLI /media/dogbert/memory99/force_projects/kili/data/force/misc/Landsat_pathrowlist.txt --daterange 2013-01-01,2021-12-31 -s /media/dogbert/memory99/force_projects/kili/data/force/misc/landsatlink.txt


landsatlinks landsat_download_links.txt ETM /media/dogbert/memory99/force_projects/kili/data/force/misc/Landsat_pathrowlist.txt --daterange 2012-01-01,2012-12-31 -s /media/dogbert/memory99/force_projects/kili/data/force/misc/landsatlink.txt

landsatlinks landsat_download_links.txt TM /media/dogbert/memory99/force_projects/kili/data/force/misc/Landsat_pathrowlist.txt --daterange 2000-01-01,2000-12-31 -s /media/dogbert/memory99/force_projects/kili/data/force/misc/landsatlink.txt




#new landsat links working search ## done on 8th nov
landsatlinks search /media/dogbert/memory99/force_projects/kili/data/force/misc/kili_shp_medicine_tmp.shp /media/dogbert/memory99/force_projects/kili/data/force/misc -s TM -d 20110101,20111231 -m 1,2,3,4,5,6,7,8,9,10,11,12 -c 0,50 --secret /media/dogbert/memory99/force_projects/kili/data/force/misc/landsatlink.txt --no-action



# 2.3 download all links in the generated list using wget
# run parallel with xargs
#xargs is helpful to set to 50 images at once -->parallelization
cat /media/dogbert/memory99/force_projects/RLP/urls_landsat_ot_c2_l1_20220720T134838.txt | xargs -n 1 -P 50 wget -q -P /media/dogbert/memory99/force_projects/RLP/level1/level1-datapool/Landsat/landsatlinks --content-disposition

##bale
cat /media/dogbert/memory99/force_projects/bale/data/force/misc/urls_landsat_ot_c2_l1_20220802T152305.txt | xargs -n 1 -P 50 wget -q -P /media/dogbert/memory99/force_projects/bale/data/force/level1/level1-datapool/Landsat/landsatlinks --content-disposition

##kili
cat /media/dogbert/memory99/force_projects/kili/data/force/misc/urls_landsat_ot_c2_l1_20220802T153226.txt| xargs -n 1 -P 50 wget -q -P /media/dogbert/memory99/force_projects/kili/data/force/level1/level1-datapool/Landsat/landsatlinks --content-disposition

cat /media/dogbert/memory99/force_projects/kili/data/force/misc/urls_landsat_ETM_20221020T155534.txt| xargs -n 1 -P 50 wget -q -P /media/dogbert/memory99/force_projects/kili/data/force/level1/level1-datapool/Landsat/landsatlinks --content-disposition

landsatlinks download /media/dogbert/memory99/force_projects/kili/data/force/misc/urls_landsat_ETM_20221020T154353.txt /media/dogbert/memory99/force_projects/kili/data/force/level1/level1-datapool/Landsat/landsatlinks


#### 21 november 
landsatlinks search /media/dogbert/memory99/force_projects/kili/data/force/misc/kili_shp_medicine_tmp.shp /media/dogbert/memory99/force_projects/kili/data/force/misc -s TM -d 20100101,20111231 -m 1,2,3,4,5,6,7,8,9,10,11,12 -c 0,100 --secret /media/dogbert/memory99/force_projects/kili/data/force/misc/landsatlink.txt --no-action
landsatlinks search /media/dogbert/memory99/force_projects/kili/data/force/misc/kili_shp_medicine_tmp.shp /media/dogbert/memory99/force_projects/kili/data/force/misc -s TM -d 20130101,20130331 -m 1,2,3, -c 0,100 --secret /media/dogbert/memory99/force_projects/kili/data/force/misc/landsatlink.txt --no-action

landsatlinks search /media/dogbert/memory99/force_projects/kili/data/force/misc/kili_shp_medicine_tmp.shp /media/dogbert/memory99/force_projects/kili/data/force/misc -s TM -d 20100101,20111231 -m 1,2,3,4,5,6,7,8,9,10,11,12 -c 0,100 --secret /media/dogbert/memory99/force_projects/kili/data/force/misc/landsatlink.txt -q /media/dogbert/memory99/force_projects/kili/data/force/misc/landsat_download_links.txt
cat /media/dogbert/memory99/force_projects/kili/data/force/misc/urls_landsat_TM_20221121T103713.txt| xargs -n 1 -P 50 wget -q -P /media/dogbert/memory99/force_projects/kili/data/force/level1/level1-datapool/Landsat/landsatlinks --content-disposition


