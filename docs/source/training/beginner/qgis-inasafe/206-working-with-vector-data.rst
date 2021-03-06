.. image:: /static/training/beginner/qgis-inasafe/image6.png

********
Module 6
********
Working with Vector Data
========================

**Learning Objectives**

- Understand vector data
- Identify attribute of vector data
- Add vector layers
- Symbolize vector layers

In this chapter, we will learn what is meant by vector data.  We will practice adding it to our QGIS projects, and we will learn how to style the data in different ways.

**1. Vector Data**

Vector data is the most common type of data found in GIS.  A vector is essentially something in the form of a dots, or lines connecting those dots.  In other words, points, lines, and polygons are all vectors.  (curved lines are vectors too, but we won’t worry about that for now)  We are already quite familiar with vector data because in the previous unit, we used JOSM to create it!

Each object in a vector dataset is referred to as a ‘feature.’  When we are using JOSM we often refer to them as objects, but in traditional GIS terminology they are features.  A polygon that represents a building is a feature, as is a line that represents a river.  Each feature has a geographic location, and is attached to other data that describe the feature.

One important thing to note is that QGIS layers can only contain one type of feature.  That is, one layer can’t contain both point features and line features, because they are different types of data.  Hence if you have a file that contains school polygons and another file that contains school points, you would add them as two separate layers.

Almost always, polygon layers will be at the bottom of your layer list, line layers in the middle, and point layers at the top.  You don’t generally want your polygons overlapping your lines and points.

**2. Attribute Data**

It’s important to know that the data you will be working with does not only represent where objects are in space, but also tells you what those objects are.

- Open the project sleman_2_5.qgs.  This is the same project that you worked with in module 3.
- Close the InaSAFE panel if you still have it open.
- You can see in your project the position of Sleman districts, the railway, and some roads, but you can’t see all of the data contained in those layers.
- Select Jalan_Sleman_OSM in the layers list.

.. image:: /static/training/beginner/qgis-inasafe/image68.png
 
- Click the “Open Attribute Table” button:

.. image:: /static/training/beginner/qgis-inasafe/image69.png
 
- You will see a table with more data about the streets layer.  This extra data is called attribute data.  The lines that you can see on your map represent where the streets go - this is the spatial data. You will remember in JOSM that there was the same division.  The points, lines, and shapes you drew tell us where, but the tags, or attributes, tell us what.  These definitions are commonly used in GIS, so it’s essential to remember them!

.. image:: /static/training/beginner/qgis-inasafe/image70.png
 
- Take a look at the attribute table.  Each row in the table is associated with one feature in the streets layer.  Each column contains one of the attributes.  If you select other layers and click on the “Open Attribute Table” button, you’ll see different tables.
- Close the attribute table.

**3. Adding Vector Data**

**Shapefiles**

You’ve already added vector data to a project once, in the form of a shapefile.  As we mentioned previously, a shapefile is a commonly used geographic file format.  It can easily be converted into other formats, and most GIS software can read this type of file.  You may notice when adding a shapefile that there are numerous files in your shapefile directory with the same name.  This is because a shapefile actually relies on a collection of several other files to store the data and keep various settings.  When you add a shapefile to your project, you should always add the one that ends in .shp, but the rest of the files are important too!

- Do you remember how to add a shapefile?  Try adding the layer POI_Sleman_OSM, from the shapefile located in the tutorial directory.  If you don’t remember how to add a new vector layer, refer to the instructions in chapter 2.
- Your project should look like this after the new layer has been added:

.. image:: /static/training/beginner/qgis-inasafe/image71.png
 

**Databases**

Shapefiles (and other types of files) are one way to store geographic data.  You can also load a vector layer into QGIS from a database.  You may already be familiar with Database Management Systems (DBMS) such as Microsoft Access.  GIS applications also make use of databases to store geographic data.  Databases can be hosted and used locally on your computer, or could be shared between users over a network or even the internet..

- Let’s try adding a layer from a database. Click on the following icon.  If you can’t find it, right-click on the toolbar and make sure that the “Manage Layers” toolbar is enabled.

