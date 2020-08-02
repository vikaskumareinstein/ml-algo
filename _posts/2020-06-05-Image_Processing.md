---
title: Object Tracking
---
We are going to learn a simple object tracking technique using OpenCV python package.
We know for better representation of color we use HSV(Hue-Saturation-Value) color format.
Hue range is [0,179];Saturation range is [0,255] ; Value range is [0,255].
You can find the list of whole color conversion flags using the below code:
`import cv2`
`flags=[i for i in dir(cv2) if i.startswith('COLOR_')]`
`print(flags)`

As,OpenCV uses BGR format(not RGB which is the common format).So for conversion from BGR->HSV use `cv2.COLOR_BGR2HSV`.For BGR->GRAY use `cv2.COLOR_BGR2GRAY`.

In this post, a particular color object will be extracted and tracked in a video.We will use a blue color object in particular.

###STEPS:
1. Take each frame of the video.
2. Convert to hsv color-space.
3. Extract the range of blue color by thresholding.

You might not be familiar with the concept of thresholding.It is a segmentation technique in which we take a particular image and convert it into binary image of black and white(simple binary thresholding).

Look at the below code and try implementing yourself.Code is commented for your convenience.

`import cv2`
`import numpy as np`
`cap = cv2.VideoCapture(0)	#Capture from the camera`
`cap = cv2.VideoCapture('<path to your video>')`
`while(True):		#Infinite loop until break`
`	ret,frame=cap.read()	#reading each frame and saving to frame variable`
`	hsv = cv2.cvtColor(frame,cv2.COLOR_BGR2HSV)	#BGR to HSV color space.`
`	lower_blue=np.array([110,50,50])`
`	high_blue = np.array([130,255,255])`
`	mask = cv2.inRange(hsv,lower_blue,high_blue)	#specified hsv<image>,lower and upper color range as array for thresholding`

``
