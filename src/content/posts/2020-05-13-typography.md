---
template: blog-post
title: Smart Pen
slug: /smartpen
date: 2016-03-20 21:15
description: A pen which can guess what you're handwriting in 3d
featuredImage: /assets/smart_pen.png
---
<!--StartFragment-->

# Smart Pen – Numerize your 3D handwriting

## Why is it smart ?

The pen I am going to show you doesn’t just copy what you write, it is able to recognize, to “understand” digits and letters written in the air and to write it in a word file. You will need a numeric software such as Matlab, an arduino board, an IMU and some pen-shaped material.

## Your computer needs to learn

We first need to teach to the computer the symbols we want it to recognize, put it simply:

* The central unit is going to collect two types of data : linear acceleration and angular velocity.
* The arduino reads it, regulates it to get a fixed time base before sending the results to your computer.
* Matlab allows you to process it, to get a clean signal and associate it with a symbol.

![schema](/assets/pen_schema.png)

## Why linear acceleration and angular velocity ?

The goal is to make the pen as usable as possible : most of the time, precise position requires external sensors which interfere with a free and convenient use of the pen. Moreover, the linear accelerations is sufficient to differentiate symbols. The angular velocity provides additional informations about the direction of gravity which will be useful during the data process.

## Why a fixed time base ?

The central unit sends data irregularly, which means that the data coming from the arduino is temporally disturbed and requests computing time to adjust it. A fixed time base allows us to put this issue aside.

## What is a clean signal ?

The acceleration signal used to teach the computer how to recognize a symbol needs to be particularly “clean” in order to be able to recognize as many other symbols as possible. The more the acceleration signal matches the one you conveyed, the more the recognition efficiency will increase. In my example I calibrated the sensor, then I applied a low pass filter to get rid of most disturbances, I removed the gravity component by using a Kalman filter to find its precise direction (by combining the data from the accelerometer with the data from the gyrometer) and finally I set up a threshold system in order to avoid reading noises.

## Write in 3D !

Now, to recognize what you are going to write we will use a Dynamic Time Warping algorithm which is simply going to compare the signal resulting from your writing with the one you associated with a symbol previously. If those two are similar enough, it will finally be written in a word file.A more extensive report and useful figures can be found in the link below:

[Smart pen report](https://nicolas-robotics-portfolio-temp.netlify.app/static/7550be49d6549bbc3f50a37e05527250/PJE.pdf)

[](https://nicolas-robotics-portfolio-temp.netlify.app/static/7550be49d6549bbc3f50a37e05527250/PJE.pdf)<!--EndFragment-->