.. image:: /static/training/beginner/qgis-inasafe/image72.png
 
- You will see a dialog box.  Click “New.”

.. image:: /static/training/beginner/qgis-inasafe/image73.png
 
- Navigate to the qgis_data/Sleman folder and find the file guna_lahan.db.  Select the file and click “Open.”
- Now in the original dialog box, you will see that the dropdown button now contains “guna_lahan.db @ ...”, followed by the path of the database file on your computer.
- Click “Connect.”  You will see the following in the box:

.. image:: /static/training/beginner/qgis-inasafe/image74.png
 
- This database actually has three different layers available, all saved in the database.  Click on the first layer to select it, then hold SHIFT and click the last layer to select them all.
- Click “Add.”  This will add all three layers to our project.

*NOTE:  Remember frequently to save your map! Your QGIS project file does not save the data (data is saved in a shapefile or a database), but it does remember the layers that you have added to the project, their order, and any settings that you adjust.*

- The layers you have just added are all polygon layers, so you will want to drag them down below the line and point layers.  If you have a checkbox beneath your layers list that reads “Control rendering order,” go ahead and check it.
- Let’s remove a couple of layers to make it easier to deal with our data.  Right-click on the railway and district layers and click “Remove.”  Then order your layers like this:

.. image:: /static/training/beginner/qgis-inasafe/image75.png 

**4. Symbology**

The symbology of a layer is its visual appearance on the map. One of the basic strengths of GIS is that you have a dynamic visual representation of the data you’re working with.  Therefore, the visual appearance of the map (which depends on the symbology of the individual layers) is very important. The end user of the maps you produce will need to be able to easily see what the map represents. Equally as important, you need to be able to explore the data as you’re working with it, and good symbology helps a lot.

In other words, having proper symbology is not a luxury or just nice to have. In fact, it’s essential for you to use a GIS properly and produce maps and information that people will understand and be able to use.

*4.1  Changing colors*

To change a layer’s symbology, we will open its Layer Properties. Let’s begin by changing the color of the pemukiman layer.
- Right-click on the pemukiman layer in the Layers list.
- Select the menu item Properties in the menu that appears.

*Note: By default you can also access the Properties menu by double-clicking on the name of the layer.*

- In the Properties window select the “Style” tab on the far left.

.. image:: /static/training/beginner/qgis-inasafe/image76.png 
 
- Click the “Change” button.

.. image:: /static/training/beginner/qgis-inasafe/image77.png 

- A standard color dialog will appear.  Choose a grey color and click OK.

.. image:: /static/training/beginner/qgis-inasafe/image78.png
 
- Click OK again in the Layer Properties window, and you will see the color change being applied to the layer.

.. image:: /static/training/beginner/qgis-inasafe/image79.png 

*4.2  Changing Symbol Structure*

This is good stuff so far, but there’s more to a layer’s symbology than just its color. Next we want to change the color of the vegetation, but we also want to eliminate the lines between the different types of vegetation so as to make the map less visually cluttered.

- Open the Layer Properties window for the vegetasi layer.  Under the Style tab, you will see the same kind of dialog as before. This time, however, we will do more than just change the color.
- Click on the Change... button below the color display:

.. image:: /static/training/beginner/qgis-inasafe/image80.png 
 
- The Symbol properties dialog will appear.

.. image:: /static/training/beginner/qgis-inasafe/image81.png 
 
- Change the color inside the polygons in the layer by clicking the button next to the Color label:

.. image:: /static/training/beginner/qgis-inasafe/image82.png 
 
- In the dialog that appears, choose a new color (that seems to suit vegetation).
- Click OK.
- Next, we want to get rid of the lines between all the farms.
- Click on the Border style dropdown. At the moment, it should be showing a short line and the words Solid Line.

.. image:: /static/training/beginner/qgis-inasafe/image83.png 
 
- Change this to No Pen.
- Click OK, and then OK again.  Now when we look at our map, the vegetasi layer will have a new color and no lines between polygons.

