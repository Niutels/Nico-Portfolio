---
template: blog-post
title: Obstacle detection
slug: /kinect
date: 2020-05-09T05:53:16.102Z
description: simple dynamic obstacle detection
featuredImage: /assets/kinect.jpg
---
<!--StartFragment-->

# Simple obstacle detection with kinect

## Continuous 3D detection

The Kinect camera is a distance sensor, it has an angular field of view which means that the coordinates are given through a spherical system. You may keep it that way, but to make it easier to visualize you can also convert it to a Cartesian system. You will need a Kinect camera and a numeric software such as Matlab or Labview.

![Simple obstacle detection with kinect](https://nicolas-robotics-portfolio.netlify.app/static/3aec801beae15239fc2127a23ac2d876/7fe1c/kinect_fov.png)

## Create your map

Let’s say that, if the camera spots an object with the (X,Y,Z) coordinates, it prints it on a map at the said location. Then by showing a wall to the camera, depending on the resolution, the data will look like this :

![Simple obstacle detection with kinect](https://nicolas-robotics-portfolio.netlify.app/static/9108e000fab0f7d5f74095e071bf409d/a7706/3d_mapping_wall.png)

However, if someone had walked in front of the camera, then it would have looked like this :

![Simple obstacle detection with kinect](https://nicolas-robotics-portfolio.netlify.app/static/ad6f9752042a0093489ad2393daad2be/dbafa/walk_infront.png)

## Can we unsee what has been seen ?

The issue here is that we can’t “unsee” what has been seen even if it’s long gone. This is why we need to use the Bresenham algorithm’s principle. Bresenham algorithm's principle : For two points P1 and P2, we search for the cases which are crossed by the \[P1;P2] segment. Here, P1 is the Kinect camera and P2 is a dot on the wall. This method gives us the “free space” (crossed cases) between the camera and the wall, so it helps us clear the areas which are empty.

![Simple obstacle detection with kinect](https://nicolas-robotics-portfolio.netlify.app/static/fea80e8862a6999e6b2920c86f35c46f/bd0ac/Bresenham_principle.png)

## Can it be trusted yet ?

We now have a continuous mapping, however its efficiency is questionable. Indeed, the Kinect camera only “believes” in what it is seeing right now, which is an issue when you consider its malfunctions and low accuracy. Here is an example of what we are supposed to find by implementing this method alone :

![Simple obstacle detection with kinect](https://nicolas-robotics-portfolio.netlify.app/static/7eea46633a026e758b2268c8c3969bee/a14f5/Malfunctions.png)

The spot on the left comes from the Kinect camera which may find incoherent data such as nul distances. To improve our mapping, we are going to use Cauchy distribution. First of all, we may consider a Normal distribution which reflects our uncertainty about the precise location of the obstacle. Here is an example of an obstacle seen at 12 meters from the camera and its associated normal distribution to consider the \[11,5 ; 12,5] range.

![Simple obstacle detection with kinect](https://nicolas-robotics-portfolio.netlify.app/static/c9b2a2d24c3f48eb4e566cbca1522311/254b2/prob_seen.jpg)

Then we may add a cumulative distribution function which will behave as a gauge of confidence : the more an obstacle is seen, the more it is trusted. Thus a wall will be hard to remove from the map but a walking person won’t be. Moreover, malfunctions are mostly erased and the accuracy is improved.

![Simple obstacle detection with kinect](https://nicolas-robotics-portfolio.netlify.app/static/ad8a1b3eb0945af39f30d9724f23acd0/d992c/Confidence_gauge.jpg)

Finally, the outcome is really good, but the map is limited to an area of your room because you can’t move the camera. If you are interested in a more advanced 3D mapping you may want to assemble a motor, allowing the camera to rotate at constant rate and pursue the 3D mapping.



<!--EndFragment-->