# Essential Geometry Checks
This repo folder contains the Essential Geometry Checks by Rule that can be used within 1Integrate.  
For instructions on restoring a backup please refer to the following [documentation](https://1spatial.com/documentation/1integrate/v2_3/Topics/Backup_Restore.htm?Highlight=Restore%20Backup%20Rules)

## Check for Duplicate Features
Checks for two features within the same class (aka Feature Class) that has the same geometry 
### Rule Syntax
Check for objects all that there are no objects duplicate features for which :duplicate features.geometry equals :all.geometry and class(:duplicate features) equals class(:all) and :duplicate features does not equal :all
![Alt text](img/DuplicateFeaturesRule.png?raw=true "Title")

## Check for Duplicate Vertices
Checks for Duplicate Verticies.  The Duplicate Vertex checks a geometry (Line or Polygon) that has any consecutive coincident vertices.  This rule uses the Built-In function has_duplicates() that Tests to see if a geometry has any consecutive coincident vertices.  It returns a Boolean value, true if the geometry has any consecutive coincident vertices and false if it does not. 
### Rule Syntax
Check for objects all that has_duplicates(:all.geometry) equals false
![Alt text](img/DuplicateVerticesRule.png?raw=true "Title")

## Check for Kickbacks
Checks whether a geometry has any kickbacks, aka snap-backs, cutbacks, (a type of geometric error where a line segment changes direction twice by approximately 180 degrees to repeat part of the line).  This rule uses the has_kickbacks built-in function.  The has_kickbacks function Checks whether a geometry has any kickbacks (a type of geometric error where a line segment changes direction twice by approximately 180 degrees to repeat part of the line).  The parameters can be configured.  The inputs are 1) geometry to test. 2) (optional) The maximum value for the sine of the angles in the kickback. Note: If omitted, this defaults to the sine of 1 degree. 3) (optional) The maximum width of the kickback. 
This rule uses a 12 degree tolerance.
![Alt text](img/KickbackExample.png?raw=true "Title")

### Rule Syntax
Check for objects all that has_kickbacks(:all.geometry,sin(to_radians(12))) equals false
![Alt text](img/KickbackRule.png?raw=true "Title")

## Check for Multipart Geometries
Checks for Multi-Part Geometries.  A multi-part geometry are geometries that contain more than one part.  For example, the State of Hawaii, if modeled as one feature in a table, would be a multi-part polygon because it contains multiple polygon geometries for each island within that record.  This rule uses the Count-Parts to determine if there is only 1 part for the geometry.  If the feature has no geometry or has more than 1 part, it will be flagged as a non-conformance.
![Alt text](img/MultiPartExample.png?raw=true "Title")

### Rule Syntax
Check for objects all that count_parts(:all.geometry) equals 1
![Alt text](img/CountPartsRule.png?raw=true "Title")