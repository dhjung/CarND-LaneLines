# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

[image1]: ./examples/laneLines_thirdPass.jpg "Combined Image"

![alt text][image1]

Reflection
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps similar to lecture notes.
I also used the same tuning parameters for functions inside the pipeline and got pretty good results until improving the draw_lines function. 
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding two features beside drawing lines on the image.
First, I divide Hough lines into the left or right lane by calculating the slope of each line. Secondly, I used numpy's polyfit function to get average slope and intercept for each lane. By using returns of polyfit function and image's size, I could extrapolate whole lanes.    


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when image or video's size has been changed.
I assumed that current pipeline uses fixed values for image's vertical length and region of interest as well.
As result, my current pipeline wouldn't work well for different sized images.

Another shortcoming could be when the road conditions has been changed.
My current pipeline used one single line for each lane so that it won't work properly when car is moving on curvy road.
In addition, If there are huge long shadows on the road like "challenge" video, hough lines in the middle of pipeline would be wrong.   


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use previous line's information to smooth moving lanes.
Current pipeline doesn't have any method to fill the gap between video frames.

