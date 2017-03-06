#**Finding Lane Lines on the Road** 

##Writeup by Saravanan Moorthyrajan

###Below is the write-up on my finding lanes lines project.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "Original Image"
[image2]: ./test_images/Output1_solidWhiteCurve.jpg "Image with raw lines"
[image3]: ./test_images/Output2_solidWhiteCurve.jpg "Image with complete lines"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the below 5 steps :

1.  Convert image to grayscale
1.  Apply Gaussian blue to smoothen the image
1.  Identify edges using Canny Edge detection
1.  Create a mask to mark the region of interest
1.  Identify the co-ordinates for lane lines using edges through Hough's transform
1.  Marking the lines using the above co-ordinates will yield two edge per lane line.  Also broken lane lines will be segmented.
1.  In order to arrive at a single solid line, the below approach has been used :
	1. 


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1] ![alt text][image2]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...