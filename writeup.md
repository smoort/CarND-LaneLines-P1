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
[image2]: ./test_images/Output1_solidWhiteCurve.jpg "Image with rough lines"
[image3]: ./test_images/Output2_solidWhiteCurve.jpg "Image with complete lines"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of the below steps :

1.  Convert image to grayscale
1.  Apply Gaussian blur to smoothen the image
1.  Identify edges using Canny Edge detection
1.  Create a mask to mark the region of interest
1.  Identify the co-ordinates for lane lines using edges through Hough transform
1.  Marking the lines using the above co-ordinates will yield two rough lines per lane line with no solid filling.  Also if the lane lines are broken, the rough lines will be segmented as well.
1.  In order to arrive at a single solid line, the below approach has been used :
	1. Determine the slope and intercept for a given co-ordinate using the np.polyfit function
	1. Filter outliers by dropping near vertical or horizontal lines.  Constraint that has been used is 0.01 < slope < 10 (both negative and positive values).
	1. Calculate the average slope and intercept seperately for the left and right lanes.  Left lanes can be identified by slope < 0.
	1. Find the top and bottom x co-ordinates for left and right lanes using their respective average slope, average intercept and y (330, 539 for top and bottom respectively)
	1. Plot the left and right solid lines in red using a thickness of 10.
	1. Use cv2.addWeighted to overlay the identified lanes on top of the original image with transparency


### Image samples : *Original image*,   *Image with rough lines*   and   *Image with solid lines* 

![alt text][image1] ![alt text][image2] ![alt text][image3]



###2. Potential shortcomings with my current pipeline


Below are the short comings with the current implementation : 

1. Have used hard-coded values for mask boundaries.  Though it works well for the provided videos, not sure if it will be suitable for all situations.
1. Have used hard-coded values for y co-ordinates (330 and 539) for extrapolation to determine the x values using the average slope and intecept. Again, it works well for the provided videos, not sure if it will be suitable for all situations.
1. Real life situation can have strong shadows cast by railings or a passing by truck, which the algorithm can mistake for lane edges.
1. The implementation works well for straight lane lanes.  Working on the challenge video with curved lanes.



###3. Possible improvements to my pipeline

Possible improvements to the solution could be :

1. Auto calculation of mask boundaries, leading to auto calculation of y co-ordinates that can be used for extrapolation
1. Being able to plot curved lines to handle curved lanes
1. Have used a constraint on slope (>0.01 & < 10) to filter out noise. Need a more scientific approach to remove outliers.


---

**Has been a fun project.  Very interesting.** 				  ~   Saravanan Moorthyrajan

---