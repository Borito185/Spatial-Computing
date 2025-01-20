# Converting the Mass Into a Building

## Homes

Converting the mass of voxels to an actual building was a long but not too complicated process.
Because the building is generated with the rooms shapes in mind, it was easy to convert these voxels into 3D geometries of the actual rooms.
These rooms were individually modelled in Houdini with the correct accompanying window designs.

The next step was isolating every point in the whole building cloud, that a unit needed to be copied to.
This would mean that our whole building cloud would be converted to a cloud of 450 points, one for every unit.
This cloud is called the “Modified Cloud”. Here you can see a simplified visualization the process of isolating the correct points:

![graph_set_1.png](graph_set_1.png)

## Galleries 

The galleries consist of three components: The concrete slabs that people can walk on, vertical metal bars, horizontal metal bars.
There are three different kind of gallery parts. A normal walkway, a corner, and a border fence. 
The normal walkway is just a straight piece of concrete with a fence, the corner goes around a corner of a building with an L-shaped piece of concrete with a fence and the border fence ends every gallery floor with a fence. 
The galleries also have several bridges spanning between the north and south galleries. 
These bridges were placed randomly, but with certain criteria in mind.

![graph_set_2.png](graph_set_2.png)

## Elevators

The process of designing elevators was actually quite simple.
The elevators in our 3D model are just stretched boxes with every side removed with smaller boxes and a boolean subtract function.
Glass planes were placed in the gaps created by the boolean functions. 
The next step was choosing the correct starting point for the elevator shafts. 
Once the points were chosen with the best access area per elevator, one elevator part was placed at these points. 
Then these parts were copied with the number of stories of the building at that spot, with a Y-distance of 3 meters (our voxel height).
Here you can see a simplified visualization of how these elevators were generated:

![graph_set_3.png](graph_set_3.png)


## The end result

The end result is a building that has two large sides with galleries, elevators and bridges in the middle.
By assigning custom materials to each part, it will be easy to edit these materials in another software, 
with which we will complete the project by rendering some nice images and videos of our building and the surrounding area.

![graph_set_4_b.png](graph_set_4_b.png)