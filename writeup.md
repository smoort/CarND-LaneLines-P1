# **Finding Lane Lines on the Road** 

## Writeup on Finding Lanes Lines project by *Saravanan Moorthyrajan*


**First Revision (18 Mar 2017) - Changes to handle Challenge video**
- Enhanced filters to handle shadows and tyre marks on roads
- Removed hard coding of mask co-ordinates
- Linked previous clip data to current clip data to provide reference

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/Challenge1.png "First Shadow"
[image2]: ./test_images/Challenge2.png "Shadow to White road"
[image3]: ./test_images/Challenge3.png "White road"
[image4]: ./test_images/Challenge4.png "White road to Shadow"
[image5]: ./test_images/Challenge5.png "Second Shadow"

---

### Reflection

### 1. Description of my pipeline

The pipeline consists of the below steps :

1.  Convert image to grayscale
1.  Apply Gaussian blur to smoothen the image
1.  Identify edges using Canny Edge detection
1.  Create a mask to mark the region of interest
1.  Identify the co-ordinates for lane lines using edges through Hough transform
1.  Lines with slope < 0 are considered part of Left lane and slope > 0 are considered part of right lane.
1.  For each line identified through Hough transform, apply the following filters :
    1. Lines with slope^2 outside the range of 0.1 and 100 are filtered out as horizontal lines
    1. Lines with slope < 0 (left lane) but lying to the right of center are filtered
    1. Lines with slope > 0 (right lane) but lying to the left of center are filtered
    1. Lines with slope & intercept beyond the allowed variance from previous clip slope & intercept are filtered.
1.  Calculate the mean slope and intercept seperately for the left and right lanes.
1.  The highest y value of valid lines across clips is considered the bottom y co-ordinate of the lanes
1.  The top y cordinate is calculated using the image height and a predetermined factor.
1.  Find the top and bottom x co-ordinates for left and right lanes using their respective average slope, average intercept and y
1.  Plot the left and right solid lines in red using a thickness of 10.
1.  Overlay the identified lanes on top of the original image with transparency

#### Image samples : Below are some images from the video with good and bad lines highlighted
1.  *Light yellow lines are detected as horizontal lines and hence filtered out*
1.  *Blue lines are detected as shadows, tyre marks and other noise which are filtered out*
1.  *Green lines are considered actual lane lines, they are averaged out and extrapolated to draw the lane lines*

![alt text][image1] ![alt text][image2] ![alt text][image3] ![alt text][image4] ![alt text][image5]


### 2. Below are the short comings with the current implementation : 

1. Have only used straight lines which do not track curves in the road.
1. Yellow marking on white roads are very difficult to identify.  Reducing canny edge low_threshold adds a lot of noise to the image
1. Tyre marks on white roads is adding to noise


### 3. Possible improvements to the solution could be :

1. Ability able to plot curved lines to handle curved lane
1. Ability to identify yellow lanes on white road better
1. A more precise way to filter out tyre markings and shadows


---

**Has been a fun project.  Very interesting.** 				  ~   Saravanan Moorthyrajan

---