.. image:: /static/training/beginner/qgis-inasafe/image84.png 
 
- Try changing the symbology of the pemukiman layer so that it also does not have outlines.
 
*4.3 Scale-based Visibility*

Sometimes you will find that one of your layers is not suitable for a given scale.  For example, if you have a layer which shows the earth’s continents but not with very much detail, the continent lines may not be very accurate when you are zoomed in very far to see streets.

*Note:  Scale is a reference to how your map references what is actually on the ground in terms of size.  Scale is usually given in terms like 1:10000, which means that one centimeter of length on your map is equal to 10000 centimeters in the real world.  When you zoom in or out on a map, the scale changes, as you can see in the status bar at the bottom of QGIS.*

In our case, we may decide to hide our streets layer when we are zoomed out very far (a small scale).  For example, the streets layer is not very useful when we are zoomed out far and it looks like a blob.

.. image:: /static/training/beginner/qgis-inasafe/image85.png 
 
Let’s enable scale-based rendering:

- Open the Layer Properties dialog for the Jalan_Sleman_OSM layer.
- Activate the General tab.

.. image:: /static/training/beginner/qgis-inasafe/image86.png 
 
- Enable scale-based rendering by clicking on the checkbox labeled “Use scale dependent rendering.”  Then change the value in “Maximum” to 100000.

.. image:: /static/training/beginner/qgis-inasafe/image87.png 
 
- Click OK.
- Now look at your map and see what happens when you zoom in and out.  The streets layer should appear when you are at a large scale and disappear at small scales.

*NOTE:  You can use your mouse wheel to zoom in increments. Alternatively, use the zoom tools to draw a box and zoom to it:*

.. image:: /static/training/beginner/qgis-inasafe/image88.png 
 
*4.4 Adding Symbol Layers*

Now that you know how to change simple symbology for layers, the next step is to create more complex symbology. QGIS allows you to do this using symbol layers.

- Go back to the vegetasi layer’s Symbol properties dialog as before.
- In this example, the current symbol has no outline (i.e., it uses the No Pen border style).

.. image:: /static/training/beginner/qgis-inasafe/image89.png 
 
- Click on the + button on the left.

.. image:: /static/training/beginner/qgis-inasafe/image90.png 
 
- Click on it and another symbol layer will be added to the list:

.. image:: /static/training/beginner/qgis-inasafe/image91.png 
 
*Note that it may appear different in color, but we’re going to change that anyway.*

Now this layer has two different symbologies.  In other words, both the green color AND the blue color will be drawn.  However, the blue color will be drawn above the green, and since it is a solid color, it will completely hide the green color.  Let’s change it.

It’s important not to get confused between a map layer and a symbol layer. A map layer is a vector (or raster) that has been loaded into the map. A symbol layer is part of the symbol used to represent a map layer. This course will usually refer to a map layer as just a layer, but a symbol layer will always be called a symbol layer, to prevent confusion.

- Set the border style to No Pen, as before.
- Change the fill style to something other than Solid or No brush. For example:

.. image:: /static/training/beginner/qgis-inasafe/image92.png 
 
- Click OK and then OK and take a look at your layers new symbology.

.. image:: /static/training/beginner/qgis-inasafe/image93.png 
 
- Now try it yourself.  Add an additional symbology layer to the Jalan_Sleman_OSM layer.

    1) Give the thickness of the original layer a value of 2.0
    2) Give the thickness of the new symbology layer a value of 1.0

- This will result in your roads looking something like this:

.. image:: /static/training/beginner/qgis-inasafe/image94.png 
 
- Our streets now appear to have an outline, but they seem disjointed, as if they don’t connect with each other.  To prevent this from happening, you can enable symbol levels, which will control the order in which the different symbol layers are rendered.
- In the Layer Properties dialog, click on Advanced ‣ Symbol levels:

.. image:: /static/training/beginner/qgis-inasafe/image95.png 
 
- The Symbol Levels dialog will appear.  Check the box next to “Enable symbol levels.”

