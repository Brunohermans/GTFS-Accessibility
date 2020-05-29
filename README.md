# GTFS-Accessibility
This project uses the network shape and locations of a GTFS dataset to calculate distances to common used facilities over roadnetwork and public transport network. The toolset used in this project is still in an experimental phase. Many of to codebase should be optimized for different systems, some code should still be generalized to functions. The project uses several python libraries, but also QGIS and Arcgis Pro (both required).

# Purpose
This package can be used to cluster houses, and thus generate multiple K-means clusters. All of these K-means clusters, show similair levels of Accessibility. For example Cluster one has an average distance of 300 meters to the closest supermarket, and 500 meters to the closest Supermarket. 

# Results
The results can be viewed by accessing this link: [Click here](https://brunohermans.github.io/GTFS-Accessibility/first_results1.html)

A preview:

![Accesibility Levels](https://raw.githubusercontent.com/Brunohermans/GTFS-Accessibility/master/Preview%20Kepler.JPG)

# Dependencies
The toolset uses the functions from the QGIS QNEAT3 plugin to calculate the OD-matrices in long format. One can implement these function into a python project, this was not done for this project untill today. This project used QNEAT3 in QGIS manually. A link to QNEAT3: [Click here](https://root676.github.io/)

Besides QGIS, the project also uses a buildin algorithm from Arcgis Pro. Arcgis Pro contains an algorithm to transform the shapes that a GTFS dataset contains, to an ESRI shapefile. You will need this ESRI shapefile in the analysis/python scripts. 

The python packeges used can be found in the requirements.txt file. Important libraries are geopandas, pandas, scikitlearn and their dependencies. For visualisation kepler.gl is used. 

# Usage
1) Data.

Start be retrieving the required data. In order to run this project, one needs at least a GTFSdataset and dataset from openstreetmap. 
You can retrieve your GTFS dataset from google, use this link: [Click](https://code.google.com/archive/p/googletransitdatafeed/wikis/PublicFeeds.wiki)

You can retrieve your openstreetmap data (for your area of analysis) [here](https://download.geofabrik.de/)

If you want to run my code, you also need a small dataset from CBS. [Clik here](https://www.cbs.nl/nl-nl/dossier/nederland-regionaal/geografische-data/wijk-en-buurtkaart-2018) This dataset is only used to clip the openstreetmap data. 

2) Preprocessing GTFS

In order to start the preprocessing process, you will need the 'GTFS5.ipynb' jupyter notebook. This notebook makes sure that you can extract the data you would like to analyse. In this project, the service network of HTM (a public transport carrier) was analyzed. 
This script makes sure than only the stops of HTM will be analysed, and not all stops and shapes in the GTFS dataset. This notebook was used to create two datasets: shapes.txt and stops.txt for HTM. Shapes.txt was converted to an ESRI shapefile, using the Arcgis PRO GTFS toolset. Stops.txt can be loaded into Qgis directly. 

3) Clipping open street map data

In this step you'll need the data of open streetmap. If you want to use the points of interests dataset as destinations, you should use the multipoint to point script (Multipoint to Point.ipynb). This makes the open streetmap data suitable for the Qneat3 algorithm you'll need in further steps. As origins, we will use the polygon houses dataset of openstreetmap. Now you'll need the 'Filter to the Hague.ipynb' notebook. This notebook will calculate the centroids of all buildings in the selected area (which is why I used the CBS dataset), after that it will cluster all obtained points with the Kmeans algorithm on the longtitude and lattitude attributes. This makes sure we will be able to reduce the size of the dataset. Once all is clustered, we use the houses closest to the centres of the clusters. These are the houses we will use to calculate the distances. 


