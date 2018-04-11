# GeoPython Conference 2018
**Processing Framework: Automating Tasks with Python**
\
A QGIS workshop for the GeoPython Conference 2018
 
## Getting started
1. Download and install QGIS 3.x [Download link](https://www.qgis.org/en/site/forusers/download.html)
2. Get the sample data that we will be using from this repository
3. Fire up QGIS and we're ready! 
 
Downloading the standalone or OSGeo4W installer will automatically install the correct version of Python as well as Qt and PyQt

## Setting up your development environment
To try out our hands on examples, the following is required:
* QGIS 3.x (We will be using QGIS 3.0)
* Python 3.x (We wil lbe using Python 3.6)
* Qt
* PyQt
 
**Notes:**
* This repository contains the hands-on problem sets and tasks that we will try out during the workshop. It also contains the suggested solutions and master script for the analytical task as a whole
* For QGIS <2.99 users, these problem sets are still workable, but do take note that as QGIS upgraded from QGIS 2.18 to QGIS 3.0.0, there are a lot of changes, including the Python syntax to be upgrade from Python 2.6 to Python 3.6
* It is still possible to follow this workshop in QGIS 2.18, but do make sure that you are aware of the backwards incompatible changes as many methods and functions were made obsolete or renamed [Version changelog](https://qgis.org/api/api_break.html#qgis_api_break_3_0_QgsGeometryAnalyzer)
   
## Getting more sample data
If you want more sample data or resources to further try out QGIS on your own, look no further:
 
* The PyQGIS Programmer's Guide [here](http://locatepress.com/ppg3)
* For raster layers to play around with, we can download one of the [Natural Earth rasters](http://www.naturalearthdata.com/downloads/)
* You can also check out [blog website](http://geometalab.tumblr.com) for some posts on interesting plugins that you can try to play with
 
## Using the QGIS Python Console
* With QGIS running, open the console by going to `Plugins -> Python Console`, clicking on the `Python Console` button from the 'Plugin toolbar', or simply press `Alt + Ctrl + P` on the keyboard
* The toolbar contains the tools *Clear console, Import Class, Run Command, Show Editor, Settings,* and *Help*
* The built-in code editor can be used alongside the console
* The QGIS API offers a large number of [Python classes](http://labs.webgeodatavore.com/partage/diagramme_principal.html) that we can use, see [Searchable documentation of PyQGIS classes](http://geoapis.sourcepole.com/qgispyapi/qgsnetworkaccessmanager)
* For the convenience of the user, the following statements are executed when the consoles is started
```python
from qgis.core import *
import qgis.utils
```
   
## Introduction to Processing Framework
*
*
*

## About PyQGIS
*
*
*

## **Task: Perform Geospatial Analysis on bla bla protected species**
* 
*
*
* More details can be found here [link to the tutorial course]

** Doing this over and over again on different files is very tedious, boring and repetitive. Is there a way to automate this? Yes! With the help of scripting and PyQGIS, we can!**
With the click of button to run a script, we can automate this task in mere seconds.\
This problem will be broken down into smaller problem sets and tasks to break the problem apart. The tasks will be progressive, from getting familiar with the QGIS client to using its Processing toolbox tools, like the Graphical Modeler before moving on to creating your own custom script.


## **Task 1.** Adding Geopackage as Layers into QGIS
- **Dataset used:** Umgebung.gpkg, Autobahn.gpkg
- **Tools used:** QGIS GUI, PyQGIS
- **Objective:** To load .gpkg files into QGIS client

#### Task 1.1. Manually adding the Geopackage files into QGIS
1. 
2.
3.

#### Task 1.2. Creating a Dialog Box to ask for User Input on File to Add
1.
2.
3.

## Task 2. Adding Buffers to Simulate Physical Autobahn
- **Dataset used:** Autobhan.gpkg
- **Tools used:** Processing Graphic Modeler, Python Console
- **Objective:** To create buffer layers for the Autobahn to simulate the actual physical space of it

#### Task 2.1. Create a 20m buffer file for the Autobahn layer using the Graphic Modeler
The Graphic Modeler is a good introduction to scripting in PyQGIS because the coding and scripting is displayed for the user as something visual, which is easy on the beginners
1.
2.
3.

#### Task 2.2. Recreating the same function using a standalone script
Now that you visualized your steps, you can now try to translate them into actual Pythonic code on the Python Console
1.
2.
3.

#### Task 2.3. Creating 2 more buffers
Often times, the actual physical space that a highway construction takes up, is smaller than the actual impact that it causes to the environment.\
Create 2 more buffers to depict 2 more impact zones that the construction of the Autobahn would cause\
Bonus: You may also create a script that interactively asks for user input before running the Buffer algorithm 
1.
2.
3.

## Task 3. Performing Union on the Buffer Areas
- **Dataset used:** Autobahn.gpkg, and the 3 buffer results from previous task
- **Tools used:** Python Console, Script Editor
- **Objective:** Now that we have 3 separate buffer layers to showcase the impact areas, we should perform an Union on them to create an overall area of impact from constructing the highway

#### Task 3.1. Union-ing the Inner Impact Zone
Now that we have tried to run Processing algorithms on the Python Console, let us try it on a standalone script
1.
2.
3.

#### Task 3.2. Union-ing the Overall Impact Area
Next, we perform the Union algorithm on the result of the previous task, the Inner Impact Zone, with the Outer Impact Zone to aggregate the total Area of Impact
1.
2.
3.

## Task 4. Performing Intersections
- **Dataset used:** Umgebung.gpkg, union result from previous task
- **Tools used:** Script Editor
- **Objective:** Now that we have an overall impact area, we run an Intersection algorithm on it and the Environment layer to highlight the habitats that would be affected

#### Task 4.1. Performing Intersection on Environment and Impact Area
You have already created your own script! Now that we are more familiar with scripting, we shall now cover the rest of the tasks using scripts \
Now, as mentioned, run an Intersection algorithm on the Environment layer as well as the Impact Zone layer
1. 
2.
3.
4. 

## Task 5. Selecting Features from Queries
- **Dataset used:** Umgebung.gpkg
- **Tools used:** Query Features and Script Editor
- **Objective:** Now, we have to sieve out habitats in the Environment layer that are protected species from the other habitats

#### Task 5.1. Running a Query on the Environment Shapefile Attributes
Query the attributes of the Environment Shapefile to determine the features that are protected by law
1.
2.
3.
4.

#### Task 5.2. Translating Query Feature into Pythonic Code
Now we do what we did in 5.1 using Pythonic code in our script
1.
2.
3.
4.
[Help: Selecting features using script]

#### Task 5.3. Adding Vector Layer of Selected Features
Now we have to create new layers with just the selected features to show which features are actually affected by the Autobahn construction
1.
2.
3.
4.

#### Task 5.4. Translating Vector Layer Adding into Pythonic Code
1.
2.
3.
4.

## Task 6. Finding Actual Protected Species Impacted by Autobahn Construction
- **Dataset used:** 
- **Tools used:** Script Editor, Processing Algorithm
- **Objective**: From the bla bla bla

#### Task 6.1. Intersect
1.
2.
3.
4.

#### Task 6.2. 

## Task 7. Stylizing and Cleaning Up
- **Dataset used:**
- **Tools used:** Script Editor
- **Objective**: Stylize the map layers to make results more obvious and clean up the project to make it more readable

#### Task 7.1. Deleting Intermediate Layers
Some of the intermediate layers can be deleted because they serve no actual analytical purpose
1.
2.
3.

#### Task 7.2. Hiding Layers
Some of the result layers can be useful, but too many layers visible on the project makes it hard to read\
Uncheck their visibility using a script so that they are still available, but not visible on the Map Canvas
1.
2.
3.

#### Task 7.3. Stylizing Map Layers
There are many styles that can be utilized on the layers so that you can get information at a glance\
Let us explore what we can achieve
1.
2.
3.
4.

#### Task 7.4. Adding a Basemap
To make your result more aesthetically pleasant, we can add a raster basemap
1.
2.
3.
4.

## Bonus: Interactive and Independent Script
We have created many different functions to help us achieve our tasks \
Can we do better to join them all into just 1 script entity?\
Can we do even better and create a script that is interactive and uses the user inputs to automate our tasks?\
Can we publish these scripts or create something that others can use?

#### Bonus 1: Creating a Main Script
1.
2.
3.
4.

#### Bonus 2: Creating an Interactive Script
1.
2.
3.
4.

#### Bonus 3: Plugins
1.
2.
3.
4.


## Notes for QGIS 3.0.0

## References, Resources and Additional Help

## Contact
