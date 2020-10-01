---
template: blog-post
title: Autonomously Guided Vehicle
slug: /AGV
date: 2020-09-30 20:35
description: Controlling an AGV
featuredImage: /assets/akeomotion.jpg
---
<!--StartFragment-->

# Line tracking for a moving robot

![AGV](/assets/akeomotion.jpg)

## Why line tracking ?

Here we are going to learn how to use a camera to follow a line drawn on the floor. Let’s say that you want to conceive an autonomous robot but you’re not ready to use mapping technologies to guide it yet. Then line tracking would be a nice and simple way to test your robot. To track lines, you will need a camera and a numeric software such as Matlab or Labview.

## See the line

* Step 1 : Get a picture

  ![AGV](/assets/lt1.png)
* Step 2 : Get access to the RGB data

  ![AGV](/assets/lt2.png)
* Step 3 : Get the coordinates of the pixels

  ![AGV](/assets/lt3.png)

  ![AGV](/assets/lt4.png)
* Step 4 : See the line

  ![AGV](/assets/lt5.png)
* ## Track the line
* Step 1 : Define what you are looking for
* Step 2 : Implement automatic control

Depending on your robot/vehicle, you will need to implement different automatic controls to monitor your motors. For “classical” applications such as wheeled robots you can configure it at low speed by implementing a Full State Feedback if you can model your system and get the following State space equations. The LQ controller fits particularly well here.Measurement equation Where x is a state vector, y is the output vector and u is the control vector. In this case y represents our motors inputs, u includes D and α, and x may correspond to y and other variables you want to estimate in your model. However if you are not familiar with State Feedbacks, you can also implement a simple feedback loop with an adjusted proportional gain, it will already work just fine but you will still have to regulate the weighting between the distance factor D and the orientation factor α depending on your system performances against it. Here is an example of a line tracking establishment I achieved at AKEOPLUS:

[Akeomotion demo](https://www.youtube.com/embed/htx5c2Kiee0)

<!--EndFragment-->