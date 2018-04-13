# GeoPython Conference 2018
**Processing Framework: Automating Tasks with Python** \ 
A QGIS workshop for the GeoPython Conference 2018
 
## Getting started
1. Download and install QGIS 3.x [Link to the download page](https://www.qgis.org/en/site/forusers/download.html)
2. Get the sample data that we will be using from this repository
3. Fire up QGIS and we're ready! 
 
Downloading the standalone or OSGeo4W installer will automatically install the correct version of Python as well as Qt and PyQt.

## Setting up your development environment
To try out our hands on examples, the following is required:
* QGIS 3.x (We will be using QGIS 3.0)
* Python 3.x (We wil lbe using Python 3.6)
* Qt
* PyQt
 
**Notes:**
* This repository contains the hands-on problem sets and tasks that we will try out during the workshop. It also contains the suggested solutions, master scripts, and graphic models for the tasks, and problem as a whole.
* For QGIS <2.99 users, these problem sets are still workable, but do take note that as QGIS upgraded from QGIS 2.18 to QGIS 3.0.0, there are a lot of changes, including the Python syntax to be upgrade from Python 2.6 to Python 3.6
* It is still possible to follow this workshop in QGIS 2.18, but do make sure that you are aware of the backwards incompatible changes as many methods and functions were made obsolete or renamed. You can see the [version changelog here] (https://qgis.org/api/api_break.html#qgis_api_break_3_0_QgsGeometryAnalyzer)
   
## Getting more sample data
If you want more sample data or resources to further try out QGIS on your own, look no further:
 
* [The PyQGIS Programmer's Guide](http://locatepress.com/ppg3)
* For raster layers to play around with, we can download one of the [Natural Earth rasters](http://www.naturalearthdata.com/downloads/)
* You can also check out [our Geometa Lab Blog](geometa.tumblr.com) for some posts on QGIS tips and tricks and other tidbits on GIS
 
## Using the QGIS Python Console
* With QGIS running, open the console by going to `Plugins -> Python Console`, clicking on the `Python Console` button from the `Plugin toolbar`, or simply press `Alt + Ctrl + P` on the keyboard
* The toolbar contains the tools **Clear console, Import Class, Run Command, Show Editor, Settings,** and **Help**
* The built-in code editor can be used alongside the console
* The QGIS API offers a large number of [Python classes](http://labs.webgeodatavore.com/partage/diagramme_principal.html) that we can use. See [Searchable documentation of PyQGIS classes](http://geoapis.sourcepole.com/qgispyapi/qgsnetworkaccessmanager)
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

**As you can already tell, doing this over and over again on different files is very tedious, boring and repetitive. Is there a way to automate this? Yes! With the help of scripting and PyQGIS, we can!**\
\
With the click of a button to run a script, we can automate this task in mere seconds.\
This problem will be broken down into smaller problem sets and tasks to break the problem apart. The tasks will be progressive, from getting familiar with the QGIS client to using its Processing toolbox tools, like the Graphical Modeler before moving on to creating your own custom script.


## **Task 1.** Adding Geopackage as Layers into QGIS
- **Dataset used:** Umgebung.gpkg, Autobahn.gpkg
- **Tools used:** QGIS GUI, PyQGIS
- **Objective:** To load .gpkg files into QGIS client

#### Task 1.1. Manually adding the Geopackage files into QGIS
1. Run QGIS 3.0 on your machine
2. On the browser panel, look for GeoPackage, right click it and select **New Connection**
3. Navigate to the folder you saved environment/umgebung.gpkg in and add it
4. On the browser panel, show the child items of environment/umgebung.gpkg and drag the vector layer onto the map canvas

#### Task 1.2. Creating a Dialog Box to ask for User Input on File to Add\
We want to write a script to automate tasks, so let us explore asking for user input for file path
1. On the Menu Toolbar, click `Plugins -> Python Console` or press `Ctrl + Alt + P` on your keyboard to open up the Python Console
2. You can run Python code on the console to perform various tasks, try creating a file dialog box that asks for user input on the file path
3. `envPath = QFileDialog.getOpenFileName(QFileDialog(), "Environment Layer Select", "$SETADEFAULTDIRECTORYHERE$")[0]`
4. The `[0]` is because the method above returns a list, and we only need the first value of it, which is the file path

#### Task 1.3. Adding Vector LAyers into QGIS
Now we can add the user input layer into QGIS
1. `env = iface.addVectorLayer(envPath, '$NAMEOFLAYER', 'ogr')`
2. If the layer name is saved as something else, you can change it with `env.setName("$NAMEOFLAYER$)`
3. Practice and do the same for the Autobahn layer

#### Task 1.4. Adding Autobahn Layer and Setting CRS
1. Add the Autobahn layer using the Python Console
2. Set the Project CRS to 31467, DHDN/Gauss-Kruger Zone 3
3. You can do this manually by clicking on the CRS at the bottom-right of the window, or by clicking `Project -> Project Properties -> CRS` or you can press `Ctrl + Shift + P` to open up Project Properties and then clicking CRS
4. As we are writing a script, we prefer to do it in PyQGIS, enter:
```
my_crs = core.QgsCoordinateReferenceSystem(31467, core.QgsCoordinateReferenceSystem.EpsgCrsId)
QgsMapSettings().setDestinationCrs(my_crs)  
iface.mapCanvas().refresh()
```
5. Once you're done, check that it says 31467 at the bottom of the window on the CRS tab

## Task 2. Adding Buffers to Autobahn Layer
- **Dataset used:** Autobhan.gpkg
- **Tools used:** Processing Graphic Modeler, Python Console
- **Objective:** To create buffer layers for the Autobahn to simulate the actual physical space of it

#### Task 2.1. Introduction and Running the Graphic Modeler
The Graphic Modeler is a good introduction to scripting in PyQGIS because the coding and scripting is displayed for the user as something visual, which is easy on the beginners
1. To start off, you need to open up your Processing Toolbox, on the menu toolbar, click `Processing -> Toolbox` or press `Ctrl + Alt + T` and see that the Processing Toolbox window now appears on the right side of the QGIS window
2. On the Toolbox's menu toolbar, click `Models -> Create New Model`
3. First, we need to visualize and get an idea of what we want to achieve (this helps us to form pseudo code before creating actual code in the future): Run through the Autobahn layer with a Buffer algorithm to create a new Autobahn layer that is 40m wide in diameter

#### Task 2.2. Create a 20m buffer file for the Autobahn layer using the Graphic Modeler\
With the Processing Graphic Modeler open, we can now visualize and build Task 2.1.3
1. Name the Model `Autobahn Buffer` and the Group `vector`
2. On the bottom left, click on Input if it is not already selected, and drag Vector Layer into the blank canvas
3. Name it `Autobahn Buffer` and under Geometry type, select Line as we only want it to exclusively deal with line geometries
4. Drag a Number under Input into the canvas, and name it `Buffer Distance`, you may choose to fill in the other fields
5. On the bottom left, click on Algorithms, and in the searchbar, type 'Buffer', and drag the Algorithm called Buffer into the canvas, making sure it is under *Vector Geometry* and not any other algorithm provider
6. In the Input Layer field, select `Autobahn` from the dropdown menu, in the Distance field, type `@bufferdist`, and in the Buffered field, type *Output Layer Name*
7. On your canvas, you should see that **Buffer Distance** and **Autobahn** are connected as inputs to **Buffer** which gives an output named **Output Layer Name**
8. On the menu toolbar, click on the green arrow Run Model or press F5 to run the model
9. Under Autobahn, select your Autobahn vector layer from the drop down menu, under Buffer Distance, type in **20** and under Output Layer Name, type **Autobahn 20** and run it
10. Let the Model run and after processing, you should see the output vector on your main QGIS window

#### Task 2.3. Recreating the same function using a standalone script
Now that you visualized your steps, you can now try to translate them into actual Pythonic code on the Python Console\
1. On the main QGIS window, at the Processing Toolbox, search for **Buffer**, this is the algorithm that we utilized in the Modeler
2. Double click on it and you can do essentially the same thing as we did in the modeler, except with a few extra fields that we set to default in the Modeler
3. Enter the fields for **Input Layer, Distance and Buffered** and run it
4. At the top of the window, click on Log, you will see a bunch of code, we will be needing this for our script
5. Study the Input parameters and copy its entire line of code
6. On the PyQGIS console, type `param =` and paste the copied code, it should look something like this:\
```
param = { 'INPUT' : %YOURFILEPATH%, 'DISTANCE' : 20, 'SEGMENTS' : 5, 'END_CAP_STYLE' : 0, 'JOIN_STYLE' : 0, 'MITER_LIMIT' : 2, 'DISSOLVE' : False, 'OUTPUT' : 'AUTOBAHN 20' }
```
   In the file path, change the `\` characters into `//` because it does not read Unicode\
7.
```
algoOutput = processing.run("qgis:buffer", param)
createAutobahn = QgsProject.instance().addMapLayer(algoOutput['OUTPUT'])
```

#### Task 2.4. Creating 2 more buffers
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
