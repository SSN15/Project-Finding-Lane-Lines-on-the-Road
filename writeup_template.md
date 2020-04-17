# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I added the denoising filter to gray scale images.
I applied canny edge detection algorithm using OpenCV and detected the edges. I created a four sided polygon mask in the image after which I applied hough transform to the images to convert the images into parameter space.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by finding the slop.
In our images, the left lane markings all have a negative slope, meaning the lines travel upwards towards the horizon as we move from left to right along the lines. On the other hand, all of our right lane markings have a positive slope, traveling downwards towards the bottom of the image as we move along them from left to right. This will be the distinction we use to group the left and right lines. Furthermore, the lane markings appear extreme in slope, so we will not consider any line with a slope absolute value less than 0.5. This means that we’ll reject any line which doesn’t move quickly towards the horizon or the bottom of the image, leaving only lines which are nearer to vertical than horizontal.

The second challenge in our single line creation problem is to average the lines in each group into a single line that fits pretty closely in orientation and location in the image.
I used polyfit and poly1d operations to gnerate solid lines on both sides.



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when executing the pipeline for the challenge.mp4 video(Optional Challene).
The piepline fail to construct lines on both sides for this video



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to make the pipeline more robust for all the lane finding videos.