.. image:: /static/training/beginner/qgis-inasafe/image96.png 
 
- Your map will now look like this:

.. image:: /static/training/beginner/qgis-inasafe/image97.png 
 
- When you’re done, you can save the symbol itself in QGIS so that you won’t have to do all this work again if you want to use the symbol again in the future.  Save your current symbol style by clicking the Save Style ... button under the Style tab of the Layer Properties dialog.

.. image:: /static/training/beginner/qgis-inasafe/image98.png 
 
- Give your style file a name and save. You can load a previously saved style at any time by clicking the Load Style ... button. Before you change a style, keep in mind that any unsaved style you are replacing will be lost.
- Try to change the appearance of the streets layer again, so that the roads are dark gray or black, with a thin yellow outline, and a dashed white line running in the middle.

.. image:: /static/training/beginner/qgis-inasafe/image99.png 
 
*4.5 Classified Symbology*

Symbol levels also work for classified layers (i.e., layers having multiple symbols).  We will cover classification in the next chapter, but you can see how it works here with roads.  By classifying various streets according to their type, we can give them different symbologies and they will still appear to flow into each other.

.. image:: /static/training/beginner/qgis-inasafe/image100.png 
 
*4.6 Symbol layer types*

In addition to setting fill colors and using predefined patterns, you can use different symbol layer types entirely. The only type we’ve been using up to now was the Simple Fill type. The more advanced symbol layer types allow you to customize your symbols even further.

Each type of vector (point, line and polygon) has its own set of symbol layer types. First we will look at the types available for points.

**Vector Points**

- Change the symbol properties for the POI_Sleman_OSM layer:

.. image:: /static/training/beginner/qgis-inasafe/image101.png 
 
- You can access the various symbol layer types by clicking the dropdown box in the upper right corner.

.. image:: /static/training/beginner/qgis-inasafe/image102.png 
 
- Investigate the various options available to you, and choose a symbol layer type other than the default Simple Marker.
- If in doubt, use an Ellipse Marker.
- Choose a white outline and dark fill, with a symbol width of 2.00 and symbol height of 4.00.

.. image:: /static/training/beginner/qgis-inasafe/image103.png 
 

**Vector Lines**

- To see the various symbology options for vector lines, open the streets layer properties and click on the dropdown box:

.. image:: /static/training/beginner/qgis-inasafe/image104.png 
 
- Click on “Marker line.”

.. image:: /static/training/beginner/qgis-inasafe/image105.png 
 
- Click on the Change button next to the Marker label.

.. image:: /static/training/beginner/qgis-inasafe/image106.png 
 
- Change the symbol properties to match this dialog:

.. image:: /static/training/beginner/qgis-inasafe/image107.png
 
- Change the interval to 2.00:

.. image:: /static/training/beginner/qgis-inasafe/image108.png 
 
- Your road should now look something like this:

.. image:: /static/training/beginner/qgis-inasafe/image109.png 
 
Once you have applied the style, take a look at its results on the map. As you can see, these symbols change direction along with the road but don’t always bend along with it. This is useful for some purposes, but not for others. If you prefer, you can change the symbol layer in question back to the way it was before.

**Vector Polygons**

- Now let’s change the symbol layer type for the pemukiman layer.  Take a look at the dropdown menu as you’ve done for the point and line layers, and see what the various options can do.

.. image:: /static/training/beginner/qgis-inasafe/image110.png 
 
- Feel free to play around with the various options.  We will use the Point pattern fill with the following settings:

.. image:: /static/training/beginner/qgis-inasafe/image111.png 
 
- Add a new symbol layer with a normal Simple fill.
- Make it gray with no outlines.
- Move it underneath the point pattern symbol layer with the Move down button:

.. image:: /static/training/beginner/qgis-inasafe/image112.png 
 
- The symbol properties should look like this:

.. image:: /static/training/beginner/qgis-inasafe/image113.png 

As a result, you have a textured symbol for the urban layer, with the added benefit that you can change the size, shape and distance of the individual dots that make up the texture.

 

 

 