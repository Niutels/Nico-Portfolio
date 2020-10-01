---
template: blog-post
title: Painting Robot
slug: /paintingrobot
date: 2020-09-30 23:03
description: Painting with a robot
featuredImage: /assets/paint_24.jpg
---
<!--StartFragment-->

# Summary of the design and implementation

## Motivation for the work of Summer 2020

We want to provide a solution for mimicking human operators manipulating spraying cans and cleaning materials, we have the robotic arm Scorpio designed by Apptronik and a gripper from Robotiq at our disposal. The initial intent here is to provide a working demonstration in a delay of 3 months, paving the way to more advanced human-like trajectory tracking in the future.

![](<>)<https://www.youtube.com/watch?v=u6k4HucUqpA&ab_channel=NicolasBrissonneau>

## Design context

![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/b7cb6185bd1635749b589c5efcb89e7d/5bd38/paint_2.jpg)

Above are three potential configurations to use the spraying can, we notice that the main means of assembly for the interface we plan to add are two planar surfaces at the base of the gripper, with an additional cylindrical surface to support the structure radially. While it is possible to design an independently actuated assembly to activate the spraying (arduino/raspberry pi + actuator + power), we want to minimize the complexity of the assembled system and final software. The philosophy behind the proposed design is to limit the number of interfacing components and to maximize the use of the assets we already have with the existing parts. In short we want a very practical solution with little design, production and assembly complexity. We have started envisioning the use of gun-shaped devices to interface the gripper with the can as the trigger is a good fit for the gripper’s grasping capabilities. We have thus ordered two models, a can-gun1 2012 and a 3M Accuspray Spray Gun Kit HPG shown below.

![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/d04fc8b3f6eb3141fc200ed575badffc/1cea9/paint_3.jpg)

## Assembly idea

![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/154356680dcd7fc81e1e97e4cfc74fb4/53be6/paint_4.jpg)

Using the gripper’s base surfaces, we would attach two supporting parts (blue) which place the device’s handle within reach of the gripper’s “fingers” and a locking part (green) would fix and rigidify the assembly. However, the scale of such spraying devices require better fitting parts.

![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/03d639cb5333e62987987dc032741bf2/cb6b8/paint_5.jpg)

## Adaptable interface with mold-like design:

Photogrammetry process (Meshroom):

* Take pictures of an object

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/1dbafd7ac846fc121819f873a7703353/04c10/paint_6.jpg)
* Identify features from the object which appear in several pictures
* From the identified features, derive a guess of the camera positions for each picture
* Infer the 3d location of the object’s features

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/ff3322708b9885bced9194335ce626a7/8bff5/paint_7.jpg)
* Infer a mesh based on the 3d points found

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/f9f0f5e1c6802181b40fbe344795ea40/78241/paint_8.jpg)

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/106d8f66cc1fb5e8d32fe193029a44bb/838b2/paint_9.jpg)

Mesh editing (Meshlab):

* Trimming
* Mesh simplification
* Surface smoothing

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/def3d0b535de584be75ac0a807c2a2ad/bbbfa/paint_10.jpg)

Mesh editing (Blender):

* Import mold-like surfaces

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/f55ec87c8be234c69944c28365f3056b/ba340/paint_11.jpg)
* Add volume

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/485f9b564d2bdadfbc5b9f94b3f3e06f/0526e/paint_12.jpg)
* Smoothen irregularities

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/c819fa6a36ab460486a2433bdacc0812/fcd63/paint_13.jpg)

Use in assembly​ :

* Add support surface
* Adapt for assembly

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/fd36606b3f30190a8189a83f40f84aaa/61495/paint_14.jpg)
* Generate interfacing parts

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/a9b82ccf89f8fc6b6db85401325faf9a/bcd3f/paint_15.jpg)

  * It will be printed, 3d printing guidelines should especially be kept in mind for this design
  * Surface contact constraints locate parts with respect to each other, while screws and nuts fix the assembly (they are never meant to position parts as this would lead to a non-repeatable and mechanically weak/unsafe assembly)
  * Curves are almost always good mechanically speaking
* Assemble everything

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/c55dfd37a91e5f4183ef30bf4bc1b5a8/68632/paint_16.jpg)
* Iterate the design until the assembly is satisfying

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/ef67bea5a99ea127a94e8df36aff46a9/d6b50/paint_17.jpg)

3d printing (Cura):

![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/bad2867cd90fc9278e90df808a1fff5f/d9c0a/paint_18.jpg)

* Avoid overhangs in your design when possible, by using angles smaller than 45 degrees.
* Avoid large flat surfaces and use rounded corners to avoid warping.below.
* Decide what is the minimum level of detail your models require and choose a 3D printing process accordingly.
* Cylindrical holes’ axis should be as perpendicular to the printing surface as possible
* 3d printers do print layer one above the other, so the main mechanical weakness of a 3d printed part is between each printed plane (avoid stressing the part in the plane parallel to the printing surface or adjust the density)
* Remember to calibrate your printer every now and then to avoid accidents

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/28e49b90acd2c34f67a0437ec66ea6d6/6515c/paint_19.jpg)

## Preliminary assembly and testing

For the first test the arm was not moved, only the gripper was activated to test the spraying and an Evian spray can was used as it’s a safe cosmetics product. Electronics exposure seemed negligible in this configuration, but ... better safe than sorry. It worked well.

![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/a6c8a417d69aaf7ebd71a64b21f2418d/c58b0/paint_20.jpg)

## Solution for including cleaning material

* Add flat top surface to previously designed parts

  ![](/assets/paint_21.jpg)
* Add gripping components with various interchangeable frictions plates for different cleaning materials to grip to

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/23d74658761bab990a8555e1740ae3e5/939e2/paint_22.jpg)
* Print and test

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/0e755341ed716824b72d933c0fc4fc13/cffaf/paint_23.jpg)

## Simulation with PnC:

* Adding visualization of the can and spray direction
* Creating simple end-effector trajectories in operational space from within the gazebo plugin with

  * Relative and absolute pose control
  * Duration specification

  ![Robocup](https://nicolas-robotics-portfolio.netlify.app/static/8e62dcad43f5143824c343ba8e7477ed/2b0f9/paint_24.jpg)

<!--EndFragment-->