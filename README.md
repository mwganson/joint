# Macro Joint (Work in progress)
Macro Joint is a macro to create joints in FreeCAD.  Usage: select a face and run the macro, select from the list the type of joint to make on that face.  Options are Mortise, Tenon, Box Joint, and Dovetail Joint.  A feature python object is created with user configurable editable properties.  Join works in Part Design and other workbenches.<br/>
<br/>
<img src="macro_joint_scr1.png" alt="screenshot"><br/>

## Toolbar Icon
<a href="Macro_Joint_Icon.svg">Download</a> the toolbar icon: <img src="Macro_Joint_Icon.svg" alt="toolbar icon"><br/>
<br/>

## Installation
Not yet available in the addon manager.  Install by placing the Joint.FCMacro into your macro folder.  On first run it will offer to create a new file called joint.py.  This file is needed for the Joint feature python objects to be parametric and functional upon reloading documents containing these objects.

## Usage
Select the face upon which you wish to create the joint, and run the macro.  A default joint with editable properties will appear in the tree.  Adjust the properties as desired, then create a mate for this joint on another face of another object.  The Mortise is the mate for the Tenon.  For the Box Joints and Dovetail Joints you will create another of the same type for the mate, setting the Use Odd property to True for the mate, usually.  For Dovetail Joints it might also be necessary to adjust the Angle X property to 90 degrees for the mate so that a good mate can be created.  Mortise, Tenon, and Box Joints are all fairly easy to make.  The Dovetail Joints will require more fiddling, but with some patience a good mate can always be created.

## Properties
Some properties are hidden for some joints where they are not used.  For example, the finger angle properties are not used with Mortise and Tenon joints, so those properties are hidden for those joint types.

## Dimensions (group)
Here I tried to put the properties related to the dimensions of the joints in one place.  All of these are float values interpreted as millimeters.  If you experiment with these values you can easily see which dimension each controls.

### Depth (float)
Depth is how deep into the face the joint will be or if it's a Tenon how far above the face it will extend.

### Finger Angle (float)
### Finger Angle2 (float)
Only used with Dovetail Joint types.  Finger Angle is the angle from the face to the tip of the joint.  Finger Angle2 is the angle from front to back if viewed from the front with the face on the xy_plane.  These 2 angles are not identical in terms of the spacing between one finger and the next, so you generally need to rotate the mate joint 90 degrees with the Angle X property to create a good matching mate unless the 2 parts are butting together straight on rather than at a 90 degree angle.

### Finger Width (float)
Used with Dovetail Joints and Box Joints.  It's the width of each finger.  For Box Joints this is very straight forward.  For Dovetail Joints it's more complicated.  With Dovetail Joints its the distance from the middle of the left side of the finger to the middle of the right side of the finger, when viewed from the front with the face on the xy_plane.

### Length (float)
This is the distance from the front to the back when viewed from the front with the face on the xy_plane.

### Width (float)
Not to be confused with Finger Width (for Dovetail and Box Joints), this is the total width of the joint.  For Mortise and Tenons this is the width of those objects.  For Dovetail and Box Joints this is the total width of all the fingers combined (and the spaces in between).  The number of fingers depends on this property along with the Finger Width property for the finger joint types, but there will always only be one object for Mortise and Tenons.  Of course, if you want more you can always position the Mortise/Tenon to one side and use a linear pattern to create more.  See the Position property for more on this.

### Offset (float)
Mating joints that are exactly the same size will be very difficult to assemble because the fit will be too tight.  The Offset property is used to increase/decrease the size of the objects that make up the joint.  You will need to experiment to determine the correct offset to use for your given situation, material used, glue used, etc.  On this note, care must be taken when making Dovetail Joints lest you end up with an impossible to assemble joint where the angles are such that the narrow end faces outward in all directions.



## Changelog
### 0.2021.11.30 == rework dovetail code
### 0.2021.11.26.rev2 == uncomment __version__ property
### 0.2021.11.26 == initial upload
