# Matlab : Tracking and Motion Estimation

```MATLAB
Optical flow, activity recognition, motion estimation, and tracking
```

```HTTP
https://ww2.mathworks.cn/help/vision/tracking-and-motion-estimation.html?s_tid=CRUX_lftnav
```

## Introduce 

```matlab
Motion estimation and tracking are key activities in many computer vision applications, including activity recognition, traffic monitoring, automotive safety, and surveillance.

Computer Vision Toolbox™ provides video tracking algorithms, such as continuously adaptive mean shift (CAMShift) and Kanade-Lucas-Tomasi (KLT). You can use these algorithms for tracking a single object or as building blocks in a more complex tracking system. The toolbox also provides a framework for multiple object tracking that includes Kalman filtering and the Hungarian algorithm for assigning object detections to tracks.

Motion estimation is the process of determining the movement of blocks between adjacent video frames. This toolbox includes motion estimation algorithms, such as optical flow, block matching, and template matching. These algorithms create motion vectors, which can relate to the whole image, blocks, arbitrary patches, or individual pixels. For block and template matching, the evaluation metrics for finding the best match include mean square error (MSE), mean absolute deviation (MAD), maximum absolute difference (MaxAD), sum of absolute difference (SAD), and sum of squared difference (SSD).
```

## Functions

#### 	>Load, Save, and Display Video

```matlab
vision.BinaryFileReader			% Read video data from binary files
vision.BinaryFileWriter			% Write binary video data to files
vision.DeployableVideoPlayer	% Display video
vision.VideoPlayer				% Play video or display image
vision.VideoFileReader			% Read video frames and audio samples from video file
vision.VideoFileWriter			% Write video frames and audio samples to video file
```

#### >Object Tracking

```MATLAB
assignDetectionsToTracks		% Assign detections to tracks for multiobject tracking
bbox2points						% Convert rectangle to corner points list
configureKalmanFilter			% Create Kalman filter for object tracking
vision.KalmanFilter				% Correction of measurement, state, and state estimation error covariance
vision.HistogramBasedTracker	% Histogram-based object tracking
vision.PointTracker				% Track points in video using Kanade-Lucas-Tomasi (KLT) algorithm
vision.BlockMatcher				% Estimate motion between images or video frames
vision.TemplateMatcher			% Locate template in image
```

#### > Motion Estimation

```matlab
opticalFlow				% Object for storing optical flow matrices
opticalFlowFarneback	% Object for estimating optical flow using Farneback method
opticalFlowHS			% Object for estimating optical flow using Horn-Schunck method
opticalFlowLK			% Object for estimating optical flow using Lucas-Kanade method
opticalFlowLKDoG		% Object for estimating optical flow using Lucas-Kanade derivative of Gaussian method
vision.BlockMatcher		% Estimate motion between images or video frames
vision.TemplateMatcher	% Locate template in image
```

####  >Visualization and Display

```matlab
insertMarker			% Insert markers in image or video
insertShape				% Insert shapes in image or video
insertObjectAnnotation	% Annotate truecolor or grayscale image or video stream
insertText				% Insert text in image or video
imshow	 				% Display image
imshowpair				% Compare differences between images
```

