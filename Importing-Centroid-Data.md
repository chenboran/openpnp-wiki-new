See the sections below for information about importing boards from your preferred CAD software into OpenPnP.

EAGLE
-----
1. In EAGLE, run mountsmd.ulp, which is included in the EAGLE distribution.
2. In OpenPnP, go to the menu at File -> Import Board -> EAGLE mountsmd.ulp.

KiCAD
-----
1. In OpenPnP, go to the menu at File -> Import Board -> KiCAD .pos.

Altium
------
1. Under Outjob configure Pick and Place Setup to use CSV and Text Formats.  Use Metric units.
1. or While Viewing the PCB, use File->Assembly Outputs->Pick and Place Files and set Pick and Place Setup to use CSV and Text Formats.  Use Metric units.

2. In OpenPnP, use File -> Import Board -> Named CSV.

Others
------

OpenPnP includes a Named CSV importer (File -> Import -> Named CSV) which can import many types of CSV files. Coordinate data must be in Millimeters. Format specifications need to be inside the first 10 lines from file,
six valid field are required in order to successful import centeroid data.

The fields that the Named CSV importer will look for are: (case sensitive)
* Refs: "Designator", "designator", "Part", "part", "Component", "component", "RefDes", "Ref"
* Vals: "Value", "value", "Val", "val", "Comment", "comment"
* Packs: "Footprint", "footprint", "Package", "package", "Pattern", "pattern"
* Xs: "X", "x", "X (mm)", "x (mm)", "Ref X", "ref x", "PosX", "Ref-X(mm)", "Ref-X(mil)"
* Ys: "Y", "y", "Y (mm)", "y (mm)", "Ref Y", "ref y", "PosY", "Ref-Y(mm)", "Ref-Y(mil)"
* Rots: "Rotation", "rotation", "Rot", "rot", "Rotate"
* TBs: "Layer", "layer", "Side", "side", "TB", "tb"
* Heights: "Height", "height", "Height(mil)", "Height(mm)"

Example:

```
"Designator","Footprint","Mid X","Mid Y","Ref X","Ref Y","Pad X","Pad Y","Layer","Rotation","Comment"
"C1","NICHICON_A","58.674mm","7.2263mm","58.674mm","7.239mm","58.674mm","8.7376mm","T","90.00","10uF"
"C3","CAP0603","54.102mm","8.255mm","54.102mm","8.255mm","54.102mm","9.1694mm","T","270.00","1uF"
```