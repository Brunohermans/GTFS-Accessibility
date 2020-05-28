# GTFS-Accessibility
This project uses the network shape and locations of a GTFS dataset to calculate distances to common used facilities over roadnetwork and public transport network. The toolset used in this project is still in an experimental phase. Many of to codebase should be optimized for different systems, some code should still be generalized to functions. 

# Purpose
This package can be used to cluster houses, and thus generate multiple K-means clusters. All of these K-means clusters, show similair levels of Accessibility. For example Cluster one has an average distance of 300 meters to the closest supermarket, and 500 meters to the closest Supermarket. 

# Results
The results can be viewed by accessing this link: [Click here](https://brunohermans.github.io/GTFS-Accessibility/first_results1.html)

A preview:

![Accesibility Levels](https://raw.githubusercontent.com/Brunohermans/GTFS-Accessibility/master/Preview%20Kepler.JPG)

# Dependencies
The toolset uses the functions from the QGIS QNEAT3 plugin to calculate the OD-matrices in long format. One can implement these function into a python project, this was not done for this project untill today. This project used QNEAT3 in QGIS manually. A link to QNEAT3: [Click here](https://root676.github.io/)

The python packeges used can be found in the requirements.txt file. Important libraries are geopandas, pandas, scikitlearn and their dependencies. For visualisation kepler.gl is used. 

#Usage
1) Data.
Start be retrieving the required data. In order to run this project, one needs at least a GTFSdataset and dataset from openstreetmap. 
You can retrieve your GTFS dataset from google, use this link: [Click](https://code.google.com/archive/p/googletransitdatafeed/wikis/PublicFeeds.wiki)
You can retrieve your openstreetmap data (for your area of analysis) [here](https://download.geofabrik.de/)
If you want to run my code, you also need a small dataset from CBS. [Clik here](https://www.cbs.nl/nl-nl/dossier/nederland-regionaal/geografische-data/wijk-en-buurtkaart-2018) This dataset is only used to clip the openstreetmap data. 

2) Preprocessing.
