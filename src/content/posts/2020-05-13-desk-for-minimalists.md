---
template: blog-post
title: the Iron Man suit is happening
slug: /exoskeleton
date: 2019-04-20 22:39
description: ironman
featuredImage: /assets/exo.png
---
<!--StartFragment-->

# How real is IronMan?

The first time I worked on an exoskeleton – a robotics suits designed to enhance human capabilities by alleviating their loads or making them stronger – I immediately pictured the Iron Man coming to life. Reality is we’re not there yet, but we’re also clearly not as far as you may think!

## 3 key challenges

* In a full-body exoskeleton, the human operator is fully “contained” inside the robot. While this is also a “handy” safety feature for the operator (e.g. his feet and hands should not touch the ground or walls, the point is for the robot to carry the loads for the human, not the other way around!), the mechanical design of **a resilient robotics suit able to contain a human without constraining his motion** is obviously a really tricky feat to accomplish.
* Now it would be great if the suit could do more than acting as a dead weight right? What we really want is for the suit to actively follow the human over his motion. As for most robotics systems, we will need three components:

  * a **configuration of sensors** to help us guess what the human operator is trying to do
  * a **set of actuators** to put the exoskeleton in motion accordingly
  * a **power source** to allow for all of this to happen.

  This is particularly difficult as humans have numerous and complex mobility features while each actuator can really provide motion in only one direction. It takes compromises between the bulkiness of the suit and the amount of power we need to provide to each joint.
* Finally, the trickiest of them all might very well be the design of a controller’s framework. It can be defined as the structure **optimizing for** **what we want**, *following the human’s motion*, **based on** **what we know**, *mostly the sensors data*, **using what we can control**, *the actuators*. This type of study is found in the field of **control theory** and we will go in slightly more details in the following paragraphs. Notice that I didn’t elaborate much on the sensors in the previous paragraph, this is because as of today there is no best compromise regarding the sensors configuration, what type of sensors to use and how to use them best, it really is about which control strategy the engineers will choose to go for and how much money they can spend on monitoring the human.

In all existing designs of full-body exoskeletons, solutions to the challenges described above are heavily influenced by the corresponding team of engineers’ expertise/background as exoskeletons are yet so uncommon that a research-oriented design approach is still meaningful.

## 3 key control strategies

Control theory is what brings robots to life, its extent is very wide but in essence it allows us to move our robots safely and accurately. We thus design control strategies based on our understanding of it, and below is a list of key elements used nowadays in exoskeleton robotics.

* **Gravity compensation:** as its name suggests, this approach aims at estimating the forces gravity applies on the exoskeleton and to compensate for them, resulting in the robotics suit being able to stand up by itself! It is called a model-based approach since it relies on the knowledge of the robot’s different components position, shape and mass. Model based approach are both fantastically efficient but fragile. What is great about it is its accuracy, provided that the model is right you won’t ever have to worry about gravity anymore. What doesn’t make it ideal is that we don’t always know the model very accurately, either because the bodies position mass and shape are not perfectly well known either because they might change over time unnoticed and the slightest model mistake can make the robot fall easily.
* **Force amplification:** making the human operator stronger. This can initially be defined as a model-free approach if for example we want to amplify the operator’s strength N times, we can simply use force sensors to read how much the operator is pushing and request the robot to provide N-1 times whatever the reading was. The resulting effort from the operator’s side would be 1/N of the robotics suits’ effort and this control strategy would not require any knowledge of a model to work. Experiments have shown however that such a control strategy can perform poorly when the human model is overlooked, thus suggesting to model the human to improve performance.
* **Whole-Body Control (WBC) Framework:** WBC is a well-recognized control strategy which has been implemented in the most successful humanoid robots of these past few years. It consists in adapting the robot’s dynamics in function of the importance of the tasks he is trying to achieve. Let’s take the example of such a robot standing on its feet, and let’s say that we want him to accomplish 3 tasks: balance its center of mass to avoid falling, raise an arm to say hi and go back to its charging station. We could quickly define a hierarchy between these tasks and rank them. First, we don’t want the robot to fall and get damaged so we may want to prioritize balancing above all, then if the robot runs out of battery it won’t be useful anymore and could get damaged too, so this task would be placed second, and finally raising the arm would be 3rd, the last task to prioritize. Now what the controller is going to do is look into how to accomplish the first task as best as it can, it will balance as much as possible. While balancing, it will check for the possibility of accomplishing the second task while still achieving the first, heading toward the charging station while keeping balance. We say that we are looking for a solution to the second task in the null space of the first: if the robot can go the charging station without interfering with its balance, the said null space will allow for the second task to happen withing it, if not it won’t. Similarly, the robot will try to raise an arm while balancing and heading toward the charging station so as to not prevent the given first and second tasks from happening.

## But does it work?

Short answer: **yes**, if you don’t move too fast on a horizontal surface, the SAGIT exoskeleton is a functional proof of concept designed by Apptronik's talented engineers whom I feel lucky to have been working with.

<https://www.youtube.com/watch?v=qvLzugCIdJs&feature=emb_title&ab_channel=Apptronik>

<!--EndFragment-->