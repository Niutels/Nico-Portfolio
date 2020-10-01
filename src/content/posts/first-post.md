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

![AGV](https://nicolas-robotics-portfolio.netlify.app/static/40734fc0c94fd13ac4fd18c02d4e40f2/e91af/akeomotion.jpg)

## Why line tracking ?

Here we are going to learn how to use a camera to follow a line drawn on the floor. Let’s say that you want to conceive an autonomous robot but you’re not ready to use mapping technologies to guide it yet. Then line tracking would be a nice and simple way to test your robot. To track lines, you will need a camera and a numeric software such as Matlab or Labview.

## See the line

* Step 1 : Get a picture

  ![AGV](https://nicolas-robotics-portfolio.netlify.app/static/30f7f919ffb269598e6897621f56a2c7/f1f45/LT1.png)
* Step 2 : Get access to the RGB data

  ![AGV](https://nicolas-robotics-portfolio.netlify.app/static/e79900f0ff016feb069d41ac81abf13e/c5862/LT2.png)
* Step 3 : Get the coordinates of the pixels

  ![AGV](https://nicolas-robotics-portfolio.netlify.app/static/9f221ca98f91741256bf879115f919d8/f1d7f/LT3.png)

  ![AGV](https://nicolas-robotics-portfolio.netlify.app/static/8bdb0db124330b13cbcebd22e3a28f7a/4d5b7/LT4.png)
* Step 4 : See the line

  ![AGV](https://nicolas-robotics-portfolio.netlify.app/static/694cf201af3015dcb3701db020649fc4/97afc/LT5.png)
* ## Track the line
* Step 1 : Define what you are looking for
* Step 2 : Implement automatic control

Depending on your robot/vehicle, you will need to implement different automatic controls to monitor your motors. For “classical” applications such as wheeled robots you can configure it at low speed by implementing a Full State Feedback if you can model your system and get the following State space equations. The LQ controller fits particularly well here.Measurement equation Where x is a state vector, y is the output vector and u is the control vector. In this case y represents our motors inputs, u includes D and α, and x may correspond to y and other variables you want to estimate in your model. However if you are not familiar with State Feedbacks, you can also implement a simple feedback loop with an adjusted proportional gain, it will already work just fine but you will still have to regulate the weighting between the distance factor D and the orientation factor α depending on your system performances against it. Here is an example of a line tracking establishment I achieved at AKEOPLUS:

[Akeomotion demo](https://www.youtube.com/embed/htx5c2Kiee0)



<!--EndFragment-->