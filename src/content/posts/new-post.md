---
template: blog-post
title: Designing a Series Elastic Actuator
slug: /sea
date: 2015-05-24 20:41
description: design of an SEA
featuredImage: /assets/pulley-system.jpg
---
<!--StartFragment-->

# Series Elastic Actuator (SEA) – Team project

## What is at stake ?

As I first wanted to involve myself into robotics, I found an opportunity to study a technology called Series Elastic Actuator which has been developed by the MIT. The principle is very simple, it consists in adding an elastic component between the load and the motor, as shown below.

![Series-Elastic Actuator design](/assets/sea-principle.jpg)

The worldwide industry never fails to show us how advanced robotics has become. While our eyes can barely follow up with a robot accomplishing its manufacturing operations, adding elastic components would mostly diminish the all system efficiency by decreasing its precision and repeatability.

## A new compromise to make

Thus, one may wonder why would we put so much interest in elasticity, specially when it is linked to actuators which we like to keep accurate ? This actually makes sense when one considers the problems of tomorrow’s world. As part of a classical industrial application, engineers avoid security issues by defining areas forbidden to humans. Plus, they are almost not concerned by accidents since the environment is well defined and regulated, which means that those engineers are able to predict quite precisely how each robot is going to deteriorate. However, robots are no longer seen as simple tools set away from humans and confined to sheds. Collaborative robots and advanced AI have emerged, robots start interacting with their environment and pave the way to more usability everyday. Here we are going to study the damages of bumps on a moving rigid system. Indeed, rigidity implies low shock tolerance which is very concerning because actuators are not designed to endure much external disturbances.

## Design of a SEA

Thereby, my project was to design a one meter long robotic arm, later assembled on a mobile platform which drives along a farm field in order to interact with agricultural plantation. In this case, the lack of knowledge about the farm surface makes it impossible to prevent the driving rigid system from being damaged by bumps. This is why it is become interesting to introduce an elastic component behaving as a low-pass filter toward those perturbations.

![Series-Elastic Actuator design](/assets/farm.jpg)

There are two main technologies linked with SEAs, rotary and linear. Linear SEAs can either place the elastic component between the load and the gearbox, in which case it is called FSEA (Force Sensing SEA), or place it between the motor and the chassis, in which case it is called RFSEA (Reaction Force Sensing SEA). To ensure that the shocks are entirely supported by the compliant element (a spring here), we chose to study the FSEA technology which is explained below. Design FSEA Design FSEA As the motor provides a torque to the first pulley, the worm gear assembled with the second pulley will allow the desired piece of the system to move linearly with the attached load. Rotary SEAs can either use a torsion or a compression spring, in this case we chose a torsion spring because of its disposability to mesure a given shock more precisely. The rotary solution is the easiest to prototype because of its simple assembly. However, it requires a more powerful motor because of the less effective reducer system.

![Series-Elastic Actuator design](/assets/pulley-system.jpg)

Here is a visualization of the final render of our work as a team in this project : CAD of the robotic arm provided with an SEA A demonstration of SEA’s efficiency lies in the Valkyrie which is a 44 degree of freedom robot based on series elastic actuators. 

![Series-Elastic Actuator design](/assets/sea_system.jpg)

<!--EndFragment-->