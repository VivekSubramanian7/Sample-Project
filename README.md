# Sample-Project# SFND 2D Feature Tracking

<img src="images/keypoints.png" width="820" height="248" />

The idea of the camera course is to build a collision detection system - that's the overall goal for the Final Project. As a preparation for this, you will now build the feature tracking part and test various detector / descriptor combinations to see which ones perform best. This mid-term project consists of four parts:

* First, you will focus on loading images, setting up data structures and putting everything into a ring buffer to optimize memory load. 
* Then, you will integrate several keypoint detectors such as HARRIS, FAST, BRISK and SIFT and compare them with regard to number of keypoints and speed. 
* In the next part, you will then focus on descriptor extraction and matching using brute force and also the FLANN approach we discussed in the previous lesson. 
* In the last part, once the code framework is complete, you will test the various algorithms in different combinations and compare them with regard to some performance measures. 

See the classroom instruction and code comments for more details on each of these parts. Once you are finished with this project, the keypoint matching part will be set up and you can proceed to the next lesson, where the focus is on integrating Lidar points and on object detection using deep-learning. 

## Dependencies for Running Locally
* cmake >= 2.8
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* OpenCV >= 4.1
  * This must be compiled from source using the `-D OPENCV_ENABLE_NONFREE=ON` cmake flag for testing the SIFT and SURF detectors.
  * The OpenCV 4.1.0 source code can be found [here](https://github.com/opencv/opencv/tree/4.1.0)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./2D_feature_tracking`.



\\\\\Answers
MP.1 the ring buffere is impetetd using deque, I choose this as I am familar with deque in my work and also that time complexicity for inserting /deleting is O(1). The size is checked and as the buffer size limit is reached the first elememt is removed, thus the rig buffer is implemented as FIFO.
The most common usage could be using std::vector but as far as optimization goes the time complexity for inserting/deleting is O(n). Hence choice of deque, but the a std::queue could be used but i prefer deque as we needed iteration and helps cleaner pop operation

MP.2 Generally i prefer using switch but as our "switch expression" is a string, we might first process it to get associated enum to be used as switch expression. Honestly, I did not invest a lot of time. 
I used if & else if and string-compare sub functionality to get the correct option parsed.We acheive a similar functionality as switch using "if.. else if" but code readabilty is compramized.

MP.3 iterated through the points and removed once outside specified ROI, this can be optimized though which but i did not invest more time on that.WE are using a std::vector as mentioned in the answer MP.1 the time complexicity of deletion is O(n). But I did nbot investigate a better solution, deque could be option. 

MP 4 if, else if is used to implement different user option, detailed answer in MP.2

MP5 if, else if is used to implement different user option, detailed answer in MP.2
After googling a bit, I figured out "MAT_FLANN" option needs the image in CV_32F format. If the input is not in the desired format we need to convert it before processing it. used "if else " to acheive this.

MP6 iterated the through the points and selected point with ration within threshold. The ratio between best and second best matches needs to within the threshold to be finalized for further processing and others are ignored.

MP7 in spreadsheet
MP8 in spreadsheet
MP9 in spreadsheet

According to my observation for the use case in hand, FAST is the best detector followed by ORB and SHITOMASI, but in case of descriptors BRIEF, BRISK , ORB have very similar performace.
