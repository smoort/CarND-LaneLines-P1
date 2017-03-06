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
	1. Determine the slope and intercept for a given co-ordinate using the np.polyfit function
	1. Filter outliers by dropping near vertical or horizontal lines.  Constraint that has been used is 0.01 < slope < 10.
	1. Calculate the average slope and intercept seperately for the left and right lanes.  Left lanes can be identified by slope < 0.
	1. Find the top and bottom x co-ordinate using the slope, intercept and y (330, 539 for top and bottom respectively)
	1. Plot the left and right solid lines in red using a thickness of 10.
	1. Use cv2.addWeighted to overlay the identified lanes on top of the original image with transparency


### Image samples : Original image, Image with raw lines and Image with solid lines 

![alt text][image1] ![alt text][image2] ![alt text][image3]


###2. Potential shortcomings with my current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...