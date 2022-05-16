# Visual-Odometry-using-RGB-D-Images
In this project, we aim to accurately estimate the pose of a moving camera at every time step and subsequently its trajectory, from RGB-D images only.

## Overview
In this project, we implement a visual odometry and mapping system using RGB-D images inspired by the paper on *"Fast visual odometry and mapping from RGB-D data"*. We estimate the 6-DoF trajectory of a moving camera by aligning sparse features obtained from RGB-D images against a persistent model set consisting previous features. A Kalman Filter is used to dynamically update the model set by incorporating new features obtained from each RGB-D frame. A Gaussian mixture model is implemented to handle the uncertainty in the sparse RGB-D image features. The results of this project show that our implementation estimates the pose of the camera fairly well and is also able to close small-scale loops in indoor environments.

## Dataset
The dataset used is the [RGB-D SLAM Dataset](https://vision.in.tum.de/data/datasets/rgbd-dataset/download#freiburg1_room) from TU Munich’s Computer Vision Group. The dataset contains color and depth images at multiple time steps captured by a Microsoft Kinect sensor along with the ground-truth trajectory of the sensor. There exists multiple series of datasets covering different environments such as office spaces and day-to-day objects - we used the *"freiburg1_room"* sequence dataset for this project. 

Along with the RGB and depth images, the corresponding rgb, depth, and ground-truth .txt files contain the timestamps for each image frame. Due to the lack of an inherent 1:1 correspondence between the data, the associated RGB, depth and, ground truth data is found. 

Finally, we are also provided with the camera intrinsic parameters for calibration - 3D coordinates in the camera coordinate frame.

## Procedure
  * Run the Visual_Odometry.ipynb notebook with the appropriate path to the downloaded TUM RGB-D dataset.
  * In \__main__\, select the feature extraction algorithm 
  
    ```
    # select feature detector
    feature_detector = "GFTT"       #"GFTT" or "SIFT" or "ORB"
    ```
  * Create the appropriate folders to save the resulting trajectory and plots. 
