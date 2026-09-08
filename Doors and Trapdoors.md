# Doors and Trapdoors

Trapdoors rotate around the green Y-Axis in Unity, from the positive X-Axis to the positive Z-axis (red to blue). It is important to setup the `GameObject`'s rotation and positioning first, before the visuals fit into place.

Exporting from Blender can be finicky, but with patience should only take a few attempts. When exporting, ensure you have the experimental Blender option `Apply Transform` enabled. Make sure you do not change the rotation of the `GameObject` once you have initially set it up, just keep changing the export dimension settings in Blender to get the visuals right.

If you want the door or trapdoor to be of a sliding variant, just add a number to the `Slide Distance` variable of the `GP Button Trapdoor` script. The door will then slide into the positive green Y-Axis.
