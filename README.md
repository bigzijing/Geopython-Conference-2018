# GeoPython Conference 2018
Processing Framework: Automating Tasks with Python\
A QGIS workshop for the GeoPython Conference 2018
 
## Getting started
 1. Download and install QGIS 3.x ([Link to the download page]https://www.qgis.org/en/site/forusers/download.html )
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
   * This repository contains the hands-on problem sets and tasks that we will try out during the workshop. It also contains the suggested solutions and master script for the analytical task as a whole.
   * For QGIS <2.99 users, these problem sets are still workable, but do take note that as QGIS upgraded from QGIS 2.18 to QGIS 3.0.0, there are a lot of changes, including the Python syntax to be upgrade from Python 2.6 to Python 3.6
   * It is still possible to follow this workshop in QGIS 2.18, but do make sure that you are aware of the backwards incompatible changes as many methods and functions were made obsolete or renamed. You can see the version changelog [here (https://qgis.org/api/api_break.html#qgis_api_break_3_0_QgsGeometryAnalyzer) ]
   
 ## Getting more sample data
 If you want more sample data or resources to further try out QGIS on your own, look no further:
 
 * *The PyQGIS Programmer's Guide, here: [http://locatepress.com/ppg3]
 * For raster layers to play around with, we can download one of the [Natural Earth rasters](http://www.naturalearthdata.com/downloads/)
 * You can also check out [blog website] for some posts on interesting plugins that you can try to play with
 
 ## Using the QGIS Python Console
  * With QGIS running, open the console by going to 'Plugins -> Python Console', clicking on the 'Python Console' button from the 'Plugin toolbar', or simply press Alt + Ctrl + P on the keyboard
  * The toolbar contains the tools *Clear console, Import Class, Run Command, Show Editor, Settings,* and *Help*
  * The built-in code editor can be used alongside the console
  * The QGIS API offers a large number of [Python classes]((http://labs.webgeodatavore.com/partage/diagramme_principal.html)) that we can use. See [Searchable documentation of PyQGIS classes](http://geoapis.sourcepole.com/qgispyapi/qgsnetworkaccessmanager)
  * For the convenience of the user, the following statements are executed when the consoles is started
  ```python
  from qgis.core import *
  import qgis.utils
  ```
   
## Introduction to Processing Framework
*
*
*
