#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

### Submitted by Raymond Leung, leung.raymond@gmail.com
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road - COMPLETED, REVIEWED AND MODIFIED BASED ON 1st REVIEW
* Reflect on your work in a written report -- COMPLETED, REVIEW AND MODIFIED BASED ON 1st REVIEW
* DID NOT COMPLETE THE OPTIONAL CHALLENGE PROJECT


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 
1) Gray Scale the original image, covert the image to gray scale and get it ready for Canny process.
2) Gaussian Blue the gray scale image to reduce the noise of the trees and the signs on both side of the road.
3) Define the area of interest, I use (450, 325) and (490, 325) for the area.  I intend to keep the y axial lower.
4) Use the Hough Transform to draw the lines.   Increase the threshold to 40 votes to reduce the multiple line.   Reduce the min_line_len to 20 pixel and Increase the max_line_gap to 60.  The gap between the line segment is big.  Need to increase the gap limit.
Note: Based on the 1st review feedback, change the threshold to 30, min length to 100, and max gap to 160 for better result.
5) Merge the lines image and the orginal image together.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by extending the y1 or y2 to the bottom of the image.   It is about 538:

`(y2 - y1) / (x2 - x1) = (y3 - y1) / (x3 - x1)`

if y3 is at the bottome of the image, it will be 538, so we calculate what x3 is and plug in back to the fomula.
	
However, there are two cases, the left side and right side, we need to use a conditional statement to distinguish them.

Here are the output images to show how the pipeline works, here is how to include an image: 

./test_images_output/solidYellowLeft.jpg "Solid Yellow Left"

./test_images_output/solidYellowCurve.jpg "Solid Yellow Curve"

./test_images_output/solidYellowCurve2.jpg "Solid Yellow Curve2"

./test_images_output/solidWhiteRight.jpg "Solid White Right"

./test_images_output/solidWhiteCurve.jpg "Solid White Curve"

./test_images_output/whiteCarLaneSwitch.jpg "White Car Lane Switch"

###2. Identify potential shortcomings with your current pipeline


One potential shortcoming: 

1) The optional challenge problem has not been resolve.  Too many horizonal line.
2) Hard code the side of the bottom of the image for Hough Transform.  Can be more dynamic.
3) The draw line logic has a conditional statement, it should be with the expression.

###3. Suggest possible improvements to your pipeline

Simpilfy the draw_line()



Another potential improvement 

If I have more time, I will fix teh optional challenge problem
