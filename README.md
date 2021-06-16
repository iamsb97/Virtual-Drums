<center> <h1>Virtual Drums</h1> </center>

## Objective

Playing drums using nothing but hands virtually in an application which is running through the webcam. 

<div align="center">
    <img src="https://images-na.ssl-images-amazon.com/images/I/71vglY8AZOL.__AC_SX300_SY300_QL70_ML2_.jpg">
</div>

## Libraries

1. OpenCv - version 4.5.2
2. Numpy - version 1.20.1
3. Mediapipe - vesion 0.8.4.2
4. Imutils - version 0.5.4
5. Pygame - version 2.0.1
6. Pymunk - version 6.0.0

## How To Run The Code

**Note: This code runs on python version 3.7.10**

1. Clone the repository into your local machine.
2. Install the appropriate versions of all the libraries listed above.
3. Run the python notebook "Virtual Drums.ipynb".

**Note: For better experience, use index finger to play the drums**

## Overview

OpenCV and imutils library has been used in the code to read in the images(drums), resizing and rotating the images as necessary, for accessing video feed through webcam and placing the drums in the frame.  

Mediapipe multi_hand_landmarks is used for hand-tracking i.e keeping track of x,y,z coordinates of [21 landmarks](https://google.github.io/mediapipe/solutions/hands.html#hand-landmark-model) on each hand at every instant of time. Mediapipe multi_handedness is used to detect left and right hand. This is done to differentiate between the two hands and assign each circular object to one hand. 

For detecting collisions between drums and hands, physics engine pymunk is used. To simulate hands, 2 circular pymunk objects are created and 4 static segments are created to represent the drums. The circular objects move along with the index finger of the hands. The segments are placed on top of each drum. Hence, whenever the hands collide with the drums, the circular objects collide with the segments. Pymunk collision handler along with pygame mixer is used to play respective drum sounds whenever it detects a collision.