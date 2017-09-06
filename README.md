# hiking_visualization
This project was meant to be a soft introduction to the world of GIS. This project displays real gps data I gathered in Shenandoah national park onto a 3D model of the mountain I hiked. From this project I learned about various file formats, such as [LAS files](http://desktop.arcgis.com/en/arcmap/10.3/manage-data/las-dataset/what-is-a-las-dataset-.htm) used to store Lidar point data, gpx files meant to store gps data, and .vrt files which can store digital elevation data. 

## Resources Used

So far, this project was done entirely using software and data available online for free. [USGS Earth Explorer](https://earthexplorer.usgs.gov/) was especially useful, as it provided both high res lidar data and 1 arcsec digital elevation data. [Google Maps](https://www.google.com/maps) was used to fetch the satellite imagery. Although I did not end up using the lidar data in the final project, learning the intricacies of lidar to digital converstion using both [pointcloudviz](http://www.pointcloudviz.com/) and [lastools](https://rapidlasso.com/lastools/) was instructive. Both [QGIS](http://www.qgis.org/en/site/) and the plugin [qgis2threejs](https://github.com/minorua/Qgis2threejs) were instrumental to this project. Also, shoutout to [gpslogger](https://play.google.com/store/apps/details?id=com.mendhak.gpslogger&hl=en) for being a simple lightweight app that works well. 

## Motivation

I love to hike and have been thinking about producing an app or website for fun which can display a 3D picture of the hikes I go on. As a first step to completing this project, I decided to try to map a single hike to learn the tools of the trade. This gave me a great excuse to go on one of my favorite hikes: Old Rag Mountain in Shenandoah naitonal park. Although I had the misfortune of experiencing labor day crowds, the hike was still worth it and I ended up with a pretty cool visual. 

## Method

In case anyone is curious, I wanted to list a step by step methodology to produce a result like mine. 

### Getting the data
For my project I used [USGS Earth Explorer](https://earthexplorer.usgs.gov/) to find the appropriate digital elevation data set. On their website, simply zoom to the area of interest, and select the data format you are interested in. Lidar data is an option if you want a very precise 3d model, but this proved to be more effort than it was worth in my experience. My dataset had a resolution of 1 arc second and turned out alright. 

