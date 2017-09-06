# hiking_visualization
This project was meant to be a soft introduction to the world of GIS. This project displays real gps data I gathered in Shenandoah national park onto a 3D model of the mountain I hiked. From this project I learned about various file formats, such as [LAS files](http://desktop.arcgis.com/en/arcmap/10.3/manage-data/las-dataset/what-is-a-las-dataset-.htm) used to store Lidar point data, gpx files meant to store gps data, and .vrt files which can store digital elevation data. 

## Resources Used

So far, this project was done entirely using software and data available online for free. [USGS Earth Explorer](https://earthexplorer.usgs.gov/) was especially useful, as it provided both high res lidar data and 1 arcsec digital elevation data. [Google Maps](https://www.google.com/maps) was used to fetch the satellite imagery. Although I did not end up using the lidar data in the final project, learning the intricacies of lidar to digital converstion using both [pointcloudviz](http://www.pointcloudviz.com/) and [lastools](https://rapidlasso.com/lastools/) was instructive. Both [QGIS](http://www.qgis.org/en/site/) and the plugin [qgis2threejs](https://github.com/minorua/Qgis2threejs) were instrumental to this project. Also, shoutout to [gpslogger](https://play.google.com/store/apps/details?id=com.mendhak.gpslogger&hl=en) for being a simple lightweight app that works well. 

## Motivation

I love to hike and have been thinking about producing an app or website for fun which can display a 3D picture of the hikes I go on. As a first step to completing this project, I decided to try to map a single hike to learn the tools of the trade. This gave me a great excuse to go on one of my favorite hikes: Old Rag Mountain in Shenandoah naitonal park. Although I had the misfortune of experiencing labor day crowds, the hike was still worth it and I ended up with a pretty cool visual. 

## Method

In case anyone is curious, I wanted to list a step by step methodology to produce a result like mine. 

### Getting the data
**DEM**
For my project I used [USGS Earth Explorer](https://earthexplorer.usgs.gov/) to find the appropriate digital elevation data set. On their website, simply zoom to the area of interest, and select the data format you are interested in. Lidar data is an option if you want a very precise 3d model, but this proved to be more effort than it was worth in my experience. My dataset had a resolution of 1 arc second and turned out alright. 
**GPX**
Using a gpslogger logger app of choice, you can create a gpx file containing your trail path. Then, I followed [these steps](http://docs.qgis.org/2.0/en/docs/user_manual/working_with_gps/plugins_gps.html) to convert the gpx file to a .shp file. 
**Satellite Images**
Simply install the openlayers plugin to qgis, and then go to web->OpenLayers Plugin to select the database of your fancy. 

### Adding layers to QGIS
First, you're gonna want to set the project CRS to whatever coordinate system your DEM is in. To load your dem, simply navigate to it in the built in file explorer on the left and double click. Once it is added as a layer, right click it in the layers panel and select "properties". Then, change reder type to single band pseudocolor, scroll down, and click "classify". Apply your changes to the see newly colored DEM. 

Then, double click the .shp file you made earlier to add it as a layer. You're gonna want to have this layer on top to overlay the trail path. If it doesn't show, try to right click it in the layer window and zoom to it. If the coordinates are way off, this means you need to reproject it into another coordinate system. 

Finally, go to web->web->OpenLayers->google maps->google satellite to load the satellite imagery. This will  automatically load the imagery corresponding to the location of your DEM file. 

### Displaying the 3D picture

Be sure to navigate to the qgis plugins tab to install qgis2threejs if you haven't already. In order for things to look better I also wanted to manually select the area that gets rendered by qgis2threejs. To do this, I first installed the Rectangles and Ovals Digitizing plugin. Then, I used the "Rectangle by extent" button to draw a polygon layer in qgis. This polygon will be used by qgis2threejs to select the area to render. From top to bottom, my layer order was .shp file, google maps, dem, polygon. 

Move the polygon to the background and click the qgis2threejs button. In the DEM tab, up the resulotion to whatever your preference is and select "clip dem with polygon layer". In the world tab, you can change the verticle exageration. THe default sometimes works well, but I had to make it very small before things went smoothly. Click run, and your fully interractible 3d model should appear!

## What to do now

Having 1 trail mapped is nice, but it is far from my goal. Hopefully as more trails come in I can add more 3d models and come up with a way to combine them all on one website. 

## Acknowledgements 

I'd like to thank everyone on reddit.com/r/gis for all the helpful suggestions for this project. The advice given there really set me off in the right direction. 
