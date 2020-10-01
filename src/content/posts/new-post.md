---
template: blog-post
title: Designing a Series Elastic Actuator
slug: /sea
date: 2020-09-30 20:41
description: design of an SEA
featuredImage: /assets/pulley-system.jpg
---
<!--StartFragment-->

# Series Elastic Actuator (SEA) – Team project

## What is at stake ?

As I first wanted to involve myself into robotics, I found an opportunity to study a technology called Series Elastic Actuator which has been developed by the MIT. The principle is very simple, it consists in adding an elastic component between the load and the motor, as shown below.

![Series-Elastic Actuator design](data:image/jpeg;base64,/9j/2wBDABALDA4MChAODQ4SERATGCgaGBYWGDEjJR0oOjM9PDkzODdASFxOQERXRTc4UG1RV19iZ2hnPk1xeXBkeFxlZ2P/2wBDARESEhgVGC8aGi9jQjhCY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2P/wgARCAAGABQDASIAAhEBAxEB/8QAFgABAQEAAAAAAAAAAAAAAAAAAAEF/8QAFAEBAAAAAAAAAAAAAAAAAAAAAP/aAAwDAQACEAMQAAAB3aFB/8QAFBABAAAAAAAAAAAAAAAAAAAAEP/aAAgBAQABBQJ//8QAFBEBAAAAAAAAAAAAAAAAAAAAEP/aAAgBAwEBPwE//8QAFBEBAAAAAAAAAAAAAAAAAAAAEP/aAAgBAgEBPwE//8QAFBABAAAAAAAAAAAAAAAAAAAAEP/aAAgBAQAGPwJ//8QAFhAAAwAAAAAAAAAAAAAAAAAAABEh/9oACAEBAAE/IaJqlP/aAAwDAQACAAMAAAAQAA//xAAUEQEAAAAAAAAAAAAAAAAAAAAQ/9oACAEDAQE/ED//xAAUEQEAAAAAAAAAAAAAAAAAAAAQ/9oACAECAQE/ED//xAAZEAADAQEBAAAAAAAAAAAAAAAAARFRIZH/2gAIAQEAAT8Qb0VTiMml4f/Z)

![Series-Elastic Actuator design](https://nicolas-robotics-portfolio.netlify.app/static/392be392d2cbe7e16de49d4d69a706aa/45521/sea-principle.jpg)

The worldwide industry never fails to show us how advanced robotics has become. While our eyes can barely follow up with a robot accomplishing its manufacturing operations, adding elastic components would mostly diminish the all system efficiency by decreasing its precision and repeatability.

## A new compromise to make

Thus, one may wonder why would we put so much interest in elasticity, specially when it is linked to actuators which we like to keep accurate ? This actually makes sense when one considers the problems of tomorrow’s world. As part of a classical industrial application, engineers avoid security issues by defining areas forbidden to humans. Plus, they are almost not concerned by accidents since the environment is well defined and regulated, which means that those engineers are able to predict quite precisely how each robot is going to deteriorate. However, robots are no longer seen as simple tools set away from humans and confined to sheds. Collaborative robots and advanced AI have emerged, robots start interacting with their environment and pave the way to more usability everyday. Here we are going to study the damages of bumps on a moving rigid system. Indeed, rigidity implies low shock tolerance which is very concerning because actuators are not designed to endure much external disturbances.

## Design of a SEA

Thereby, my project was to design a one meter long robotic arm, later assembled on a mobile platform which drives along a farm field in order to interact with agricultural plantation. In this case, the lack of knowledge about the farm surface makes it impossible to prevent the driving rigid system from being damaged by bumps. This is why it is become interesting to introduce an elastic component behaving as a low-pass filter toward those perturbations.

![Series-Elastic Actuator design](https://nicolas-robotics-portfolio.netlify.app/static/d5aea7c4f88531e4838c1f425b419495/a7fbf/farm.jpg)

There are two main technologies linked with SEAs, rotary and linear. Linear SEAs can either place the elastic component between the load and the gearbox, in which case it is called FSEA (Force Sensing SEA), or place it between the motor and the chassis, in which case it is called RFSEA (Reaction Force Sensing SEA). To ensure that the shocks are entirely supported by the compliant element (a spring here), we chose to study the FSEA technology which is explained below. Design FSEA Design FSEA As the motor provides a torque to the first pulley, the worm gear assembled with the second pulley will allow the desired piece of the system to move linearly with the attached load. Rotary SEAs can either use a torsion or a compression spring, in this case we chose a torsion spring because of its disposability to mesure a given shock more precisely. The rotary solution is the easiest to prototype because of its simple assembly. However, it requires a more powerful motor because of the less effective reducer system.

![Series-Elastic Actuator design](https://nicolas-robotics-portfolio.netlify.app/static/c30fc079e64ca720fb945c60e80a3726/5be08/Pulley-System.jpg)

Here is a visualization of the final render of our work as a team in this project : CAD of the robotic arm provided with an SEA A demonstration of SEA’s efficiency lies in the Valkyrie which is a 44 degree of freedom robot based on series elastic actuators. Valkyrie

![Series-Elastic Actuator design](https://nicolas-robotics-portfolio.netlify.app/static/9e3e7939adad3d23853aa68857daa4e6/92819/sea_system.jpg)



<!--EndFragment-->